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
ms.openlocfilehash: b70454cd1e2d6d38e6ca4d0ea0bd8974963c201c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136730"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="3031a-102">IHostMemoryManager::AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="3031a-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="3031a-103">Upozorňuje hostitele, že modul CLR (Common Language Runtime) získal zadanou paměť z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3031a-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3031a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3031a-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3031a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3031a-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="3031a-106">pro Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="3031a-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="3031a-107">pro Velikost paměti (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="3031a-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3031a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3031a-108">Remarks</span></span>  
 <span data-ttu-id="3031a-109">Metoda `AcquiredVirtualAddressSpace` je metoda zpětného volání a musí být implementována zapisovačí hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="3031a-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="3031a-110">Je volána modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="3031a-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3031a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3031a-111">Requirements</span></span>  
 <span data-ttu-id="3031a-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3031a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3031a-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3031a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3031a-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3031a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3031a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3031a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3031a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3031a-116">See also</span></span>

- [<span data-ttu-id="3031a-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3031a-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
