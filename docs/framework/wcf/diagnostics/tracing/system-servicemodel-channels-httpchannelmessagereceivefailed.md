---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46bc39237f0a6f0b9b25b9616782ec3e97fa22ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="ce799-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="ce799-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>
<span data-ttu-id="ce799-103">Nepodařilo se přijmout zprávu přes kanál protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce799-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ce799-104">Popis</span><span class="sxs-lookup"><span data-stu-id="ce799-104">Description</span></span>  
 <span data-ttu-id="ce799-105">Trasování může být poslán jako upozornění nebo chybu.</span><span class="sxs-lookup"><span data-stu-id="ce799-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="ce799-106">V obou případech jsou vydávány trasování, pokud pro příchozí požadavek HTTP se nenašel kompatibilní naslouchací proces a požadavek HTTP se zahodí.</span><span class="sxs-lookup"><span data-stu-id="ce799-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="ce799-107">Toto může nastat, protože příkaz HTTP žádosti nebyla rozpoznána ve všech naslouchací proces protokolu HTTP, nebo protože byla žádné naslouchací proces naslouchání na adrese žádosti je určený pro.</span><span class="sxs-lookup"><span data-stu-id="ce799-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="ce799-108">Trasování jsou vydávány jako upozornění v případě, že vlastním hostováním a jako chybu, pokud služba je hostovaná ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="ce799-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce799-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce799-109">See Also</span></span>  
 [<span data-ttu-id="ce799-110">Trasování</span><span class="sxs-lookup"><span data-stu-id="ce799-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="ce799-111">Řešení problémů s aplikací pomocí trasování</span><span class="sxs-lookup"><span data-stu-id="ce799-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="ce799-112">Správa a diagnostika</span><span class="sxs-lookup"><span data-stu-id="ce799-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
