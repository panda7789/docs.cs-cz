---
title: IHostMemoryManager::ReleasedVirtualAddressSpace – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0acbf4163e98b1171510260c4fac72c3d6f6fb1d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189284"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="5634a-102">IHostMemoryManager::ReleasedVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="5634a-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="5634a-103">Upozorňuje hostitele, že modul CLR (CLR) byla dokončena, pomocí zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="5634a-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5634a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5634a-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5634a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5634a-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="5634a-106">[in] Ukazatel na počáteční adresu paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="5634a-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5634a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5634a-107">Remarks</span></span>  
 <span data-ttu-id="5634a-108">`ReleasedVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5634a-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="5634a-109">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="5634a-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5634a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5634a-110">Requirements</span></span>  
 <span data-ttu-id="5634a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5634a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5634a-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5634a-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5634a-113">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5634a-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5634a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5634a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5634a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5634a-115">See also</span></span>

- [<span data-ttu-id="5634a-116">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5634a-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
