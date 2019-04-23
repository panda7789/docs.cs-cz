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
ms.openlocfilehash: b30bd3e97af8d222f629c5b4f9f318a9b6379e78
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181399"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="0fd32-102">ICLRDataTarget2::FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="0fd32-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="0fd32-103">Je voláno common language runtime (CLR) data access services uvolněte paměť, která byla dříve přidělena v adresním prostoru cílového procesu.</span><span class="sxs-lookup"><span data-stu-id="0fd32-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fd32-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd32-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fd32-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="0fd32-106">[in] A `CLRDATA_ADDRESS` hodnotu, která určuje počáteční adresu paměti k uvolnění.</span><span class="sxs-lookup"><span data-stu-id="0fd32-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="0fd32-107">[in] Velikost v bajtech, určený k uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0fd32-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="0fd32-108">[in] Příznaky, které řídí uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0fd32-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="0fd32-109">Zobrazit Win32 `VirtualFree` funkce.</span><span class="sxs-lookup"><span data-stu-id="0fd32-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fd32-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fd32-110">Remarks</span></span>  
 <span data-ttu-id="0fd32-111">`FreeVirtual` Metody slouží jako logické obálku pro Win32 `VirtualFree` funkce.</span><span class="sxs-lookup"><span data-stu-id="0fd32-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="0fd32-112">Tato metoda je implementováno tvůrci ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="0fd32-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd32-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0fd32-113">Requirements</span></span>  
 <span data-ttu-id="0fd32-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd32-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd32-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0fd32-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0fd32-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fd32-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fd32-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd32-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fd32-118">See also</span></span>

- [<span data-ttu-id="0fd32-119">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0fd32-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="0fd32-120">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="0fd32-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
