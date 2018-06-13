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
ms.openlocfilehash: 87c97a678fce4c25a113670a4668515a898e5251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438415"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="b73de-102">IHostMemoryManager::NeedsVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="b73de-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="b73de-103">Aby modul CLR (CLR) bude pokus o použití zadaná paměťová upozorní hostitele.</span><span class="sxs-lookup"><span data-stu-id="b73de-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b73de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b73de-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b73de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b73de-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="b73de-106">[v] Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="b73de-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="b73de-107">[v] Velikost v bajtech paměti.</span><span class="sxs-lookup"><span data-stu-id="b73de-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b73de-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b73de-108">Remarks</span></span>  
 <span data-ttu-id="b73de-109">`NeedsVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b73de-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b73de-110">Je volána metodou modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b73de-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="b73de-111">Pokud hostitel nechce CLR použití zadané paměti, může vrátit E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b73de-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b73de-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b73de-112">Requirements</span></span>  
 <span data-ttu-id="b73de-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b73de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b73de-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b73de-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b73de-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b73de-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b73de-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b73de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b73de-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b73de-117">See Also</span></span>  
 [<span data-ttu-id="b73de-118">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b73de-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
