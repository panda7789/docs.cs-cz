---
title: ICLRDataTarget2::AllocVirtual – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e63b6a015bd1ffa86d8fd04b0154dbade85a35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465917"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="8de84-102">ICLRDataTarget2::AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="8de84-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="8de84-103">Je voláno common language runtime (CLR) data access services přidělení paměti v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="8de84-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8de84-104">Syntax</span></span>  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8de84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8de84-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="8de84-106">[in] A `CLRDATA_ADDRESS` hodnota, která určuje požadovanou počáteční adresu paměti, která bude přidělena.</span><span class="sxs-lookup"><span data-stu-id="8de84-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="8de84-107">[in] Velikost v bajtech, která bude přidělena paměť.</span><span class="sxs-lookup"><span data-stu-id="8de84-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="8de84-108">[in] Příznaky, které řídí přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="8de84-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="8de84-109">Zobrazit Win32 `VirtualAlloc` funkce.</span><span class="sxs-lookup"><span data-stu-id="8de84-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="8de84-110">[in] Atributy ochrany pro přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="8de84-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="8de84-111">Zobrazit Win32 `VirtualAlloc` funkce.</span><span class="sxs-lookup"><span data-stu-id="8de84-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="8de84-112">[out] Ukazatel `CLRDATA_ADDRESS` hodnota, která určuje skutečné počáteční adresa přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="8de84-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de84-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8de84-113">Remarks</span></span>  
 <span data-ttu-id="8de84-114">`AllocVirtual` Metody slouží jako logické obálku pro Win32 `VirtualAlloc` funkce.</span><span class="sxs-lookup"><span data-stu-id="8de84-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="8de84-115">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8de84-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de84-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8de84-116">Requirements</span></span>  
 <span data-ttu-id="8de84-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8de84-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de84-118">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8de84-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8de84-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8de84-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8de84-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de84-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de84-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8de84-121">See also</span></span>
- [<span data-ttu-id="8de84-122">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8de84-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="8de84-123">FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="8de84-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
