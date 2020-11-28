# nest-microservices-redis
- A NestJS module for `generator-nest-microservices` yeoman template for redis features
### How to use
- install package with `npm i -S nest-microservices-redis`
- Register the `RedisModule` to your feature modules:
```
@Module({})
export class AppModule {
  static register(config: ConfigOptions): DynamicModule {
    return {
      module: AppModule,
      imports: [
        RedisModule.register(config.redisOptions),
        ...
      ],
    };
  }
}
```
- Once `RedisModule` is registered, then you can use `RedisService` to get/set keys from cache or use pub/sub
```
export class ExampleController {
  constructor (private service: RedisService) {
    super (service);
  }

  await get () {
    this.redisService.get<any>('my-cached-stuff');
  }
}
```
### Redis options
|Property|Type|Required|Description|
|-|-|-|-|
|appName|`MessageQueueOptions`|true| The channel name to be used for your pub/sub
|host|`String`|true| Host of your Redis server
|port|`Number`|true| Port used for your Redis server
