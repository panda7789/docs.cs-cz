---
title: IHostMemoryManager::AcquiredVirtualAddressSpace – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 423fbfc2bda9d3544a5c32b6cd650643209f0e86
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767239"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="7e851-102">IHostMemoryManager::AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="7e851-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="7e851-103">Upozorňuje hostitele, že modul CLR (CLR) získal zadaná paměťová z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="7e851-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e851-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e851-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e851-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e851-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="7e851-106">[in] Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="7e851-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="7e851-107">[in] Velikost v bajtech paměti.</span><span class="sxs-lookup"><span data-stu-id="7e851-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e851-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e851-108">Remarks</span></span>  
 <span data-ttu-id="7e851-109">`AcquiredVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="7e851-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="7e851-110">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="7e851-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e851-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e851-111">Requirements</span></span>  
 <span data-ttu-id="7e851-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e851-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e851-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e851-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e851-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e851-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e851-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e851-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e851-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e851-116">See also</span></span>

- [<span data-ttu-id="7e851-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e851-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
