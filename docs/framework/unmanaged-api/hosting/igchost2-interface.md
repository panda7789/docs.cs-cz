---
title: IGCHost2 – rozhraní
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805180"
---
# <a name="igchost2-interface"></a><span data-ttu-id="17620-102">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="17620-102">IGCHost2 Interface</span></span>
<span data-ttu-id="17620-103">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="17620-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17620-104">Pro nové vývojové prostředí doporučujeme místo toho použít rozhraní [ICLRGCManager2 –](iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="17620-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17620-105">Metody</span><span class="sxs-lookup"><span data-stu-id="17620-105">Methods</span></span>  
  
|<span data-ttu-id="17620-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="17620-106">Method</span></span>|<span data-ttu-id="17620-107">Popis</span><span class="sxs-lookup"><span data-stu-id="17620-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17620-108">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="17620-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="17620-109">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="17620-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="17620-110">Povoluje generaci 0 a velikosti segmentů větší než `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="17620-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17620-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17620-111">Requirements</span></span>  
 <span data-ttu-id="17620-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17620-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17620-113">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="17620-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="17620-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="17620-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17620-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17620-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17620-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="17620-116">See also</span></span>

- [<span data-ttu-id="17620-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="17620-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="17620-118">Rozhraní hostování CLR</span><span class="sxs-lookup"><span data-stu-id="17620-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="17620-119">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="17620-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
