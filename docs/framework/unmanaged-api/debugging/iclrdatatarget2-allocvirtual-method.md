---
title: "ICLRDataTarget2::AllocVirtual – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d869b350217903dda209699f94897b70bc57132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="5d909-102">ICLRDataTarget2::AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="5d909-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="5d909-103">Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup přidělit paměť v adresním prostoru tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="5d909-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d909-104">Syntax</span></span>  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d909-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d909-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="5d909-106">[v] A `CLRDATA_ADDRESS` hodnotu, která určuje požadovanou počáteční adresa paměti, která bude přidělena.</span><span class="sxs-lookup"><span data-stu-id="5d909-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="5d909-107">[v] Velikost v bajtech, paměti, která bude přidělena.</span><span class="sxs-lookup"><span data-stu-id="5d909-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="5d909-108">[v] Příznaky, které řídí přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="5d909-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="5d909-109">V tématu Win32 `VirtualAlloc` funkce.</span><span class="sxs-lookup"><span data-stu-id="5d909-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="5d909-110">[v] Atributy ochrany přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="5d909-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="5d909-111">V tématu Win32 `VirtualAlloc` funkce.</span><span class="sxs-lookup"><span data-stu-id="5d909-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="5d909-112">[out] Ukazatel na `CLRDATA_ADDRESS` hodnotu, která určuje skutečné počáteční adresa přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="5d909-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d909-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d909-113">Remarks</span></span>  
 <span data-ttu-id="5d909-114">`AllocVirtual` Metoda slouží jako logické obálku pro Win32 `VirtualAlloc` funkce.</span><span class="sxs-lookup"><span data-stu-id="5d909-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="5d909-115">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d909-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d909-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d909-116">Requirements</span></span>  
 <span data-ttu-id="5d909-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d909-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d909-118">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5d909-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5d909-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d909-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d909-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d909-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d909-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d909-121">See Also</span></span>  
 [<span data-ttu-id="5d909-122">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d909-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="5d909-123">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="5d909-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
