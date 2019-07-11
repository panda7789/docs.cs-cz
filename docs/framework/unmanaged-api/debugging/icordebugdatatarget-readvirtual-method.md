---
title: ICorDebugDataTarget::ReadVirtual – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9d42c85502c12d4d77694626a533c69af97da67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750260"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="7e0a6-102">ICorDebugDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="7e0a6-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="7e0a6-103">Získá blok souvislé paměti začínající na zadané adrese a vrátí jej v poskytnutá vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="7e0a6-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e0a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e0a6-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e0a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e0a6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="7e0a6-106">[in] Počáteční adresa požadované paměti.</span><span class="sxs-lookup"><span data-stu-id="7e0a6-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="7e0a6-107">[out] Vyrovnávací paměť, kde budou uloženy paměti.</span><span class="sxs-lookup"><span data-stu-id="7e0a6-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="7e0a6-108">[in] Počet bajtů, které mají získat z cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="7e0a6-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="7e0a6-109">[out] Počet bajtů ke čtení ve skutečnosti z cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="7e0a6-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="7e0a6-110">To může být kratší než `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="7e0a6-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e0a6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e0a6-111">Remarks</span></span>  
 <span data-ttu-id="7e0a6-112">Pokud lze číst prvního bajtu (na adrese zadaným počátečním), by měla vrátit volání úspěšné (pro podporu efektivního čtení datových struktur s popisující samy sebe délku, jako je řetězec zakončený null).</span><span class="sxs-lookup"><span data-stu-id="7e0a6-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e0a6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e0a6-113">Requirements</span></span>  
 <span data-ttu-id="7e0a6-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e0a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e0a6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e0a6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e0a6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e0a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e0a6-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e0a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e0a6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e0a6-118">See also</span></span>

- [<span data-ttu-id="7e0a6-119">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e0a6-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="7e0a6-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7e0a6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7e0a6-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="7e0a6-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
