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
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804515"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="51b73-102">IHostMemoryManager::NeedsVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="51b73-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="51b73-103">Upozorňuje hostitele, že se bude modul CLR (Common Language Runtime) pokoušet použít zadanou paměť.</span><span class="sxs-lookup"><span data-stu-id="51b73-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51b73-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51b73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51b73-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="51b73-106">pro Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="51b73-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="51b73-107">pro Velikost paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="51b73-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51b73-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51b73-108">Remarks</span></span>  
 <span data-ttu-id="51b73-109">`NeedsVirtualAddressSpace`Metoda je metoda zpětného volání a musí být implementována zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="51b73-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="51b73-110">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="51b73-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="51b73-111">Pokud hostitel nechce, aby CLR používal zadanou paměť, může vrátit E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="51b73-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b73-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51b73-112">Requirements</span></span>  
 <span data-ttu-id="51b73-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b73-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b73-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="51b73-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51b73-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51b73-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51b73-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b73-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b73-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="51b73-117">See also</span></span>

- [<span data-ttu-id="51b73-118">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="51b73-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
