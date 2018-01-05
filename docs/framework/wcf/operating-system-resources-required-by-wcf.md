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
ms.workload: dotnet
ms.openlocfilehash: fde00011a7fffde4c4c75f9605758971b42627f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="bde8f-102">Prostředky operačního systému požadované službou WCF</span><span class="sxs-lookup"><span data-stu-id="bde8f-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="bde8f-103">závisí na několika prostředky, které jsou k dispozici v operačním systému funkce.</span><span class="sxs-lookup"><span data-stu-id="bde8f-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="bde8f-104">Následující tabulka uvádí tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="bde8f-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="bde8f-105">Prostředek</span><span class="sxs-lookup"><span data-stu-id="bde8f-105">Resource</span></span>|<span data-ttu-id="bde8f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bde8f-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="bde8f-107">Microsoft Distributed Transaction Coordinator služba MSDTC)</span><span class="sxs-lookup"><span data-stu-id="bde8f-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="bde8f-108">Vyžadovaný jako podpora OleTx transakce.</span><span class="sxs-lookup"><span data-stu-id="bde8f-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="bde8f-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="bde8f-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="bde8f-110">Vyžaduje, pokud chcete službu IIS použít k hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="bde8f-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="bde8f-111">Aktivační služba procesů systému Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="bde8f-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="bde8f-112">Vyžaduje, pokud chcete použít WAS kvůli hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="bde8f-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bde8f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bde8f-113">See Also</span></span>  
 [<span data-ttu-id="bde8f-114">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="bde8f-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
