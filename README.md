# Extraload

Powerful ETL library.

## Note

> This is just a draft, the implementation will follow.

## Summary

Inspired by friends @docteurklein awesome library [php-etl](https://github.com/docteurklein/php-etl), it will provide 3 main ETL interfaces. 

## Extract

We can start with few simple extractors, like json and csv.

## Transform

Interface is enough, maybe a callback transformer and one chainable that allows chaining of multiple transformers.

## Load

We can start with few simple loaders, like csv and console.

## Pipeline

In addition, we will have a pipeline that will glue them together and make sure library is easy to use. 
Given extractor, transformer and loader, pipeline will be capable to handle ETL.

```php
(new Extraload\Pipeline(
    new XmlLoader('http://umpirsky.com/'),
    new AwesomeTransformer(),
    new ConsoleLoader()
))->run();
```

## Events

We should use some events to make it easyer to hook into ETL pipeline for easier logging, progress tracking...

## Easy to use

Not high priority, but there should also be some power that will make library easy to use. Smart factories that can create csv loader from simple file path, or xml extractor from url to xml file.

```php
(new Extraload\DynamicPipeline())
    ->extract('http://umpirsky.com/sample.xml')
    ->transform('array_change_key_case')
    ->load('/home/umpirsky/sample.json')
;
```

## Parallelization

Ability to run E, T and L in parallel. Probably using services like RabbitMQ or similar.

## DX

Should be developer friendly, easy to understand, use and flexible to extend.

Useful debugging things like console [table](http://symfony.com/doc/current/components/console/helpers/table.html) loeader can also help a lot.
