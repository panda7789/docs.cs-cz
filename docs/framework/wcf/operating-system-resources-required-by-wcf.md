---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100934"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="6bd25-102">Prostředky operačního systému požadované službou WCF</span><span class="sxs-lookup"><span data-stu-id="6bd25-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="6bd25-103">Windows Communication Foundation (WCF) závisí na několika prostředcích, které jsou k dispozici v operačním systému na funkci.</span><span class="sxs-lookup"><span data-stu-id="6bd25-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="6bd25-104">V následující tabulce jsou uvedeny tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="6bd25-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="6bd25-105">Prostředek</span><span class="sxs-lookup"><span data-stu-id="6bd25-105">Resource</span></span>|<span data-ttu-id="6bd25-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6bd25-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6bd25-107">Microsoft distribuované transakce koordinátor (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="6bd25-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="6bd25-108">Vyžadovaný jako podpora OleTx transakce.</span><span class="sxs-lookup"><span data-stu-id="6bd25-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="6bd25-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="6bd25-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="6bd25-110">Povinné, pokud chcete použít k hostování vaší aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6bd25-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="6bd25-111">Aktivační služba procesů Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="6bd25-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="6bd25-112">Povinné, pokud chcete používat WAS k hostování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6bd25-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bd25-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bd25-113">See also</span></span>

- [<span data-ttu-id="6bd25-114">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="6bd25-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
