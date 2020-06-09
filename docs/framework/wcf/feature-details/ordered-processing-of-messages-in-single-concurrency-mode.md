---
title: Uspořádané zpracování zpráv v režimu jedné souběžnosti
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: baba75fe398d974f989acfda7ef7366986f6813b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598733"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="66116-102">Uspořádané zpracování zpráv v režimu jedné souběžnosti</span><span class="sxs-lookup"><span data-stu-id="66116-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="66116-103">WCF neposkytuje žádné záruky týkající se pořadí, ve kterém jsou zprávy zpracovávány, pokud se nejedná o relace příslušného podkladového kanálu.</span><span class="sxs-lookup"><span data-stu-id="66116-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="66116-104">Například služba WCF, která používá MsmqInputChannel, která není kanálem relace, nebude schopna zpracovat zprávy v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="66116-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="66116-105">V některých případech se může stát, že vývojář bude chtít v pořadí zpracování, ale nechce používat relace.</span><span class="sxs-lookup"><span data-stu-id="66116-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="66116-106">Toto téma popisuje, jak toto chování nakonfigurovat, když je služba spuštěna v režimu jedné souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="66116-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="66116-107">Zpracování zpráv v pořadí</span><span class="sxs-lookup"><span data-stu-id="66116-107">In-order Message Processing</span></span>  
 <span data-ttu-id="66116-108">Do rozhraní byl přidán nový atribut s názvem <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="66116-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="66116-109">Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastavená hodnota true a <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavená na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odesílané službě, budou zpracovány v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="66116-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="66116-110">Následující fragment kódu ukazuje, jak tyto atributy nastavit.</span><span class="sxs-lookup"><span data-stu-id="66116-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="66116-111">Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je hodnota nastavena na jinou hodnotu, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="66116-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66116-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="66116-112">See also</span></span>

- [<span data-ttu-id="66116-113">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="66116-113">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="66116-114">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="66116-114">Concurrency</span></span>](../samples/concurrency.md)
