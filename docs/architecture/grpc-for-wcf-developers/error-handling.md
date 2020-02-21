---
title: Zpracování chyb – gRPC pro vývojáře WCF
description: Témata týkající se zpracování chyb v gRPC. Obsahuje tabulku nejčastěji používaných stavových kódů.
ms.date: 09/02/2019
ms.openlocfilehash: c380c651f854adc97e8b2ead36d30c3b83662aac
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542790"
---
# <a name="error-handling"></a>Zpracování chyb

Windows Communication Foundation (WCF) používá <xref:System.ServiceModel.FaultException%601> a [FaultContract](xref:System.ServiceModel.FaultContractAttribute) k poskytování podrobných informací o chybách, včetně podpory standardu SOAP chyb.

Aktuální verze gRPC bohužel neobsahuje sofistikovanější nalezené pomocí WCF a má pouze omezené integrované zpracování chyb na základě jednoduchých stavových kódů a metadat. V následující tabulce je Stručná příručka k nejčastěji používaným stavovým kódům:

| Kód stavu | Problém |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nebyla zapsána. |
| `GRPC_STATUS_UNAVAILABLE` | Problém s celou službou. |
| `GRPC_STATUS_UNKNOWN` | Neplatná odpověď. |
| `GRPC_STATUS_INTERNAL` | Problém s kódováním/dekódováním. |
| `GRPC_STATUS_UNAUTHENTICATED` | Ověřování se nezdařilo. |
| `GRPC_STATUS_PERMISSION_DENIED` | Ověření se nepovedlo. |
| `GRPC_STATUS_CANCELLED` | Volání bylo zrušeno, obvykle volající. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Vyvolávání chyb v ASP.NET Core gRPC

Služba ASP.NET Core gRPC může odeslat chybovou odpověď vyvoláním `RpcException`, kterou může klient zachytit, jako kdyby byl ve stejném procesu. `RpcException` musí zahrnovat stavový kód a popis a může volitelně zahrnovat metadata a delší zprávu o výjimce. Metadata lze použít k odesílání podpůrných dat, podobně jako `FaultContract` objekty mohou pro chyby WCF přenášet další data.

```csharp
public async Task<GetPortfolioResponse> GetPortfolio(GetPortfolioRequest request, ServerCallContext context)
{
    var user = context.GetHttpContext().User;
    if (!ValidateUser(user))
    {
        var metadata = new Metadata
        {
            { "User", user.Identity.Name }
        };
        throw new RpcException(new Status(StatusCode.PermissionDenied, "Permission denied"), metadata);
    }
}
```

## <a name="catch-errors-in-grpc-clients"></a>Zachycení chyb v klientech gRPC

Stejně jako klienti WCF můžou zachytit chyby <xref:System.ServiceModel.FaultException%601>, klient gRPC může zachytit `RpcException` a zpracovávat chyby. Vzhledem k tomu, že `RpcException` není obecný typ, nemůžete zachytávání různých typů chyb v různých blocích. Můžete ale použít C#funkci *filtry výjimek* pro deklaraci samostatných `catch`ch bloků pro různé stavové kódy, jak je znázorněno v následujícím příkladu:

```csharp
try
{
    var portfolio = await client.GetPortfolioAsync(new GetPortfolioRequest { Id = id });
}
catch (RpcException ex) when (ex.StatusCode == StatusCode.PermissionDenied)
{
    var userEntry = ex.Trailers.FirstOrDefault(e => e.Key == "User");
    Console.WriteLine($"User '{userEntry.Value}' does not have permission to view this portfolio.");
}
catch (RpcException)
{
    // Handle any other error type ...
}
```

> [!IMPORTANT]
> Když zadáte další metadata pro chyby, nezapomeňte zdokumentovat příslušné klíče a hodnoty v dokumentaci k rozhraní API nebo v komentářích v souboru `.proto`.

## <a name="grpc-richer-error-model"></a>model gRPC bohatých chyb

Google vyvinul [model rozsáhlejších chyb](https://cloud.google.com/apis/design/errors#error_model) , který je více podobný jako [FaultContract](xref:System.ServiceModel.FaultContractAttribute)WCF, ale tento model C# ještě není podporovaný. V současné době je dostupná jenom pro jazyky přejít, Java, Python a C++.

>[!div class="step-by-step"]
>[Předchozí](metadata.md)
>[Další](ws-protocols.md)
