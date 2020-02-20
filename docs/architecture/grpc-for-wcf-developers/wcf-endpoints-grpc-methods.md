---
title: Koncové body WCF a metody gRPC – gRPC pro vývojáře WCF
description: Porovnání koncových bodů WCF deklarované s atributy třídy ServiceContract a OperationContract a metody gRPC deklarované v Protobuf
ms.date: 09/02/2019
ms.openlocfilehash: 1bc6ecbc73bfc0a58393e4c28672b897ed6f2f15
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503421"
---
# <a name="wcf-endpoints-and-grpc-methods"></a><span data-ttu-id="07139-103">Koncové body WCF a metody gRPC</span><span class="sxs-lookup"><span data-stu-id="07139-103">WCF endpoints and gRPC methods</span></span>

<span data-ttu-id="07139-104">Při psaní kódu aplikace v Windows Communication Foundation (WCF) použijte jednu z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="07139-104">In Windows Communication Foundation (WCF), when you're writing your application code, you use one of the following methods:</span></span>

- <span data-ttu-id="07139-105">Kód aplikace píšete ve třídě a metody lze pomocí atributu [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="07139-105">You write the application code in a class and decorate methods with the [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute.</span></span>
- <span data-ttu-id="07139-106">Deklarujete rozhraní pro službu a přidáte do rozhraní atributy [OperationContract](xref:System.ServiceModel.OperationContractAttribute) .</span><span class="sxs-lookup"><span data-stu-id="07139-106">You declare an interface for the service and add [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attributes to the interface.</span></span>

<span data-ttu-id="07139-107">Například ekvivalent služby `greet.proto`ového pozdravu WCF je možné zapsat takto:</span><span class="sxs-lookup"><span data-stu-id="07139-107">For example, the WCF equivalent of the `greet.proto` Greeter service might be written as follows:</span></span>

```csharp
[ServiceContract]
public interface IGreeterService
{
    [OperationContract]
    string SayHello(string name);
}
```

<span data-ttu-id="07139-108">Kapitola 3 ukázala, že definice zpráv Protobuf slouží ke generování datových tříd.</span><span class="sxs-lookup"><span data-stu-id="07139-108">Chapter 3 showed that Protobuf message definitions are used to generate data classes.</span></span> <span data-ttu-id="07139-109">Deklarace služby a metody se používají ke generování základních tříd, ze kterých dědíte pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="07139-109">Service and method declarations are used to generate base classes that you inherit from to implement the service.</span></span> <span data-ttu-id="07139-110">Pouze deklarujete metody, které mají být implementovány v souboru `.proto` a kompilátor vygeneruje základní třídu s virtuálními metodami, které je nutné přepsat.</span><span class="sxs-lookup"><span data-stu-id="07139-110">You just declare the methods to be implemented in the `.proto` file, and the compiler generates a base class with virtual methods that you must override.</span></span>

## <a name="operationcontract-properties"></a><span data-ttu-id="07139-111">Vlastnosti OperationContract</span><span class="sxs-lookup"><span data-stu-id="07139-111">OperationContract properties</span></span>

<span data-ttu-id="07139-112">Atribut [OperationContract](xref:System.ServiceModel.OperationContractAttribute) má vlastnosti pro kontrolu a vylepšení způsobu, jakým funguje.</span><span class="sxs-lookup"><span data-stu-id="07139-112">The [OperationContract](xref:System.ServiceModel.OperationContractAttribute) attribute has properties to control or refine how it works.</span></span> <span data-ttu-id="07139-113">metody gRPC nenabízejí tento typ ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="07139-113">gRPC methods don't offer this type of control.</span></span> <span data-ttu-id="07139-114">Následující tabulka uvádí tyto vlastnosti `OperationContract` a popisuje, jak funkce, které určí, jsou (nebo nejsou) řešeny v gRPC:</span><span class="sxs-lookup"><span data-stu-id="07139-114">The following table lists those `OperationContract` properties and describes how the functionality that they specify is (or isn't) dealt with in gRPC:</span></span>

| <span data-ttu-id="07139-115">`OperationContract` – vlastnost</span><span class="sxs-lookup"><span data-stu-id="07139-115">`OperationContract` property</span></span> | <span data-ttu-id="07139-116">gRPC</span><span class="sxs-lookup"><span data-stu-id="07139-116">gRPC</span></span>                                             |
| ---------------------------- | ------------------------------------------------ |
| <xref:System.ServiceModel.OperationContractAttribute.Action>             | <span data-ttu-id="07139-117">Identifikátor URI identifikuje operaci.</span><span class="sxs-lookup"><span data-stu-id="07139-117">A URI identifies the operation.</span></span> <span data-ttu-id="07139-118">gRPC používá název `package`, `service`a `rpc` ze souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="07139-118">gRPC uses the name of `package`, `service`, and `rpc` from the `.proto` file.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern>       | <span data-ttu-id="07139-119">Všechny metody služby gRPC vrací `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="07139-119">All gRPC service methods return `Task` objects.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsInitiating>       | <span data-ttu-id="07139-120">Podívejte se na odstavec za touto tabulkou.</span><span class="sxs-lookup"><span data-stu-id="07139-120">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsOneWay>           | <span data-ttu-id="07139-121">Jednosměrné metody gRPC vrací `Empty` výsledky nebo používají streamování klientů.</span><span class="sxs-lookup"><span data-stu-id="07139-121">One-way gRPC methods return `Empty` results or use client streaming.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.IsTerminating>      | <span data-ttu-id="07139-122">Podívejte se na odstavec za touto tabulkou.</span><span class="sxs-lookup"><span data-stu-id="07139-122">See the paragraph after this table.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.Name>               | <span data-ttu-id="07139-123">Tato vlastnost se vztahuje na SOAP a v gRPC nemá žádný význam.</span><span class="sxs-lookup"><span data-stu-id="07139-123">This property is SOAP related and has no meaning in gRPC.</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel>    | <span data-ttu-id="07139-124">Neexistují žádné šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="07139-124">There's no message encryption.</span></span> <span data-ttu-id="07139-125">Šifrování sítě se zpracovává na transportní vrstvě (TLS přes HTTP/2).</span><span class="sxs-lookup"><span data-stu-id="07139-125">Network encryption is handled at the transport layer (TLS over HTTP/2).</span></span> |
| <xref:System.ServiceModel.OperationContractAttribute.ReplyAction>        | <span data-ttu-id="07139-126">Tato vlastnost se vztahuje na SOAP a v gRPC nemá žádný význam.</span><span class="sxs-lookup"><span data-stu-id="07139-126">This property is SOAP related and has no meaning in gRPC.</span></span> |

<span data-ttu-id="07139-127">Vlastnost `IsInitiating` umožňuje označit, že metoda v rámci [třídy ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) nemůže být první metodou volanou jako součást relace.</span><span class="sxs-lookup"><span data-stu-id="07139-127">The `IsInitiating` property lets you indicate that a method within [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) can't be the first method called as part of a session.</span></span> <span data-ttu-id="07139-128">Vlastnost `IsTerminating` způsobí, že server ukončí relaci po volání operace (nebo klienta, pokud je vlastnost použita na klientovi zpětného volání).</span><span class="sxs-lookup"><span data-stu-id="07139-128">The `IsTerminating` property causes the server to close the session after an operation is called (or the client, if the property is used on a callback client).</span></span> <span data-ttu-id="07139-129">V gRPC jsou datové proudy vytvářeny pomocí jediné metody a explicitně uzavřeny.</span><span class="sxs-lookup"><span data-stu-id="07139-129">In gRPC, streams are created by single methods and closed explicitly.</span></span> <span data-ttu-id="07139-130">Viz [streamování gRPC](rpc-types.md#grpc-streaming).</span><span class="sxs-lookup"><span data-stu-id="07139-130">See [gRPC streaming](rpc-types.md#grpc-streaming).</span></span>

<span data-ttu-id="07139-131">Další informace o zabezpečení a šifrování gRPC naleznete v části [Kapitola 6](security.md).</span><span class="sxs-lookup"><span data-stu-id="07139-131">For more information on gRPC security and encryption, see [chapter 6](security.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="07139-132">[Předchozí](wcf-services-to-grpc-comparison.md)
>[Další](wcf-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="07139-132">[Previous](wcf-services-to-grpc-comparison.md)
[Next](wcf-bindings.md)</span></span>
