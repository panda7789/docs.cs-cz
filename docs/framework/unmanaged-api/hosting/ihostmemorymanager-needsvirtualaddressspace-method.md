---
title: IHostMemoryManager::NeedsVirtualAddressSpace – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0f029c8fbab97afe3089956391e8446d4cc5e15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215492"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="77a5f-102">IHostMemoryManager::NeedsVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="77a5f-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="77a5f-103">Upozorňuje hostitele, že bude pokus o použití zadaná paměťová common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="77a5f-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77a5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77a5f-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77a5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77a5f-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="77a5f-106">[in] Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="77a5f-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="77a5f-107">[in] Velikost v bajtech paměti.</span><span class="sxs-lookup"><span data-stu-id="77a5f-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77a5f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77a5f-108">Remarks</span></span>  
 <span data-ttu-id="77a5f-109">`NeedsVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="77a5f-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="77a5f-110">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="77a5f-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="77a5f-111">Pokud hostitel nechce CLR, která pomocí zadané paměti, může vrátit E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="77a5f-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77a5f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77a5f-112">Requirements</span></span>  
 <span data-ttu-id="77a5f-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77a5f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77a5f-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77a5f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77a5f-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77a5f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="77a5f-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="77a5f-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77a5f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77a5f-117">See also</span></span>

- [<span data-ttu-id="77a5f-118">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77a5f-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
