---
title: "IHostMemoryManager::AcquiredVirtualAddressSpace – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.AcquiredVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af80a43b86b1a16c5afe2741cb3d2bd7f0d874ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="63a56-102">IHostMemoryManager::AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="63a56-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="63a56-103">Upozorní hostitele, modul CLR (CLR) má získat zadaná paměťová z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="63a56-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63a56-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63a56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63a56-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="63a56-106">[v] Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="63a56-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="63a56-107">[v] Velikost v bajtech paměti.</span><span class="sxs-lookup"><span data-stu-id="63a56-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63a56-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63a56-108">Remarks</span></span>  
 <span data-ttu-id="63a56-109">`AcquiredVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63a56-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="63a56-110">Je volána metodou modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="63a56-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63a56-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63a56-111">Requirements</span></span>  
 <span data-ttu-id="63a56-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63a56-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63a56-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63a56-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63a56-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63a56-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63a56-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63a56-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a56-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="63a56-116">See Also</span></span>  
 [<span data-ttu-id="63a56-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63a56-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
