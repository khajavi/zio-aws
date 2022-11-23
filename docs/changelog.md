---
id: changelog
title: Changelog
---

# Version history

Note: this is a manually maintained list of important changes. Because of having auto-release from CI, this
list may not reflect _all_ changes immediately. Dependencies are continuously updated and are not documented here.

#### 5.x.x.x
- Migrated to `ZIO 2.0.0` 
- Moved to the ZIO organisation
- Using the new ZIO service pattern
- Changed getter naming to match `zio-k8s`
- Using `zio-prelude` _newtype wrappers_ for primitives
- Using `ZIO` aspects as a base of `AwsCallAspect`
- Exposed lower level pagination API calls beside the streaming ones
- Using the `Optional` type instead of `Option` to reduce boilerplate

See the [migration guide](migration_guide.md) for more information.

#### 4.17.104.1
- Migrated to `zio-config v2.0.0`

#### 3.15.35.5
- Support for defining dual HTTP/1.1 and HTTP/2 `HttpClient` layers
- Convert model case classes to `.ReadOnly` trait with `.asReadOnly`

#### 3.15.19.10
- Fix for libraries that use the `Integer` alias for ints (such as `zio-aws-sqs`)

#### 3.15.19.8
- Updated [fs2](https://fs2.io) release that fixes the http4s backend

#### 3.15.19.7
- Fix for event streaming wrappers such as `subscribeToShard` in `zio-aws-kinesis`

#### 3.15.16.0

- Introduced automatic release from CI, each new AWS SDK release triggers a new `zio-aws` build now
- zio-config support 

#### 2.14.7.0

- Updated to AWS SDK 2.14.7
- Fix an [issue](https://github.com/vigoo/zio-aws/issues/23) with http4s streaming uploads
- `Iterable` in place of `List` in the request models
- The akka-http client now gets the _actor system_ from the environment
- Code generator rewritten as an sbt plugin

#### 2.14.3.0
API breaking changes to make the streaming interface more ergonomic:
- Input/output byte streams are now flat (`ZStream[Any, AwsError, Byte]` instead of `ZStream[Any, AwsError, Chunk[Byte]`)
- Streaming operations return a `ZStream` that performs the request on first pull instead of a `ZIO[..., ZStream[...]]`
- Streaming for paginated operations that does not have a paginator in the Java SDK
- No `xxxStream` variants, streaming is the default and only interface for paginatable operations
- Updated to AWS SDK 2.14.3
- Fixed handling of some error cases
- Scala 2.12 version is now available

#### 1.13.69.1
Initial release republished with fixed metadata in POMs

#### 1.13.69.0
Initial release based on AWS Java SDK 2.13.69  
