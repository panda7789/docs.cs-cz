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
ms.openlocfilehash: 3a8e967a3ecc452ebda08872d8bcd9e9d08c766f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777695"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="023a3-102">ICorDebugGCReferenceEnum::Next – metoda</span><span class="sxs-lookup"><span data-stu-id="023a3-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="023a3-103">Získá zadaný počet instancí [COR_GC_REFERENCE](cor-gc-reference-structure.md) , které obsahují informace o objektech, které budou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="023a3-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="023a3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="023a3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="023a3-105">Parameters</span></span>  
 <span data-ttu-id="023a3-106">celt</span><span class="sxs-lookup"><span data-stu-id="023a3-106">celt</span></span>  
 <span data-ttu-id="023a3-107">pro Počet kořenových adresářů, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="023a3-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="023a3-108">autorit</span><span class="sxs-lookup"><span data-stu-id="023a3-108">roots</span></span>  
 <span data-ttu-id="023a3-109">mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_GC_REFERENCE](cor-gc-reference-structure.md) , který představuje kořen objektu, který má být shromážděn z paměti.</span><span class="sxs-lookup"><span data-stu-id="023a3-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="023a3-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="023a3-110">pceltFetched</span></span>  
 <span data-ttu-id="023a3-111">mimo Ukazatel na počet objektů [COR_GC_REFERENCE](cor-gc-reference-structure.md) ve skutečnosti vrácených v `roots`.</span><span class="sxs-lookup"><span data-stu-id="023a3-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="023a3-112">Tato hodnota může být `null`, pokud `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="023a3-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="023a3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="023a3-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023a3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="023a3-114">Requirements</span></span>  
 <span data-ttu-id="023a3-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="023a3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="023a3-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="023a3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="023a3-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="023a3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="023a3-118">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="023a3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023a3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="023a3-119">See also</span></span>

- [<span data-ttu-id="023a3-120">ICorDebugGCReferenceEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="023a3-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="023a3-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="023a3-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
