---
title: Prostředky operačního systému požadované službou WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: ac9bd5ed7c2092720c6521d0f78185c3fbf9f94b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318945"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="d32b9-102">Prostředky operačního systému požadované službou WCF</span><span class="sxs-lookup"><span data-stu-id="d32b9-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="d32b9-103">Windows Communication Foundation (WCF) závisí na několika prostředcích, které poskytuje operační systém k fungování.</span><span class="sxs-lookup"><span data-stu-id="d32b9-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="d32b9-104">Následující tabulka uvádí tyto prostředky.</span><span class="sxs-lookup"><span data-stu-id="d32b9-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="d32b9-105">Partner</span><span class="sxs-lookup"><span data-stu-id="d32b9-105">Resource</span></span>|<span data-ttu-id="d32b9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d32b9-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="d32b9-107">Microsoft DTC (Distributed Transaction Coordinator) (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="d32b9-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="d32b9-108">Vyžaduje se pro podporu transakcí OleTx.</span><span class="sxs-lookup"><span data-stu-id="d32b9-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="d32b9-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="d32b9-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="d32b9-110">Povinné, pokud chcete použít službu IIS k hostování aplikace.</span><span class="sxs-lookup"><span data-stu-id="d32b9-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="d32b9-111">Aktivační služba procesů systému Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="d32b9-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="d32b9-112">Vyžadováno, pokud chcete použít k hostování aplikace.</span><span class="sxs-lookup"><span data-stu-id="d32b9-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d32b9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d32b9-113">See also</span></span>

- [<span data-ttu-id="d32b9-114">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="d32b9-114">System Requirements</span></span>](wcf-system-requirements.md)
