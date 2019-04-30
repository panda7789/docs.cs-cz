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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934846"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="c2933-102">IHostMemoryManager::ReleasedVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="c2933-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="c2933-103">Upozorňuje hostitele, že modul CLR (CLR) byla dokončena, pomocí zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="c2933-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2933-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2933-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2933-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2933-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="c2933-106">[in] Ukazatel na počáteční adresu paměť uvolnit.</span><span class="sxs-lookup"><span data-stu-id="c2933-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2933-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2933-107">Remarks</span></span>  
 <span data-ttu-id="c2933-108">`ReleasedVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2933-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="c2933-109">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="c2933-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2933-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2933-110">Requirements</span></span>  
 <span data-ttu-id="c2933-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2933-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2933-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2933-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2933-113">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2933-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2933-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2933-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2933-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2933-115">See also</span></span>

- [<span data-ttu-id="c2933-116">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2933-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
