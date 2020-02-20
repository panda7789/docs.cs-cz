---
title: Porovnání WCF s gRPC-gRPC pro vývojáře WCF
description: Porovnání rozhraní WCF a gRPC pro vytváření distribuovaných aplikací.
ms.date: 09/02/2019
ms.openlocfilehash: 4f54db76c9512b770b4dd993496d95437dd89753
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503339"
---
# <a name="comparing-wcf-to-grpc"></a><span data-ttu-id="75bf8-103">Porovnávání WCF s gRPC</span><span class="sxs-lookup"><span data-stu-id="75bf8-103">Comparing WCF to gRPC</span></span>

<span data-ttu-id="75bf8-104">Předchozí kapitola vám poskytla dobrý pohled na Protobuf a způsob, jakým gRPC zpracovává zprávy.</span><span class="sxs-lookup"><span data-stu-id="75bf8-104">The previous chapter gave you a good look at Protobuf and how gRPC handles messages.</span></span> <span data-ttu-id="75bf8-105">Než provedete podrobný převod z Windows Communication Foundation (WCF) na gRPC, je důležité znát, jak jsou funkce dostupné v rámci služby WCF zpracovávány v gRPC a jaká alternativní řešení můžete použít, pokud neexistuje žádný ekvivalent gRPC.</span><span class="sxs-lookup"><span data-stu-id="75bf8-105">Before you work through a detailed conversion from Windows Communication Foundation (WCF) to gRPC, it's important know how the features available in WCF are handled in gRPC and what workarounds you can use when there's no gRPC equivalent.</span></span> <span data-ttu-id="75bf8-106">Konkrétně tato kapitola se zabývá následujícími tématy:</span><span class="sxs-lookup"><span data-stu-id="75bf8-106">In particular, this chapter will cover the following subjects:</span></span>

- <span data-ttu-id="75bf8-107">Operace a metody</span><span class="sxs-lookup"><span data-stu-id="75bf8-107">Operations and methods</span></span>
- <span data-ttu-id="75bf8-108">Vazby a přenosy</span><span class="sxs-lookup"><span data-stu-id="75bf8-108">Bindings and transports</span></span>
- <span data-ttu-id="75bf8-109">Typy RPC</span><span class="sxs-lookup"><span data-stu-id="75bf8-109">RPC types</span></span>
- <span data-ttu-id="75bf8-110">Metadata</span><span class="sxs-lookup"><span data-stu-id="75bf8-110">Metadata</span></span>
- <span data-ttu-id="75bf8-111">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="75bf8-111">Error handling</span></span>
- <span data-ttu-id="75bf8-112">Protokoly WS-\*</span><span class="sxs-lookup"><span data-stu-id="75bf8-112">WS-\* protocols</span></span>

## <a name="grpc-example"></a><span data-ttu-id="75bf8-113">Příklad gRPC</span><span class="sxs-lookup"><span data-stu-id="75bf8-113">gRPC example</span></span>

<span data-ttu-id="75bf8-114">Při vytváření nového projektu ASP.NET Core 3,0 gRPC ze sady Visual Studio 2019 nebo příkazového řádku, je pro vás vygenerován ekvivalent gRPC "Hello World".</span><span class="sxs-lookup"><span data-stu-id="75bf8-114">When you create a new ASP.NET Core 3.0 gRPC project from Visual Studio 2019 or the command line, the gRPC equivalent of "Hello World" is generated for you.</span></span> <span data-ttu-id="75bf8-115">Skládá se z `greeter.proto` souboru, který definuje službu a její zprávy a `GreeterService.cs` soubor s implementací služby.</span><span class="sxs-lookup"><span data-stu-id="75bf8-115">It consists of a `greeter.proto` file that defines the service and its messages, and a `GreeterService.cs` file with an implementation of the service.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "HelloGrpc";

package Greet;

// The greeting service definition.
service Greeter {
  // Sends a greeting
  rpc SayHello (HelloRequest) returns (HelloReply);
}

// The request message that contains the user's name.
message HelloRequest {
  string name = 1;
}

// The response message that contains the greetings.
message HelloReply {
  string message = 1;
}
```

```csharp
using System.Threading.Tasks;
using Grpc.Core;
using Microsoft.Extensions.Logging;

namespace HelloGrpc
{
    public class GreeterService : Greeter.GreeterBase
    {
        private readonly ILogger<GreeterService> _logger;
        public GreeterService(ILogger<GreeterService> logger)
        {
            _logger = logger;
        }

        public override Task<HelloReply> SayHello(HelloRequest request, ServerCallContext context)
        {
            return Task.FromResult(new HelloReply
            {
                Message = "Hello " + request.Name
            });
        }
    }
}
```

<span data-ttu-id="75bf8-116">Tato kapitola bude odkazovat na tento ukázkový kód při vysvětlení různých konceptů a funkcí gRPC.</span><span class="sxs-lookup"><span data-stu-id="75bf8-116">This chapter will refer to this example code when explaining different concepts and features of gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="75bf8-117">[Předchozí](protobuf-maps.md)
>[Další](wcf-endpoints-grpc-methods.md)</span><span class="sxs-lookup"><span data-stu-id="75bf8-117">[Previous](protobuf-maps.md)
[Next](wcf-endpoints-grpc-methods.md)</span></span>
