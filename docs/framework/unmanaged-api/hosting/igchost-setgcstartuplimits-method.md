---
title: "IGCHost::SetGCStartupLimits – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f95e5afa1297602e4ef12ed0dfb3f98aa5c762ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="a91b9-102">IGCHost::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="a91b9-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="a91b9-103">Nastaví velikost segmentu a maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="a91b9-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a91b9-104">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete nastavit velikost segmentu a hodnoty větší než maximální generace 0 velikost tak, aby `DWORD` pomocí [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a91b9-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a91b9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a91b9-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a91b9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a91b9-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="a91b9-107">[v] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="a91b9-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="a91b9-108">[v] Maximální velikost pro generování 0.</span><span class="sxs-lookup"><span data-stu-id="a91b9-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a91b9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a91b9-109">Remarks</span></span>  
 <span data-ttu-id="a91b9-110">`SetGCStartupLimits` Metoda může být volána pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a91b9-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="a91b9-111">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="a91b9-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a91b9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a91b9-112">Requirements</span></span>  
 <span data-ttu-id="a91b9-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a91b9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a91b9-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="a91b9-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a91b9-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a91b9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a91b9-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a91b9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91b9-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a91b9-117">See Also</span></span>  
 [<span data-ttu-id="a91b9-118">Igchost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a91b9-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
