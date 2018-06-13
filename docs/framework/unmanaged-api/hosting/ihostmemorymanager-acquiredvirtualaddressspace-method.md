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
ms.openlocfilehash: d93c50968192a7789cbf08968d7ec272c9775d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438510"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="817fd-102">IHostMemoryManager::AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="817fd-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="817fd-103">Upozorní hostitele, modul CLR (CLR) má získat zadaná paměťová z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="817fd-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="817fd-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="817fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="817fd-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="817fd-106">[v] Počáteční adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="817fd-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="817fd-107">[v] Velikost v bajtech paměti.</span><span class="sxs-lookup"><span data-stu-id="817fd-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="817fd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="817fd-108">Remarks</span></span>  
 <span data-ttu-id="817fd-109">`AcquiredVirtualAddressSpace` Metoda je metoda zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="817fd-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="817fd-110">Je volána metodou modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="817fd-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="817fd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="817fd-111">Requirements</span></span>  
 <span data-ttu-id="817fd-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="817fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817fd-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="817fd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="817fd-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="817fd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="817fd-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="817fd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="817fd-116">See Also</span></span>  
 [<span data-ttu-id="817fd-117">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="817fd-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
