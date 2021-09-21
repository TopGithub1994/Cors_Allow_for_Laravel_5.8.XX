# Cors Allow for Laravel 5.8.XX

## 1. Goto `app/Http/Kernel.php`  and Add the following line to the $middleware array in `app/Http/Kernel.php`.

~~~
\App\Http\Middleware\CheckCors::class,
~~~

## 2. Goto `app/Http/Middleware` and create file name `CheckCors.php` copy code below to file CheckCors.php.

~~~
<?php

namespace App\Http\Middleware;

use Closure;

class CheckCors
{
    /**
     * Handle an incoming request.
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  \Closure  $next
     * @return mixed
     */
    public function handle($request, Closure $next)
    {
            return $next($request)
                ->header('Access-Control-Allow-Origin', '*')
                ->header('Access-Control-Allow-Methods', 'POST, GET, OPTIONS, PUT, DELETE')
                ->header('Access-Control-Max-Age', '86400')
                ->header('Access-Control-Allow-Headers', 'Content-Type, Authorization, X-Requested-With');
    
    
    
    /*$headers = [
            'Access-Control-Allow-Origin'      => '*',
            'Access-Control-Allow-Methods'     => 'POST, GET, OPTIONS, PUT, DELETE',
            'Access-Control-Allow-Credentials' => 'true',
            'Access-Control-Max-Age'           => '86400',
            'Access-Control-Allow-Headers'     => 'Content-Type, Authorization, X-Requested-With'
        ];

        if ($request->isMethod('OPTIONS'))
        {
            return response()->json('{"method":"OPTIONS"}', 200, $headers);
        }

        $response = $next($request);
        foreach($headers as $key => $value)
        {
            $response->header($key, $value);
        }

        return $response;*/
    
    }
}

~~~

~~~
php artisan config:cache
~~~

