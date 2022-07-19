
```cs
// <auto-generated>
//     Generated by the protocol buffer compiler.  DO NOT EDIT!
//     source: summator.proto
// </auto-generated>
#pragma warning disable 0414, 1591
#region Designer generated code

using grpc = global::Grpc.Core;

public static partial class Summator
{
  static readonly string __ServiceName = "Summator";

  static readonly grpc::Marshaller<global::Number1> __Marshaller_Number1 = grpc::Marshallers.Create((arg) => global::Google.Protobuf.MessageExtensions.ToByteArray(arg), global::Number1.Parser.ParseFrom);
  static readonly grpc::Marshaller<global::Number2> __Marshaller_Number2 = grpc::Marshallers.Create((arg) => global::Google.Protobuf.MessageExtensions.ToByteArray(arg), global::Number2.Parser.ParseFrom);

  static readonly grpc::Method<global::Number1, global::Number2> __Method_Sum = new grpc::Method<global::Number1, global::Number2>(
      grpc::MethodType.Unary,
      __ServiceName,
      "sum",
      __Marshaller_Number1,
      __Marshaller_Number2);

  /// <summary>Service descriptor</summary>
  public static global::Google.Protobuf.Reflection.ServiceDescriptor Descriptor
  {
    get { return global::SummatorReflection.Descriptor.Services[0]; }
  }

  /// <summary>Base class for server-side implementations of Summator</summary>
  [grpc::BindServiceMethod(typeof(Summator), "BindService")]
  public abstract partial class SummatorBase
  {
    public virtual global::System.Threading.Tasks.Task<global::Number2> Sum(global::Number1 request, grpc::ServerCallContext context)
    {
      throw new grpc::RpcException(new grpc::Status(grpc::StatusCode.Unimplemented, ""));
    }

  }

  /// <summary>Client for Summator</summary>
  public partial class SummatorClient : grpc::ClientBase<SummatorClient>
  {
    /// <summary>Creates a new client for Summator</summary>
    /// <param name="channel">The channel to use to make remote calls.</param>
    public SummatorClient(grpc::ChannelBase channel) : base(channel)
    {
    }
    /// <summary>Creates a new client for Summator that uses a custom <c>CallInvoker</c>.</summary>
    /// <param name="callInvoker">The callInvoker to use to make remote calls.</param>
    public SummatorClient(grpc::CallInvoker callInvoker) : base(callInvoker)
    {
    }
    /// <summary>Protected parameterless constructor to allow creation of test doubles.</summary>
    protected SummatorClient() : base()
    {
    }
    /// <summary>Protected constructor to allow creation of configured clients.</summary>
    /// <param name="configuration">The client configuration.</param>
    protected SummatorClient(ClientBaseConfiguration configuration) : base(configuration)
    {
    }

    public virtual global::Number2 Sum(global::Number1 request, grpc::Metadata headers = null, global::System.DateTime? deadline = null, global::System.Threading.CancellationToken cancellationToken = default(global::System.Threading.CancellationToken))
    {
      return Sum(request, new grpc::CallOptions(headers, deadline, cancellationToken));
    }
    public virtual global::Number2 Sum(global::Number1 request, grpc::CallOptions options)
    {
      return CallInvoker.BlockingUnaryCall(__Method_Sum, null, options, request);
    }
    public virtual grpc::AsyncUnaryCall<global::Number2> SumAsync(global::Number1 request, grpc::Metadata headers = null, global::System.DateTime? deadline = null, global::System.Threading.CancellationToken cancellationToken = default(global::System.Threading.CancellationToken))
    {
      return SumAsync(request, new grpc::CallOptions(headers, deadline, cancellationToken));
    }
    public virtual grpc::AsyncUnaryCall<global::Number2> SumAsync(global::Number1 request, grpc::CallOptions options)
    {
      return CallInvoker.AsyncUnaryCall(__Method_Sum, null, options, request);
    }
    /// <summary>Creates a new instance of client from given <c>ClientBaseConfiguration</c>.</summary>
    protected override SummatorClient NewInstance(ClientBaseConfiguration configuration)
    {
      return new SummatorClient(configuration);
    }
  }

  /// <summary>Creates service definition that can be registered with a server</summary>
  /// <param name="serviceImpl">An object implementing the server-side handling logic.</param>
  public static grpc::ServerServiceDefinition BindService(SummatorBase serviceImpl)
  {
    return grpc::ServerServiceDefinition.CreateBuilder()
        .AddMethod(__Method_Sum, serviceImpl.Sum).Build();
  }

  /// <summary>Register service method with a service binder with or without implementation. Useful when customizing the  service binding logic.
  /// Note: this method is part of an experimental API that can change or be removed without any prior notice.</summary>
  /// <param name="serviceBinder">Service methods will be bound by calling <c>AddMethod</c> on this object.</param>
  /// <param name="serviceImpl">An object implementing the server-side handling logic.</param>
  public static void BindService(grpc::ServiceBinderBase serviceBinder, SummatorBase serviceImpl)
  {
    serviceBinder.AddMethod(__Method_Sum, serviceImpl == null ? null : new grpc::UnaryServerMethod<global::Number1, global::Number2>(serviceImpl.Sum));
  }

}
#endregion

```