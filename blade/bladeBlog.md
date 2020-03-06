## Extend Layout
`@yield('title',Default value)`
> display contents of a given section

> **Default value :** will be rendered if the section being yielded is undefined

`@extends`

> to specify which layout the child view should "inherit"


`@section('sidebar')
     This is the master sidebar
[@show|@endsection|@stop]`

> **@show :** is used to display the contents of the section

> **@ednsection |@stop**  indicate the end of a section

> We can set content of section on one line **Ex :** `@section('title','page title')`

`@parent`

> displays the content which defined in the master layout


----------------------------------------------------------------------------

## Display Data :


`{{ $variable }}`

> To echo the value of this variable

> You may also echo the results of any PHP function **EX :** `{{ time() }}`

`{!! $variable !!}`

> Displaying Unescaped Data

`@{{ name }}`

> To prevent the conflict between blade and the other JS frameworks which use curly braces to display data

### The `@verbatim` Directive
> you may wrap the HTML in the `@verbatim` directive so that you do not have to prefix each Blade {{  }} with an `@` symbol to prevent conflic .

**EX:**
```
@verbatim
    <div class="container">
        Hello, {{ name }}.
    </div>
@endverbatim
```
### Rendering JSON
>`<?php echo json_encode($array); ?>`

> The same in blade `@json($array);`

----------------------------------------------------------------------------

## Components & Slots

`@component('alert') ... @endcomponent`

> ***component*** we would like to reuse throughout our application .

> we can define component as follows :
```
<!-- /resources/views/alert.blade.php -->
<div class="alert alert-danger">
    {{ $slot }}
</div>
```

`{{ $variable }}`

> To echo the value of this variable

`@componentFirst(['custom.alert', 'alert'])`

> to load the first view that exists from a given array of possible views

```
<div class="alert alert-danger">
    <div class="alert-title">{{ $title }}</div>

    {{ $slot }}
</div>
```
```
@component('alert')
    @slot('title')
        Forbidden
    @endslot

    You are not allowed to access this resource!
@endcomponent
```
> we can inject content into the named slot using the `@slot` directive. Any content not within a `@slot` directive will be passed to the component in the `$slot` variable

### Passing Additional Data To Components
```
@component('alert', ['foo' => 'bar'])
    ...
@endcomponent
```
> All of the data of the array will be made available to the component template as variables

### Aliasing Components
> we can alias components for easier aceess in `AppServiceProvider` as Follows :

```
use Illuminate\Support\Facades\Blade;

Blade::component('components.alert', 'alert');
```
> Once the component has been aliased, you may render it using a directive:

```
@alert(['type' => 'danger'])
    You are not allowed to access this resource!
@endalert
```
----------------------------------------------------------------------------
## Control Structures

### `if` Statement :

```
@if (count($records) === 1)
    I have one record!
@elseif (count($records) > 1)
    I have multiple records!
@else
    I don't have any records!
@endif
```

### `if not` Statement :

```
@unless (Auth::check())
    You are not signed in.
@endunless
```

### `isset` control

```
@isset($records)
    // $records is defined and is not null...
@endisset
```

### `empty()` function

```
@empty($records)
    // $records is "empty"...
@endempty
```

### Authentication Directives

```
@auth
    // The user is authenticated...
@endauth

@guest
    // The user is not authenticated...
@endguest
```

### check if Section has content

```
@hasSection('navigation')
    <div class="pull-right">
        @yield('navigation') // if section has content display content
    </div>

    <div class="clearfix"></div> // if section doesn't have content , display this content
@endif
```

### `switch` Statements

```
@switch($i)
    @case(1)
        First case...
        @break

    @case(2)
        Second case...
        @break

    @default
        Default case...
@endswitch
```

### Loops :

#### `for` Loop :

```
@for ($i = 0; $i < 10; $i++)
    The current value is {{ $i }}
@endfor
```

### `foreach` Loop :

```
@foreach ($users as $user)
    <p>This is user {{ $user->id }}</p>
@endforeach
```

### `while` Loop :

```
@while (true)
    <p>I'm looping forever.</p>
@endwhile
```
> When using loops you may also end the loop or skip the current iteration:

```
@foreach ($users as $user)
    @if ($user->type == 1)
        @continue
    @endif

    <li>{{ $user->name }}</li>

    @if ($user->number == 5)
        @break
    @endif
@endforeach
```

### The `$loop` - **will be available inside of your loop** - variable contains a variety of useful properties :

|Property |	Description                                               |
|  ---    | ---                                                       |
|`$loop->index`|	The index of the current loop iteration (starts at 0).|
|`$loop->iteration`|	The current loop iteration (starts at 1).|
|`$loop->remaining`|	The iterations remaining in the loop.|
|`$loop->count`|	The total number of items in the array being iterated.|
|`$loop->first`|	Whether this is the first iteration through the loop.|
|`$loop->last`|	Whether this is the last iteration through the loop.|
|`$loop->even`|	Whether this is an even iteration through the loop.|
|`$loop->odd`	|Whether this is an odd iteration through the loop.|
|`$loop->depth`|	The nesting level of the current loop.|
|`$loop->parent`|	When in a nested loop, the parent's loop variable.|

## Comments :

> `{{-- you can write your comment here and will not be present in the rendered HTML --}}`

## PHP :
```
@php
    // to embed PHP code into your views
@endphp

```

## Forms :

> `@csrf` , you should include a hidden CSRF token field in every form you define

>  `@method(`**'Method'**`)` **Method** may be [ `PUT` ,  `PATCH` , or  `DELETE`]

> Since HTML forms can't make `PUT, PATCH, or DELETE` requests, you will need to add a hidden `_method` field to spoof these HTTP verbs , use `@method` directive for that

## Validation Errors :

> The `@error` directive may be used to quickly check if **validation error messages** exist

----------------------------------------------------------------------------
# References :
1. https://laravel.com/docs/6.x/blade
2. https://stackoverflow.com/questions/50530267/laravel-blade-stop-vs-show-vs-endsection-vs-append
3. https://laravel-guide.readthedocs.io/en/latest/blade/#blade-templates
