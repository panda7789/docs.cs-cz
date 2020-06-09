---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.date: 03/30/2017
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
ms.openlocfilehash: 8b81cdcaf74aca044260495867b2c4f1de517682
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593747"
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a><span data-ttu-id="02f48-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span><span class="sxs-lookup"><span data-stu-id="02f48-102">System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed</span></span>
<span data-ttu-id="02f48-103">Zprávu nelze přesunout nebo odstranit.</span><span class="sxs-lookup"><span data-stu-id="02f48-103">Cannot move or delete message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="02f48-104">Popis</span><span class="sxs-lookup"><span data-stu-id="02f48-104">Description</span></span>  
 <span data-ttu-id="02f48-105">Trasování indikuje, že došlo k chybě při pokusu o přesunutí, odstranění nebo odmítnutí zprávy služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="02f48-105">The trace indicates that a failure occurred when attempting to move, delete, or reject an MSMQ message.</span></span>  
  
 <span data-ttu-id="02f48-106">Zprávy služby MSMQ jsou zaměstnány pomocí Windows Communication Foundation (WCF) (při použití s rozhraním NetMsmqBinding nebo MsmqIntegrationBinding). Toto trasování se vztahuje k zvolené hodnotě `ReceiveErrorHandling` vlastnosti v NetMsmqBinding nebo MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="02f48-106">MSMQ messages are employed by Windows Communication Foundation (WCF) (when used with either the NetMsmqBinding or the MsmqIntegrationBinding).This trace is related to the chosen value of the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding.</span></span>  
  
 <span data-ttu-id="02f48-107">Toto trasování není indikativní pro celkové selhání systému.</span><span class="sxs-lookup"><span data-stu-id="02f48-107">This trace is not indicative of an overall system failure.</span></span> <span data-ttu-id="02f48-108">Označuje však, že u zprávy se nezdařilo dispozice zvolené nepoškozené zprávy.</span><span class="sxs-lookup"><span data-stu-id="02f48-108">However, it indicates that the chosen poison message disposition failed for a message.</span></span> <span data-ttu-id="02f48-109">Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="02f48-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f48-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="02f48-110">See also</span></span>

- [<span data-ttu-id="02f48-111">Trasování</span><span class="sxs-lookup"><span data-stu-id="02f48-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="02f48-112">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="02f48-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="02f48-113">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="02f48-113">Administration and Diagnostics</span></span>](../index.md)
