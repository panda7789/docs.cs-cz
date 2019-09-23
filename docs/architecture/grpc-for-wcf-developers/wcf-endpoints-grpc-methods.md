---
title: Koncové body WCF a metody gRPC – gRPC pro vývojáře WCF
description: Porovnání koncových bodů WCF deklarované s atributy třídy ServiceContract a OperationContract a metody gRPC deklarované v Protobuf
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 08f2d0874417c0ca319b0c193e6108536376d693
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184062"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Koncové body WCF a metody gRPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Při psaní kódu aplikace v technologii WCF použijte jednu z následujících metod:

- Kód aplikace píšete ve třídě a metody lze pomocí atributu [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Deklarujete rozhraní pro službu a přidáte do rozhraní atributy [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .

Například ekvivalent služby typu `greet.proto` WCF na službu Greeter může být zapsán následujícím způsobem:

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Kapitola 3 ukázala, že definice zpráv Protobuf slouží ke generování datových tříd. Deklarace služby a metody se používají ke generování základních tříd, ze kterých dědíte pro implementaci služby. Pouze deklarujete metody, které mají být implementovány `.proto` v souboru, a kompilátor vygeneruje základní třídu s virtuálními metodami, které musíte přepsat.

## <a name="operationcontract-properties"></a>Vlastnosti OperationContract

Atribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) má vlastnosti pro kontrolu a vylepšení způsobu, jakým funguje. metody gRPC nenabízejí tento typ ovládacího prvku. Následující tabulka uvádí tyto `OperationContract` vlastnosti a způsob, jakým jsou funkce, které určíte (nebo nejsou) řešeny v gRPC:

| `OperationContract`majetek | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Identifikátor URI, který identifikuje operaci gRPC `package`používá název `service` a `rpc` ze souboru.`.proto` |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Všechny metody služby gRPC vrací `Task` objekty. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Viz poznámka níže. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Jednosměrné metody gRPC vracejí `Empty` výsledky nebo používají streamování klientů. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Viz poznámka níže. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Související s protokolem SOAP, žádný význam v gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Žádné šifrování zpráv; šifrování sítě je zpracované v transportní vrstvě (TLS přes HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Související s protokolem SOAP, žádný význam v gRPC. |

Vlastnost umožňuje označit, že metoda v rámci [třídy ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nemůže být první metodou volanou jako součást relace. `IsInitiating` `IsTerminating` Vlastnost způsobí, že server ukončí relaci po volání operace (nebo klienta, pokud se používá u klienta zpětného volání). V gRPC jsou datové proudy vytvářeny pomocí jediné metody a explicitně uzavřeny. Viz [streamování gRPC](rpc-types.md#grpc-streaming).

Další informace o zabezpečení a šifrování gRPC naleznete v části [Kapitola 6](security.md).

>[!div class="step-by-step"]
>[Předchozí](wcf-services-to-grpc-comparison.md)
>[Další](wcf-bindings.md)
