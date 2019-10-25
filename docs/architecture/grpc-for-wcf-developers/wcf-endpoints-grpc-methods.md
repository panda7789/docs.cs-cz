---
title: Koncové body WCF a metody gRPC – gRPC pro vývojáře WCF
description: Porovnání koncových bodů WCF deklarované s atributy třídy ServiceContract a OperationContract a metody gRPC deklarované v Protobuf
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 1cb7fedf1fbb632438134375306801f356d7b921
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846057"
---
# <a name="wcf-endpoints-and-grpc-methods"></a>Koncové body WCF a metody gRPC

Při psaní kódu aplikace v technologii WCF použijte jednu z následujících metod:

- Kód aplikace píšete ve třídě a metody lze pomocí atributu [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .
- Deklarujete rozhraní pro službu a přidáte do rozhraní atributy [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .

Například ekvivalent služby `greet.proto`ového pozdravu WCF je možné zapsat takto:

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

Kapitola 3 ukázala, že definice zpráv Protobuf slouží ke generování datových tříd. Deklarace služby a metody se používají ke generování základních tříd, ze kterých dědíte pro implementaci služby. Pouze deklarujete metody, které mají být implementovány v souboru `.proto` a kompilátor generuje základní třídu s virtuálními metodami, které musíte přepsat.

## <a name="operationcontract-properties"></a>Vlastnosti OperationContract

Atribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) má vlastnosti pro kontrolu a vylepšení způsobu, jakým funguje. metody gRPC nenabízejí tento typ ovládacího prvku. Následující tabulka uvádí tyto vlastnosti `OperationContract` a způsob, jakým jsou funkce, které určíte (nebo nejsou) řešeny v gRPC:

| `OperationContract` – vlastnost | gRPC                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | Identifikátor URI, který identifikuje operaci gRPC používá název `package``service` a `rpc` ze souboru `.proto`. |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | Všechny metody služby gRPC vrací `Task` objekty. |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | Viz poznámka níže. |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | Jednosměrné metody gRPC vrací `Empty` výsledky nebo používají streamování klientů. |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | Viz poznámka níže. |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | Související s protokolem SOAP, žádný význam v gRPC. |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | Žádné šifrování zpráv; šifrování sítě je zpracované v transportní vrstvě (TLS přes HTTP/2). |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | Související s protokolem SOAP, žádný význam v gRPC. |

Vlastnost `IsInitiating` umožňuje označit, že metoda v rámci [třídy ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nemůže být první metodou volanou jako součást relace. Vlastnost `IsTerminating` způsobí, že server ukončí relaci po volání operace (nebo klienta, pokud se používá u klienta zpětného volání). V gRPC jsou datové proudy vytvářeny pomocí jediné metody a explicitně uzavřeny. Viz [streamování gRPC](rpc-types.md#grpc-streaming).

Další informace o zabezpečení a šifrování gRPC naleznete v části [Kapitola 6](security.md).

>[!div class="step-by-step"]
>[Předchozí](wcf-services-to-grpc-comparison.md)
>[Další](wcf-bindings.md)
