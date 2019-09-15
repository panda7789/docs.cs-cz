---
title: Uspořádané zpracování zpráv v režimu jedné souběžnosti
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: ecabb9a6e838b0137c538d76c554646356ea87f5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991505"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="7b089-102">Uspořádané zpracování zpráv v režimu jedné souběžnosti</span><span class="sxs-lookup"><span data-stu-id="7b089-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="7b089-103">WCF neposkytuje žádné záruky týkající se pořadí, ve kterém jsou zprávy zpracovávány, pokud se nejedná o relace příslušného podkladového kanálu.</span><span class="sxs-lookup"><span data-stu-id="7b089-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="7b089-104">Například služba WCF, která používá MsmqInputChannel, která není kanálem relace, nebude schopna zpracovat zprávy v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7b089-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="7b089-105">V některých případech se může stát, že vývojář bude chtít v pořadí zpracování, ale nechce používat relace.</span><span class="sxs-lookup"><span data-stu-id="7b089-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="7b089-106">Toto téma popisuje, jak toto chování nakonfigurovat, když je služba spuštěna v režimu jedné souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="7b089-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="7b089-107">Zpracování zpráv v pořadí</span><span class="sxs-lookup"><span data-stu-id="7b089-107">In-order Message Processing</span></span>  
 <span data-ttu-id="7b089-108">Do rozhraní <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute>byl přidán nový atribut s názvem.</span><span class="sxs-lookup"><span data-stu-id="7b089-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="7b089-109">Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastavená hodnota true <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a je nastavená na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odesílané službě, budou zpracovány v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7b089-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="7b089-110">Následující fragment kódu ukazuje, jak tyto atributy nastavit.</span><span class="sxs-lookup"><span data-stu-id="7b089-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="7b089-111">Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je hodnota nastavena na jinou hodnotu <xref:System.InvalidOperationException> , je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7b089-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b089-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b089-112">See also</span></span>

- [<span data-ttu-id="7b089-113">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="7b089-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="7b089-114">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="7b089-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
