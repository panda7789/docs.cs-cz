---
title: "Uspořádané zpracování zpráv v režimu jedné souběžnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c50381c678a84f5602d08342d02dbf44316994c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="daf45-102">Uspořádané zpracování zpráv v režimu jedné souběžnosti</span><span class="sxs-lookup"><span data-stu-id="daf45-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="daf45-103">WCF umožňuje žádné záruky o pořadí, ve kterém jsou zpracovány zprávy, není-li základní kanál relacemi.</span><span class="sxs-lookup"><span data-stu-id="daf45-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="daf45-104">Pro instanci služby WCF, který používá MsmqInputChannel, která není kanál s relacemi, se nezdaří zpracování zpráv v pořadí.</span><span class="sxs-lookup"><span data-stu-id="daf45-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="daf45-105">Existují některé okolnosti, kdy může vývojář má v pořadí zpracování chování ale použít relací.</span><span class="sxs-lookup"><span data-stu-id="daf45-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="daf45-106">Toto téma popisuje postupy pro konfiguraci tohoto chování, když služba běží v režimu jedné souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="daf45-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="daf45-107">Pořadí zpracování zpráv</span><span class="sxs-lookup"><span data-stu-id="daf45-107">In-order Message Processing</span></span>  
 <span data-ttu-id="daf45-108">Volá se nový atribut <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> byl přidán do <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="daf45-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="daf45-109">Když <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> je nastaven na hodnotu true a <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastaven na <xref:System.ServiceModel.ConcurrencyMode.Single> zprávy odeslané do služby budou zpracovány v pořadí.</span><span class="sxs-lookup"><span data-stu-id="daf45-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="daf45-110">Následující fragment kódu ukazuje, jak nastavit tyto atributy.</span><span class="sxs-lookup"><span data-stu-id="daf45-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="daf45-111">Pokud <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> nastavena na žádné jiné hodnoty, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="daf45-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf45-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="daf45-112">See Also</span></span>  
 [<span data-ttu-id="daf45-113">Relace, vytváření instancí a souběžnost</span><span class="sxs-lookup"><span data-stu-id="daf45-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="daf45-114">Souběžnost</span><span class="sxs-lookup"><span data-stu-id="daf45-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
