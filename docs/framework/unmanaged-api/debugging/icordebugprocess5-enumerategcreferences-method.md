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
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178625"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="91358-102">ICorDebugProcess5::EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="91358-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="91358-103">Získá čítač výčtu pro všechny objekty, které mají být uvolněny v procesu.</span><span class="sxs-lookup"><span data-stu-id="91358-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91358-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91358-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91358-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91358-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="91358-106">[v] Logická hodnota, která označuje, zda mají být také uvedeny slabé odkazy.</span><span class="sxs-lookup"><span data-stu-id="91358-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="91358-107">Pokud `enumerateWeakReferences` `true`je `ppEnum` , čítač obsahuje silné odkazy a slabé odkazy.</span><span class="sxs-lookup"><span data-stu-id="91358-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="91358-108">Pokud `enumerateWeakReferences` `false`je , čítač obsahuje pouze silné odkazy.</span><span class="sxs-lookup"><span data-stu-id="91358-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="91358-109">[out] Ukazatel na adresu [ICorDebugGCReferenceEnum,](icordebuggcreferenceenum-interface.md) který je čítač výčtu pro objekty, které mají být uvolněny.</span><span class="sxs-lookup"><span data-stu-id="91358-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91358-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91358-110">Remarks</span></span>  
 <span data-ttu-id="91358-111">Tato metoda poskytuje způsob, jak určit celý řetězec zakořenění pro libovolný spravovaný objekt v procesu a lze určit, proč je objekt stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="91358-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91358-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91358-112">Requirements</span></span>  
 <span data-ttu-id="91358-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91358-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91358-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91358-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91358-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91358-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91358-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91358-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91358-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="91358-117">See also</span></span>

- [<span data-ttu-id="91358-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91358-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="91358-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91358-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
