---
title: Porovnání WCF s gRPC-gRPC pro vývojáře WCF
description: Porovnání rozhraní WCF a gRPC pro vytváření distribuovaných aplikací.
ms.date: 09/02/2019
ms.openlocfilehash: 312492dcce4bdef61feff0bf924c6df287b9c676
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966956"
---
# <a name="comparing-wcf-to-grpc"></a>Porovnávání WCF s gRPC

Předchozí kapitola by měla mít za cíl dobrý pohled na Protobuf a způsob, jakým gRPC zpracovává zprávy. Před provedením podrobného převodu z WCF na gRPC je důležité pohlížet na to, jak se rozsah funkcí aktuálně dostupných ve službě WCF zpracovává v gRPC a jaká alternativní řešení můžete použít, když se zdá, že se nejeví jako ekvivalentní gRPC. Konkrétně tato kapitola se zabývá následujícími tématy:

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

// The request message containing the user's name.
message HelloRequest {
  string name = 1;
}

// The response message containing the greetings.
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
