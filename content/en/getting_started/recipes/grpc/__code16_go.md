
```go
// Pre-requisites
import (
	"context"
	"fmt"
	"mymodule/calculations"
	"mymodule/protos"

	cconf "github.com/pip-services3-go/pip-services3-commons-go/config"
	cref "github.com/pip-services3-go/pip-services3-commons-go/refer"
	grpcclients "github.com/pip-services3-go/pip-services3-grpc-go/clients"
)

// gRPC server
type MyGrpcService struct {
	grpcservices.GrpcService
	protos.SummatorServer
}

func NewMyGrpcService() *MyGrpcService {
	c := &MyGrpcService{}
	c.GrpcService = *grpcservices.InheritGrpcService(c, "Summator")
	return c
}

func (c *MyGrpcService) Sum(ctx context.Context, req *protos.Number1) (result *protos.Number2, err error) {

	res := calculations.Summator(req.GetValue1(), req.GetValue2())
	result = &protos.Number2{Value: res}
	return result, nil
}

func (c *MyGrpcService) Register() {
	protos.RegisterSummatorServer(c.Endpoint.GetServer(), c)
}
    
service := NewMyGrpcService()
service.Configure(cconf.NewConfigParamsFromTuples(
	"connection.protocol", "http",
	"connection.host", "localhost",
	"connection.port", 50055,
))

service.SetReferences(cref.NewEmptyReferences())

err := service.Open("123")
```