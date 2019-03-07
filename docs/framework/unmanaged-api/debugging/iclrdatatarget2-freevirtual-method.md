---
title: ICLRDataTarget2::FreeVirtual – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8d2f6a716c65596c781015bad0dea52705611a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487153"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="c741a-102">ICLRDataTarget2::FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c741a-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="c741a-103">Je voláno common language runtime (CLR) data access services uvolněte paměť, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="c741a-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c741a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c741a-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c741a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c741a-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c741a-106">[in] A `CLRDATA_ADDRESS` hodnotu, která určuje počáteční adresu paměti k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="c741a-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="c741a-107">[in] Velikost v bajtech, určený k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c741a-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="c741a-108">[in] Příznaky, které řídí uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c741a-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="c741a-109">Zobrazit Win32 `VirtualFree` funkce.</span><span class="sxs-lookup"><span data-stu-id="c741a-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c741a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c741a-110">Remarks</span></span>  
 <span data-ttu-id="c741a-111">`FreeVirtual` Metody slouží jako logické obálku pro Win32 `VirtualFree` funkce.</span><span class="sxs-lookup"><span data-stu-id="c741a-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="c741a-112">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c741a-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c741a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c741a-113">Requirements</span></span>  
 <span data-ttu-id="c741a-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c741a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c741a-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c741a-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c741a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c741a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c741a-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c741a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c741a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c741a-118">See also</span></span>
- [<span data-ttu-id="c741a-119">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c741a-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="c741a-120">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c741a-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
