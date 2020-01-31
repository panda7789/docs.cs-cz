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
ms.openlocfilehash: c25f26bb0f1f34e3799bab4bec7e697d393cccb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784518"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="37103-102">ICorDebugBlockingObjectEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="37103-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="37103-103">Získá zadaný počet objektů [CorDebugBlockingObject –](cordebugblockingobject-structure.md) z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="37103-103">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37103-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37103-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="37103-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37103-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="37103-106">pro Počet objektů, které se mají načíst.</span><span class="sxs-lookup"><span data-stu-id="37103-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="37103-107">mimo Pole ukazatelů na [CorDebugBlockingObject –](cordebugblockingobject-structure.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="37103-107">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="37103-108">mimo Ukazatel na počet objektů, které byly načteny.</span><span class="sxs-lookup"><span data-stu-id="37103-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37103-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37103-109">Return Value</span></span>  
 <span data-ttu-id="37103-110">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="37103-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="37103-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37103-111">HRESULT</span></span>|<span data-ttu-id="37103-112">Popis</span><span class="sxs-lookup"><span data-stu-id="37103-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37103-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="37103-113">S_OK</span></span>|<span data-ttu-id="37103-114">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="37103-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="37103-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="37103-115">S_FALSE</span></span>|<span data-ttu-id="37103-116">`pceltFetched` se nerovná `celt`.</span><span class="sxs-lookup"><span data-stu-id="37103-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37103-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37103-117">Remarks</span></span>  
 <span data-ttu-id="37103-118">Tato metoda funguje jako typický enumerátor COM.</span><span class="sxs-lookup"><span data-stu-id="37103-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="37103-119">Hodnoty vstupního pole musí mít velikost alespoň `celt`.</span><span class="sxs-lookup"><span data-stu-id="37103-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="37103-120">Pole bude vyplněno buď další `celt` hodnoty ve výčtu, nebo všechny zbývající hodnoty, pokud méně než `celt` zůstane.</span><span class="sxs-lookup"><span data-stu-id="37103-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="37103-121">Když se tato metoda vrátí, `pceltFetched` vyplní počet hodnot, které se načetly.</span><span class="sxs-lookup"><span data-stu-id="37103-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="37103-122">Pokud `values` obsahuje neplatné ukazatele nebo odkazuje na vyrovnávací paměť, která je menší než `celt`, nebo pokud je `pceltFetched` neplatný ukazatel, výsledek není definován.</span><span class="sxs-lookup"><span data-stu-id="37103-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37103-123">I když struktura [CorDebugBlockingObject –](cordebugblockingobject-structure.md) nemusí být uvolněna, je nutné uvolnit rozhraní "ICorDebugValue" uvnitř této struktury.</span><span class="sxs-lookup"><span data-stu-id="37103-123">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37103-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37103-124">Requirements</span></span>  
 <span data-ttu-id="37103-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37103-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37103-126">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37103-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37103-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="37103-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37103-128">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37103-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37103-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37103-129">See also</span></span>

- [<span data-ttu-id="37103-130">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37103-130">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="37103-131">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="37103-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="37103-132">Ladění</span><span class="sxs-lookup"><span data-stu-id="37103-132">Debugging</span></span>](index.md)
