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
ms.openlocfilehash: 87316b20c5835d9b887355a1f9374fa5f2156e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122171"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="cc59c-102">ICorDebugDataTarget::ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="cc59c-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="cc59c-103">Načte blok souvislé paměti začínající na zadané adrese a vrátí ji do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="cc59c-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc59c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc59c-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc59c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc59c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cc59c-106">pro Počáteční adresa požadované paměti.</span><span class="sxs-lookup"><span data-stu-id="cc59c-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="cc59c-107">mimo Vyrovnávací paměť, do které se uloží paměť.</span><span class="sxs-lookup"><span data-stu-id="cc59c-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="cc59c-108">pro Počet bajtů, které mají být získány z cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="cc59c-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="cc59c-109">mimo Počet bajtů skutečně přečtených z cílové adresy.</span><span class="sxs-lookup"><span data-stu-id="cc59c-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="cc59c-110">To může být méně než `bytesRequested`.</span><span class="sxs-lookup"><span data-stu-id="cc59c-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc59c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc59c-111">Remarks</span></span>  
 <span data-ttu-id="cc59c-112">Pokud je možné číst první bajt (na zadané počáteční adrese), volání by mělo vracet úspěch (pro podporu efektivního čtení datových struktur s délkou, jako jsou řetězce zakončené znakem null).</span><span class="sxs-lookup"><span data-stu-id="cc59c-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc59c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc59c-113">Requirements</span></span>  
 <span data-ttu-id="cc59c-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc59c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc59c-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc59c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc59c-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cc59c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc59c-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc59c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc59c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc59c-118">See also</span></span>

- [<span data-ttu-id="cc59c-119">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc59c-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="cc59c-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cc59c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cc59c-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="cc59c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
