### Polymorph

#### One To Many


Migration untuk tabel Comment
```php
	//...
	$table->nullableMorphs('commentable');
	//...
```

Comment.php

```php

	public function commentable(){
		return $this->morphTo();
	}

```

Post.php

```php

	public function comments(){
		return $this->morphMany(Comment::class, 'commentable');
	}

```

#### One to One

Post.php

```php

	public function best_comment(){
		return $this->morphOne(Comment::class, 'commentable')->best_comment();
	}

```


[referensi](https://laravel.com/docs/7.x/eloquent-relationships#one-to-many-polymorphic-relations)