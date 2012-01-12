# Bash script for inspecting an item or set of items from Nginx cache

## Introduction 

This simple script **inspects** an item or set of items from
[Nginx](http://nginx.org) cache, be it
[`fastcgi`](http://wiki.nginx.org/HttpFcgiModule#fastcgi_cache) or
[`proxy`](http://wiki.nginx.org/HttpProxyModule#proxy_cache).

It accepts a
[`grep` pattern](http://www.gnu.org/software/grep/manual/grep.html#Fundamental-Structure)
as argument to search for cached items in the given cache directory.

This script uses `grep`
[**basic**](http://www.gnu.org/software/grep/manual/grep.html#Basic-vs-Extended)
regular expressions. Pressuposes the use of
[GNU `grep`](http://www.gnu.org/software/grep/manual/grep.html).

It **requires** a GNU grep version that supports
[PCRE](ww.gnu.org/software/grep/manual/grep.html#grep-Programs).

Non ASCII keys are usually **filtered** out. If you want to inspect non
ASCII based keys then invoke the script with an additional 3rd argument.

The script **requires** `rw` (read-write) access to the cache
directory.

## Usage

 1. Inspect `foobar.css` from the `/var/cache/nginx/baz` cache.
 
        nginx-cache-purge "foobar.cs" /var/cache/nginx/baz
    
 2. Inspect all JPEG files from the `/var/cache/nginx/img` cache.
 
        nginx-cache-purge "\.jpe*g" /var/cache/nginx/img 
        
 3. Inspect all URIs starting with baz and match also non ASCII keys.
 
        nginx-cache-purge "^baz" /var/cache/nginx/static 1

## Installation 

 1. Clone the repo:
 
        git clone git://github.com/perusio/nginx-cache-inspector.git
    
 2. Place the script in a convenient place.
 
 3. Done.

## See also 

There's another [script](https://github.com/perusio/nginx-cache-purge)
on github for **purging** items from the cache.
