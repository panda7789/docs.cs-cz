---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: f89dd1373d67714046f8cb958582c3a5dea04456
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674781"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="5f531-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="5f531-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="5f531-103">Zprávu nelze přesunout ani odstranit.</span><span class="sxs-lookup"><span data-stu-id="5f531-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5f531-104">Popis</span><span class="sxs-lookup"><span data-stu-id="5f531-104">Description</span></span>  
 <span data-ttu-id="5f531-105">Trasování označuje, že při pokusu o přesunutí, odstranění nebo odmítnutí zprávy služby MSMQ došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="5f531-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="5f531-106">Zprávy služby MSMQ jsou používány službou WCF (Při použití s netmsmqbinding nebo MsmqIntegrationBinding). Toto trasování souvisí s `ReceiveErrorHandling` vybranou hodnotu vlastnosti na NetMsmqBinding nebo MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="5f531-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="5f531-107">Toto trasování nesvědčí o celkové selhání systému.</span><span class="sxs-lookup"><span data-stu-id="5f531-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="5f531-108">Však označuje, že vybrané poškozená zpráva dispozice se nezdařilo pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="5f531-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="5f531-109">Další informace o tom, kdy se zprávy stanou jedovatými a jak nakonfigurovat službu tak, aby je správně zpracovávala, naleznete v [tématu Zpracování zpráv poison](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="5f531-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f531-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f531-110">See also</span></span>

- [<span data-ttu-id="5f531-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="5f531-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="5f531-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="5f531-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5f531-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="5f531-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
