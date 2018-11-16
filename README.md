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
use Saumini\Count\Count;

class Survey extends Resource
{
    ...
    public function fields(Request $request)
    {
        return [
            Count::make('Comments Count', 'comments'),
        ];
    }
}
```

## Screenshot

![Screenshot 1](https://raw.githubusercontent.com/nsaumini/nova-field-count/master/.docs/Screenshot1.png)

