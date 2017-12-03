---
title: "Prostředky operačního systému požadované službou WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31006331f5e8a71bf3f4fb9a68c31cb32d0b6f2b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="ad0f3-102">Prostředky operačního systému požadované službou WCF</span><span class="sxs-lookup"><span data-stu-id="ad0f3-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="ad0f3-103">závisí na několika prostředky, které jsou k dispozici v operačním systému funkce.</span><span class="sxs-lookup"><span data-stu-id="ad0f3-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="ad0f3-104">Následující tabulka uvádí tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="ad0f3-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="ad0f3-105">Prostředek</span><span class="sxs-lookup"><span data-stu-id="ad0f3-105">Resource</span></span>|<span data-ttu-id="ad0f3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ad0f3-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ad0f3-107">Microsoft Distributed Transaction Coordinator služba MSDTC)</span><span class="sxs-lookup"><span data-stu-id="ad0f3-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="ad0f3-108">Vyžadovaný jako podpora OleTx transakce.</span><span class="sxs-lookup"><span data-stu-id="ad0f3-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="ad0f3-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="ad0f3-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="ad0f3-110">Vyžaduje, pokud chcete službu IIS použít k hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad0f3-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="ad0f3-111">Aktivační služba procesů systému Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="ad0f3-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="ad0f3-112">Vyžaduje, pokud chcete použít WAS kvůli hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ad0f3-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad0f3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad0f3-113">See Also</span></span>  
 [<span data-ttu-id="ad0f3-114">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="ad0f3-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
