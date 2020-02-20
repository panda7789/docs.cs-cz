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
# <a name="comparing-wcf-to-grpc"></a>Porovnávání WCF s gRPC

Předchozí kapitola vám poskytla dobrý pohled na Protobuf a způsob, jakým gRPC zpracovává zprávy. Než provedete podrobný převod z Windows Communication Foundation (WCF) na gRPC, je důležité znát, jak jsou funkce dostupné v rámci služby WCF zpracovávány v gRPC a jaká alternativní řešení můžete použít, pokud neexistuje žádný ekvivalent gRPC. Konkrétně tato kapitola se zabývá následujícími tématy:

- Operace a metody
- Vazby a přenosy
- Typy RPC
- Metadata
- Zpracování chyb
- Protokoly WS-\*

## <a name="grpc-example"></a>Příklad gRPC

Při vytváření nového projektu ASP.NET Core 3,0 gRPC ze sady Visual Studio 2019 nebo příkazového řádku, je pro vás vygenerován ekvivalent gRPC "Hello World". Skládá se z `greeter.proto` souboru, který definuje službu a její zprávy a `GreeterService.cs` soubor s implementací služby.

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

Tato kapitola bude odkazovat na tento ukázkový kód při vysvětlení různých konceptů a funkcí gRPC.

>[!div class="step-by-step"]
>[Předchozí](protobuf-maps.md)
>[Další](wcf-endpoints-grpc-methods.md)
