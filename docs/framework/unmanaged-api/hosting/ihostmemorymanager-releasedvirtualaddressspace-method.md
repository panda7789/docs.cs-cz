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
ms.openlocfilehash: 46082ddcee0163d5e61b3e468eb32c71e9f242ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128629"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="41453-102">IHostMemoryManager::ReleasedVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="41453-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="41453-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) dokončil používání zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="41453-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41453-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41453-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41453-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41453-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="41453-106">pro Ukazatel na počáteční adresu paměti, která se má uvolnit.</span><span class="sxs-lookup"><span data-stu-id="41453-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41453-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41453-107">Remarks</span></span>  
 <span data-ttu-id="41453-108">Metoda `ReleasedVirtualAddressSpace` je metoda zpětného volání a musí být implementována zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="41453-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="41453-109">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="41453-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41453-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41453-110">Requirements</span></span>  
 <span data-ttu-id="41453-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41453-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41453-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="41453-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41453-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="41453-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41453-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41453-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41453-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41453-115">See also</span></span>

- [<span data-ttu-id="41453-116">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41453-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
