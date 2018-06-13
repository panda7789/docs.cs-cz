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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f92667191cad163998d233e1110365de65c0340c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437687"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="8c49f-102">IGCHost2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="8c49f-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="8c49f-103">Nastaví velikost segmentu a maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="8c49f-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c49f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c49f-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c49f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c49f-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="8c49f-106">[v] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="8c49f-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="8c49f-107">[v] Maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="8c49f-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c49f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c49f-108">Remarks</span></span>  
 <span data-ttu-id="8c49f-109">Hodnoty, `SetGCStartupLimitsEx` sady lze zadat pouze, před zahájením hostitele.</span><span class="sxs-lookup"><span data-stu-id="8c49f-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="8c49f-110">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="8c49f-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c49f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c49f-111">Requirements</span></span>  
 <span data-ttu-id="8c49f-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c49f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c49f-113">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="8c49f-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8c49f-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c49f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c49f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c49f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c49f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c49f-116">See Also</span></span>  
 [<span data-ttu-id="8c49f-117">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c49f-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
