---
title: Zpracování chyb - gRPC pro vývojáře WCF
description: Témata týkající se zpracování chyb v gRPC. Obsahuje tabulku nejčastěji používaných stavových kódů.
ms.date: 09/02/2019
ms.openlocfilehash: 64a2355a8bd608c074f9bc420312b23aba0c1fb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988944"
---
# <a name="error-handling"></a>Zpracování chyb

Windows Communication Foundation (WCF) používá <xref:System.ServiceModel.FaultException%601> a [FaultContract](xref:System.ServiceModel.FaultContractAttribute) poskytnout podrobné informace o chybě, včetně podpory standardu chyba SOAP.

Bohužel, aktuální verze gRPC postrádá sofistikovanost nalezenou s WCF a má pouze omezené vestavěné zpracování chyb na základě jednoduchých stavových kódů a metadat. Následující tabulka obsahuje stručný průvodce nejčastěji používanými stavovými kódy:

| Kód stavu | Problém |
| ----------- | ------- |
| `GRPC_STATUS_UNIMPLEMENTED` | Metoda nebyla napsána. |
| `GRPC_STATUS_UNAVAILABLE` | Problém s celou službou. |
| `GRPC_STATUS_UNKNOWN` | Neplatná odpověď. |
| `GRPC_STATUS_INTERNAL` | Problém s kódováním/dekódováním. |
| `GRPC_STATUS_UNAUTHENTICATED` | Ověření se nezdařilo. |
| `GRPC_STATUS_PERMISSION_DENIED` | Autorizace se nezdařila. |
| `GRPC_STATUS_CANCELLED` | Hovor byl zrušen, obvykle volajícím. |

## <a name="raise-errors-in-aspnet-core-grpc"></a>Zvýšení chyb v ASP.NET Core gRPC

Služba ASP.NET Core gRPC může odeslat odpověď `RpcException`na chybu vyvoláním , který může být zachycen klientem, jako by byl ve stejném procesu. Musí `RpcException` obsahovat stavový kód a popis a volitelně může obsahovat metadata a delší zprávu o výjimce. Metadata lze použít k odeslání podpůrných dat, podobně jako `FaultContract` objekty mohou přenášet další data pro chyby WCF.

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

## <a name="catch-errors-in-grpc-clients"></a>Zachytávat chyby v klientech gRPC

Stejně jako WCF <xref:System.ServiceModel.FaultException%601> klienti mohou zachytit chyby, `RpcException` gRPC klient může zachytit zpracování chyb. Protože `RpcException` není obecný typ, nelze zachytit různé typy chyb v různých blocích. Ale můžete použít C# *filtry výjimek* funkce deklarovat samostatné `catch` bloky pro různé stavové kódy, jak je znázorněno v následujícím příkladu:

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
> Pokud zadáte další metadata pro chyby, nezapomeňte zdokumentovat příslušné klíče a hodnoty `.proto` v dokumentaci k rozhraní API nebo v komentářích v souboru.

## <a name="grpc-richer-error-model"></a>gRPC bohatší chybový model

Google vyvinul [bohatší chybový model,](https://cloud.google.com/apis/design/errors#error_model) který je spíše jako [WCF FaultContract](xref:System.ServiceModel.FaultContractAttribute), ale tento model není podporován v C# dosud. V současné době je k dispozici pouze pro Go, Java, Python a C++.

>[!div class="step-by-step"]
>[Předchozí](metadata.md)
>[další](ws-protocols.md)
