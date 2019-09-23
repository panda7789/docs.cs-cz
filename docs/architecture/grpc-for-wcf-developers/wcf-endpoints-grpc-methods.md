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
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="0be7a-103">Koncové body WCF a metody gRPC</span><span class="sxs-lookup"><span data-stu-id="0be7a-103">WCF endpoints and gRPC methods</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0be7a-104">Při psaní kódu aplikace v technologii WCF použijte jednu z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="0be7a-104">In WCF, when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="0be7a-105">Kód aplikace píšete ve třídě a metody lze pomocí atributu [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0be7a-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="0be7a-106">Deklarujete rozhraní pro službu a přidáte do rozhraní atributy [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="0be7a-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="0be7a-107">Například ekvivalent služby typu `greet.proto` WCF na službu Greeter může být zapsán následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0be7a-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="0be7a-108">Kapitola 3 ukázala, že definice zpráv Protobuf slouží ke generování datových tříd.</span><span class="sxs-lookup"><span data-stu-id="0be7a-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="0be7a-109">Deklarace služby a metody se používají ke generování základních tříd, ze kterých dědíte pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="0be7a-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="0be7a-110">Pouze deklarujete metody, které mají být implementovány `.proto` v souboru, a kompilátor vygeneruje základní třídu s virtuálními metodami, které musíte přepsat.</span><span class="sxs-lookup"><span data-stu-id="0be7a-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="0be7a-111">Vlastnosti OperationContract</span><span class="sxs-lookup"><span data-stu-id="0be7a-111">OperationContract properties</span></span>

<span data-ttu-id="0be7a-112">Atribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) má vlastnosti pro kontrolu a vylepšení způsobu, jakým funguje.</span><span class="sxs-lookup"><span data-stu-id="0be7a-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="0be7a-113">metody gRPC nenabízejí tento typ ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0be7a-113">gRPC methods don’t offer this type of control.</span></span> <span data-ttu-id="0be7a-114">Následující tabulka uvádí tyto `OperationContract` vlastnosti a způsob, jakým jsou funkce, které určíte (nebo nejsou) řešeny v gRPC:</span><span class="sxs-lookup"><span data-stu-id="0be7a-114">The following table sets out those `OperationContract` properties and how the functionality they specify is (or isn’t) dealt with in gRPC:</span></span>

| <span data-ttu-id="0be7a-115">`OperationContract`majetek</span><span class="sxs-lookup"><span data-stu-id="0be7a-115">`OperationContract` property</span></span> | <span data-ttu-id="0be7a-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="0be7a-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="0be7a-117">Identifikátor URI, který identifikuje operaci</span><span class="sxs-lookup"><span data-stu-id="0be7a-117">URI identifying the operation.</span></span> <span data-ttu-id="0be7a-118">gRPC `package`používá název `service` a `rpc` ze souboru.`.proto`</span><span class="sxs-lookup"><span data-stu-id="0be7a-118">gRPC uses the name of the `package`, `service` and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="0be7a-119">Všechny metody služby gRPC vrací `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="0be7a-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="0be7a-120">Viz poznámka níže.</span><span class="sxs-lookup"><span data-stu-id="0be7a-120">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="0be7a-121">Jednosměrné metody gRPC vracejí `Empty` výsledky nebo používají streamování klientů.</span><span class="sxs-lookup"><span data-stu-id="0be7a-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="0be7a-122">Viz poznámka níže.</span><span class="sxs-lookup"><span data-stu-id="0be7a-122">See note below.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="0be7a-123">Související s protokolem SOAP, žádný význam v gRPC.</span><span class="sxs-lookup"><span data-stu-id="0be7a-123">SOAP-related, no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="0be7a-124">Žádné šifrování zpráv; šifrování sítě je zpracované v transportní vrstvě (TLS přes HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="0be7a-124">No message encryption; network encryption handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="0be7a-125">Související s protokolem SOAP, žádný význam v gRPC.</span><span class="sxs-lookup"><span data-stu-id="0be7a-125">SOAP-related, no meaning in gRPC.</span></span> |

<span data-ttu-id="0be7a-126">Vlastnost umožňuje označit, že metoda v rámci [třídy ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nemůže být první metodou volanou jako součást relace. `IsInitiating`</span><span class="sxs-lookup"><span data-stu-id="0be7a-126">The `IsInitiating` property lets you indicate that a method within a [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="0be7a-127">`IsTerminating` Vlastnost způsobí, že server ukončí relaci po volání operace (nebo klienta, pokud se používá u klienta zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="0be7a-127">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if used on a callback client).</span></span> <span data-ttu-id="0be7a-128">V gRPC jsou datové proudy vytvářeny pomocí jediné metody a explicitně uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="0be7a-128">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="0be7a-129">Viz [streamování gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="0be7a-129">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="0be7a-130">Další informace o zabezpečení a šifrování gRPC naleznete v části [Kapitola 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="0be7a-130">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0be7a-131">[Předchozí](wcf-services-to-grpc-comparison.md)
>[Další](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0be7a-131">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
