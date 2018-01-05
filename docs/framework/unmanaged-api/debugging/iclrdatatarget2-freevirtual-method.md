---
title: "ICLRDataTarget2::FreeVirtual – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.FreeVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6c52291d08af4c9537de6ca17d80f28870a6bc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="cad68-102">ICLRDataTarget2::FreeVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="cad68-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="cad68-103">Voláno rozhraním common language runtime (CLR) služby přístupu k datům volné paměti, které již bylo přiděleno v adresním prostoru tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="cad68-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cad68-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cad68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cad68-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="cad68-106">[v] A `CLRDATA_ADDRESS` hodnotu, která určuje počáteční adresa paměti na uvolnění.</span><span class="sxs-lookup"><span data-stu-id="cad68-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="cad68-107">[v] Velikost v bajtech, na uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="cad68-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="cad68-108">[v] Příznaky, které řídí uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="cad68-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="cad68-109">V tématu Win32 `VirtualFree` funkce.</span><span class="sxs-lookup"><span data-stu-id="cad68-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cad68-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cad68-110">Remarks</span></span>  
 <span data-ttu-id="cad68-111">`FreeVirtual` Metoda slouží jako logické obálku pro Win32 `VirtualFree` funkce.</span><span class="sxs-lookup"><span data-stu-id="cad68-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="cad68-112">Tato metoda je implementována zapisovačem ladění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cad68-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cad68-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cad68-113">Requirements</span></span>  
 <span data-ttu-id="cad68-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad68-115">**Záhlaví:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cad68-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cad68-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cad68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cad68-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad68-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="cad68-118">See Also</span></span>  
 [<span data-ttu-id="cad68-119">ICLRDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cad68-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="cad68-120">AllocVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="cad68-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
