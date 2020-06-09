---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 4b016f53a75d9527a5cd1bbadacacd650b7f35b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601898"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="3de3b-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="3de3b-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>
<span data-ttu-id="3de3b-103">Služba MSMQ vynechala zprávu.</span><span class="sxs-lookup"><span data-stu-id="3de3b-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3de3b-104">Popis</span><span class="sxs-lookup"><span data-stu-id="3de3b-104">Description</span></span>  
 <span data-ttu-id="3de3b-105">Trasování indikuje, že zpráva MSMQ byla vyřazena.</span><span class="sxs-lookup"><span data-stu-id="3de3b-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="3de3b-106">Zprávy služby MSMQ je možné vyřadit, pokud Windows Communication Foundation (WCF) (používá se s NetMsmqBinding nebo MsmqIntegrationBinding) není schopen je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="3de3b-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="3de3b-107">Tyto zprávy se označují jako nepoškozené zprávy.</span><span class="sxs-lookup"><span data-stu-id="3de3b-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="3de3b-108">Pokud `ReceiveErrorHandling` je vlastnost na NetMsmqBinding nebo MsmqIntegrationBinding nastavena na hodnotu, je zahozena nezpracovatelná zpráva `Drop` .</span><span class="sxs-lookup"><span data-stu-id="3de3b-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="3de3b-109">Vyřazená zpráva se odebere z fronty a už není obnovitelná.</span><span class="sxs-lookup"><span data-stu-id="3de3b-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="3de3b-110">Další informace o tom, kdy se zprávy stanou neslušně a jak nakonfigurovat službu tak, aby byla správně zpracována, naleznete v tématu [manipulace s poškozením](../../feature-details/poison-message-handling.md).</span><span class="sxs-lookup"><span data-stu-id="3de3b-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de3b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="3de3b-111">See also</span></span>

- [<span data-ttu-id="3de3b-112">Trasování</span><span class="sxs-lookup"><span data-stu-id="3de3b-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="3de3b-113">Řešení potíží s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="3de3b-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3de3b-114">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="3de3b-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="3de3b-115">Zpracování nezpracovatelných zpráv</span><span class="sxs-lookup"><span data-stu-id="3de3b-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
