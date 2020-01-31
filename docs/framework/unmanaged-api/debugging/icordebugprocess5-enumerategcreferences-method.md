---
title: ICorDebugProcess5::EnumerateGCReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 81993f108ae9b59300b5d29402d7a423c3657757
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792438"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="cb5eb-102">ICorDebugProcess5::EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="cb5eb-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="cb5eb-103">Získá enumerátor pro všechny objekty, které mají být v procesu shromažďovány jako uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="cb5eb-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb5eb-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb5eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb5eb-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="cb5eb-106">pro Logická hodnota, která určuje, zda mají být také vyčísleny slabé odkazy.</span><span class="sxs-lookup"><span data-stu-id="cb5eb-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="cb5eb-107">Pokud je `enumerateWeakReferences` `true`, enumerátor `ppEnum` zahrnuje silné odkazy i slabé odkazy.</span><span class="sxs-lookup"><span data-stu-id="cb5eb-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="cb5eb-108">Pokud je `enumerateWeakReferences` `false`, enumerátor zahrnuje pouze silné odkazy.</span><span class="sxs-lookup"><span data-stu-id="cb5eb-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="cb5eb-109">mimo Ukazatel na adresu [ICorDebugGCReferenceEnum –](icordebuggcreferenceenum-interface.md) , která je enumerátorem pro objekty, které mají být shromážděny z paměti.</span><span class="sxs-lookup"><span data-stu-id="cb5eb-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb5eb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb5eb-110">Remarks</span></span>  
 <span data-ttu-id="cb5eb-111">Tato metoda poskytuje způsob, jak určit úplný kořenový řetězec pro jakýkoli spravovaný objekt v procesu a který lze použít k určení, proč je objekt stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="cb5eb-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5eb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb5eb-112">Requirements</span></span>  
 <span data-ttu-id="cb5eb-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5eb-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb5eb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb5eb-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cb5eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb5eb-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5eb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb5eb-117">See also</span></span>

- [<span data-ttu-id="cb5eb-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb5eb-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="cb5eb-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cb5eb-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
