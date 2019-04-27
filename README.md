# Nova Field Count
A Laravel Nova field for relationship count. Displays only on index view.

## Installation

```bash
> composer require saumini/count
```

## Usage

Define the relationship on model.

```php
class Post extends Model
{
    public function comments()
    {
        return $this->hasMany('App\Comment');
    }
}

```

Use `Count` field on relationship.

```php
use Saumini\Count\RelationshipCount;

class Survey extends Resource
{
    ...
    public function fields(Request $request)
    {
        return [
            RelationshipCount::make('Comments Count', 'comments'),
        ];
    }
}
```

#### For sortable field

```php
use Saumini\Count\RelationshipCount;

class Survey extends Resource
{
    ...
    public function fields(Request $request)
    {
        return [
            RelationshipCount::make('Comments Count', 'comments')->sortable(),
        ];
    }
    
    // Overwrite the indexQuery to include relationship count
    public static function indexQuery(NovaRequest $request, $query)
    {
        // Give relationship name as alias else Laravel will name it as comments_count
        return $query->withCount('comments as comments');
    }
}
```

## Screenshot

![Screenshot 1](https://raw.githubusercontent.com/nsaumini/nova-field-count/master/.docs/Screenshot1.png)




