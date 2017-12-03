---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a><span data-ttu-id="73120-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="73120-102">MSMQ</span></span>
<span data-ttu-id="73120-103">V aplikaci služby MSMQ žádná další aktivita se přenáší z tohoto kanálu zařazených do fronty pro služby MSMQ a ze služby MSMQ ve frontě kanálu.</span><span class="sxs-lookup"><span data-stu-id="73120-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="73120-104">Kromě toho jsou ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s ID aktivity, pokud existuje) jako součást trasování kanálu ve frontě na operaci odeslání trasovat.</span><span class="sxs-lookup"><span data-stu-id="73120-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="73120-105">ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s aktivity, které ID, pokud existuje) budou trasovány jako součást trasování kanálu ve frontě na operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="73120-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="73120-106">Požadované přenosy na operace příjmu jsou spuštěný podobně jako ostatní přenosu (přijímat bajtů -> procesu zpráva -> operaci).</span><span class="sxs-lookup"><span data-stu-id="73120-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
