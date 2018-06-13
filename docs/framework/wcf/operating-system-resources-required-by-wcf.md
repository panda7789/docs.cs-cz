---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498641"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="a916c-102">Prostředky operačního systému požadované službou WCF</span><span class="sxs-lookup"><span data-stu-id="a916c-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="a916c-103">Windows Communication Foundation (WCF) závisí na několika prostředky, které jsou k dispozici v operačním systému funkce.</span><span class="sxs-lookup"><span data-stu-id="a916c-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="a916c-104">Následující tabulka uvádí tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="a916c-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="a916c-105">Prostředek</span><span class="sxs-lookup"><span data-stu-id="a916c-105">Resource</span></span>|<span data-ttu-id="a916c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a916c-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="a916c-107">Microsoft Distributed Transaction Coordinator služba MSDTC)</span><span class="sxs-lookup"><span data-stu-id="a916c-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="a916c-108">Vyžadovaný jako podpora OleTx transakce.</span><span class="sxs-lookup"><span data-stu-id="a916c-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="a916c-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="a916c-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="a916c-110">Vyžaduje, pokud chcete službu IIS použít k hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a916c-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="a916c-111">Aktivační služba procesů systému Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="a916c-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="a916c-112">Vyžaduje, pokud chcete použít WAS kvůli hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="a916c-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a916c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a916c-113">See Also</span></span>  
 [<span data-ttu-id="a916c-114">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="a916c-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
