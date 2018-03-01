---
title: "ICorDebugProcess5::EnumerateGCReferences – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44975a7896c71ce8061dedde13d31c4fbb88d6a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="a0700-102">ICorDebugProcess5::EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="a0700-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="a0700-103">Získá enumerátor pro všechny objekty, které mají být uklizeny v procesu.</span><span class="sxs-lookup"><span data-stu-id="a0700-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0700-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0700-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0700-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0700-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="a0700-106">[v] Logická hodnota, která určuje, zda slabé odkazy jsou také výčet.</span><span class="sxs-lookup"><span data-stu-id="a0700-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="a0700-107">Pokud `enumerateWeakReferences` je `true`, `ppEnum` enumerátor zahrnuje silné odkazy a slabé odkazy.</span><span class="sxs-lookup"><span data-stu-id="a0700-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="a0700-108">Pokud `enumerateWeakReferences` je `false`, enumerátor obsahuje pouze silné odkazy.</span><span class="sxs-lookup"><span data-stu-id="a0700-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="a0700-109">[out] Ukazatel na adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) tedy enumerátor pro objekty být uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a0700-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0700-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0700-110">Remarks</span></span>  
 <span data-ttu-id="a0700-111">Tato metoda poskytuje způsob, jak určit úplnou rooting řetězu pro každý spravovaný objekt v procesu a umožňuje zjistit, proč je objekt stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="a0700-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0700-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a0700-112">Requirements</span></span>  
 <span data-ttu-id="a0700-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0700-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0700-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0700-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0700-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0700-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0700-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0700-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0700-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0700-117">See Also</span></span>  
 [<span data-ttu-id="a0700-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a0700-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="a0700-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a0700-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
