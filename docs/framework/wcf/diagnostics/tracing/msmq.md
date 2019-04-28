---
title: MSMQ
ms.date: 03/30/2017
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
ms.openlocfilehash: 5e157da25829a0741de988d1d6dde0318a93b109
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663723"
---
# <a name="msmq"></a><span data-ttu-id="ef186-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="ef186-102">MSMQ</span></span>
<span data-ttu-id="ef186-103">V aplikaci služby MSMQ se přenesou žádná další aktivita v kanálu ve frontě MSMQ a ze služby MSMQ pro kanálu ve frontě.</span><span class="sxs-lookup"><span data-stu-id="ef186-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="ef186-104">Kromě toho ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s ID aktivity, pokud existuje) jsou trasovány jako součást kanálu ve frontě trasování na operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="ef186-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="ef186-105">ID zprávy služby MSMQ a ID zprávy protokolu SOAP (spolu s aktivity, které ID, pokud existuje) jsou trasovány jako součást kanálu ve frontě trasování na operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="ef186-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="ef186-106">Požadované přenosy na operace obdržení provádějí podobně jako ostatní přenosu (přijímání bajtů -> zpracovat zprávu -> operace).</span><span class="sxs-lookup"><span data-stu-id="ef186-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
