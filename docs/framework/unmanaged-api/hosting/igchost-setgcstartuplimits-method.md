---
title: IGCHost::SetGCStartupLimits – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 3b0c11ac9d827bd252018172e2337df653054a7b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805204"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="d9698-102">IGCHost::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="d9698-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="d9698-103">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="d9698-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9698-104">Počínaje .NET Framework 4,5 můžete nastavit velikost segmentu a maximální velikost generace 0 na hodnoty větší než pomocí `DWORD` metody [IGCHost2 –:: SetGCStartupLimitsEx –](igchost2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9698-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9698-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9698-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9698-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9698-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="d9698-107">pro Velikost segmentu používaného systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d9698-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="d9698-108">pro Maximální velikost pro generaci 0</span><span class="sxs-lookup"><span data-stu-id="d9698-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9698-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9698-109">Remarks</span></span>  
 <span data-ttu-id="d9698-110">`SetGCStartupLimits`Metodu lze volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="d9698-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="d9698-111">Tyto hodnoty nelze později změnit.</span><span class="sxs-lookup"><span data-stu-id="d9698-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9698-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9698-112">Requirements</span></span>  
 <span data-ttu-id="d9698-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9698-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9698-114">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="d9698-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d9698-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d9698-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9698-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9698-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9698-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9698-117">See also</span></span>

- [<span data-ttu-id="d9698-118">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9698-118">IGCHost Interface</span></span>](igchost-interface.md)
