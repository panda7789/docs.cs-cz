---
title: ICorDebugGCReferenceEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178869"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="30107-102">ICorDebugGCReferenceEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="30107-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="30107-103">Získá zadaný počet [COR_GC_REFERENCE](cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které budou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="30107-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30107-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30107-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30107-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30107-105">Parameters</span></span>  
 <span data-ttu-id="30107-106">celt</span><span class="sxs-lookup"><span data-stu-id="30107-106">celt</span></span>  
 <span data-ttu-id="30107-107">[v] Počet kořenů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="30107-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="30107-108">Kořeny</span><span class="sxs-lookup"><span data-stu-id="30107-108">roots</span></span>  
 <span data-ttu-id="30107-109">[out] Pole ukazatelů, z nichž každý odkazuje na [COR_GC_REFERENCE](cor-gc-reference-structure.md) objekt, který představuje kořen objektu, který má být uvolněno.</span><span class="sxs-lookup"><span data-stu-id="30107-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="30107-110">pceltnačten</span><span class="sxs-lookup"><span data-stu-id="30107-110">pceltFetched</span></span>  
 <span data-ttu-id="30107-111">[out] Ukazatel na počet [objektů COR_GC_REFERENCE](cor-gc-reference-structure.md) skutečně `roots`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="30107-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="30107-112">Tato hodnota `null` může `celt` být, pokud je 1.</span><span class="sxs-lookup"><span data-stu-id="30107-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30107-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30107-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30107-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30107-114">Requirements</span></span>  
 <span data-ttu-id="30107-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30107-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30107-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30107-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30107-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30107-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30107-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30107-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30107-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="30107-119">See also</span></span>

- [<span data-ttu-id="30107-120">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30107-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="30107-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30107-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
