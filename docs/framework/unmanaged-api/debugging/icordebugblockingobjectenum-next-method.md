---
title: ICorDebugBlockingObjectEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 0ef49d2d833841eac62b2b964a0fdc902b4fb6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894775"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="0bfdd-102">ICorDebugBlockingObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0bfdd-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="0bfdd-103">Získá zadaný počet objektů [CorDebugBlockingObject –](cordebugblockingobject-structure.md) z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-103">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bfdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bfdd-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bfdd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bfdd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0bfdd-106">pro Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="0bfdd-107">mimo Pole ukazatelů na [CorDebugBlockingObject –](cordebugblockingobject-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-107">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0bfdd-108">mimo Ukazatel na počet objektů, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bfdd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0bfdd-109">Return Value</span></span>  
 <span data-ttu-id="0bfdd-110">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="0bfdd-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0bfdd-111">HRESULT</span></span>|<span data-ttu-id="0bfdd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0bfdd-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bfdd-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0bfdd-113">S_OK</span></span>|<span data-ttu-id="0bfdd-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0bfdd-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0bfdd-115">S_FALSE</span></span>|<span data-ttu-id="0bfdd-116">`pceltFetched`se nerovná `celt`.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bfdd-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bfdd-117">Remarks</span></span>  
 <span data-ttu-id="0bfdd-118">Tato metoda funguje jako typický enumerátor COM.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="0bfdd-119">Hodnoty vstupního pole musí mít aspoň velikost `celt`.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="0bfdd-120">Pole bude vyplněno buď pomocí dalších `celt` hodnot ve výčtu, nebo se všemi zbývajícími hodnotami, pokud je méně než `celt` zbývá.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="0bfdd-121">Když se tato metoda vrátí `pceltFetched` , vyplní se počtem hodnot, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="0bfdd-122">Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`nebo pokud `pceltFetched` je neplatný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bfdd-123">I když struktura [CorDebugBlockingObject –](cordebugblockingobject-structure.md) nemusí být uvolněna, je nutné uvolnit rozhraní "ICorDebugValue" uvnitř této struktury.</span><span class="sxs-lookup"><span data-stu-id="0bfdd-123">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bfdd-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bfdd-124">Requirements</span></span>  
 <span data-ttu-id="0bfdd-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bfdd-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bfdd-126">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0bfdd-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bfdd-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bfdd-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bfdd-128">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bfdd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfdd-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bfdd-129">See also</span></span>

- [<span data-ttu-id="0bfdd-130">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bfdd-130">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="0bfdd-131">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bfdd-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0bfdd-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="0bfdd-132">Debugging</span></span>](index.md)
