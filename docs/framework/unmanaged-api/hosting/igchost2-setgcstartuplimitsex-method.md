---
title: IGCHost2::SetGCStartupLimitsEx – metoda
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: ca9566168b8aae361af8d61539066624697a2d04
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805146"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="aea7b-102">IGCHost2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="aea7b-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="aea7b-103">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="aea7b-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aea7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aea7b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aea7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aea7b-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="aea7b-106">pro Velikost segmentu používaného systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="aea7b-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="aea7b-107">pro Maximální velikost pro generaci 0</span><span class="sxs-lookup"><span data-stu-id="aea7b-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aea7b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aea7b-108">Remarks</span></span>  
 <span data-ttu-id="aea7b-109">Hodnoty, které `SetGCStartupLimitsEx` nastavíte, lze zadat pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="aea7b-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="aea7b-110">Tyto hodnoty nelze později změnit.</span><span class="sxs-lookup"><span data-stu-id="aea7b-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aea7b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aea7b-111">Requirements</span></span>  
 <span data-ttu-id="aea7b-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aea7b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aea7b-113">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="aea7b-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="aea7b-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aea7b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aea7b-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aea7b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aea7b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="aea7b-116">See also</span></span>

- [<span data-ttu-id="aea7b-117">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aea7b-117">IGCHost2 Interface</span></span>](igchost2-interface.md)
