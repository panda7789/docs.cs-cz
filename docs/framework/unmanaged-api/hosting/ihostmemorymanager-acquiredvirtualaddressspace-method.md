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
ms.openlocfilehash: 4675c34bfe8d1d79c184c43e5f7f5dd3a03be6a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935652"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="c746b-102">IHostMemoryManager::AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="c746b-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="c746b-103">Upozorňuje hostitele, že modul CLR (CLR) získal zadaná paměťová z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="c746b-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c746b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c746b-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c746b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c746b-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="c746b-106">[in] Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="c746b-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="c746b-107">[in] Velikost v bajtech paměti.</span><span class="sxs-lookup"><span data-stu-id="c746b-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c746b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c746b-108">Remarks</span></span>  
 <span data-ttu-id="c746b-109">`AcquiredVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementováno tvůrci hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="c746b-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="c746b-110">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="c746b-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c746b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c746b-111">Requirements</span></span>  
 <span data-ttu-id="c746b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c746b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c746b-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c746b-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c746b-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c746b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c746b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c746b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c746b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c746b-116">See also</span></span>

- [<span data-ttu-id="c746b-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c746b-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
