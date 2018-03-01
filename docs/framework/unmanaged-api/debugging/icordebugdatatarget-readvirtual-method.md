---
title: "ICorDebugDataTarget::ReadVirtual – metoda"
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
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a406af14d4cb5612009972542c0efe9c1b5f62cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="e16f4-102">ICorDebugDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="e16f4-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="e16f4-103">Získá blok souvislé paměti začínající na zadanou adresu a vrátí ji v poskytnutá vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="e16f4-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e16f4-104">Syntax</span></span>  
  
```  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e16f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e16f4-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e16f4-106">[v] Počáteční adresa požadovanou paměť.</span><span class="sxs-lookup"><span data-stu-id="e16f4-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="e16f4-107">[out] Vyrovnávací paměť, kde bude uložena paměti.</span><span class="sxs-lookup"><span data-stu-id="e16f4-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="e16f4-108">[v] Počet bajtů, které mají získat z cílovou adresu.</span><span class="sxs-lookup"><span data-stu-id="e16f4-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="e16f4-109">[out] Počet bajtů ve skutečnosti čtení z cílovou adresu.</span><span class="sxs-lookup"><span data-stu-id="e16f4-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="e16f4-110">To může být méně než `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="e16f4-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e16f4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e16f4-111">Remarks</span></span>  
 <span data-ttu-id="e16f4-112">Pokud lze číst prvního bajtu (na adrese zadaným počátečním), by měla vrátit volání úspěšné (pro podporu efektivní čtení datových struktur s popisující samy sebe délka jako řetězce ukončené hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="e16f4-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e16f4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e16f4-113">Requirements</span></span>  
 <span data-ttu-id="e16f4-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e16f4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e16f4-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e16f4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e16f4-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e16f4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e16f4-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e16f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16f4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e16f4-118">See Also</span></span>  
 [<span data-ttu-id="e16f4-119">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e16f4-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="e16f4-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e16f4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e16f4-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="e16f4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
