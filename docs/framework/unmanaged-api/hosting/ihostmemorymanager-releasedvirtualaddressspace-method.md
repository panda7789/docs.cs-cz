---
title: "IHostMemoryManager::ReleasedVirtualAddressSpace – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.ReleasedVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6db2868405aadb5879241e12128c6db40c0a5c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="d4633-102">IHostMemoryManager::ReleasedVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="d4633-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="d4633-103">Modul CLR (CLR) má dokončení pomocí zadaná paměťová upozorní hostitele.</span><span class="sxs-lookup"><span data-stu-id="d4633-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4633-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4633-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4633-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4633-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="d4633-106">[v] Ukazatel na počáteční adresa paměti k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="d4633-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4633-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4633-107">Remarks</span></span>  
 <span data-ttu-id="d4633-108">`ReleasedVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d4633-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="d4633-109">Je volána metodou modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="d4633-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4633-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4633-110">Requirements</span></span>  
 <span data-ttu-id="d4633-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4633-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4633-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4633-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4633-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4633-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4633-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4633-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4633-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4633-115">See Also</span></span>  
 [<span data-ttu-id="d4633-116">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4633-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
