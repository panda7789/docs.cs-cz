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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0845165e3200d7a5e14715cbe116ea5255aa021
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948769"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="d8238-102">ICorDebugProcess5::EnumerateGCReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="d8238-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="d8238-103">Získá enumerátor pro všechny objekty, které mají být prováděno uvolnění paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="d8238-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8238-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8238-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8238-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8238-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="d8238-106">[in] Logická hodnota, která určuje, zda slabé odkazy taky jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="d8238-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="d8238-107">Pokud `enumerateWeakReferences` je `true`, `ppEnum` enumerátor obsahuje odkazy na silné a slabé odkazy.</span><span class="sxs-lookup"><span data-stu-id="d8238-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="d8238-108">Pokud `enumerateWeakReferences` je `false`, enumerátor obsahuje pouze silné odkazy.</span><span class="sxs-lookup"><span data-stu-id="d8238-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="d8238-109">[out] Ukazatel na adresu [icordebuggcreferenceenum –](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , který je enumerátor pro objekty být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d8238-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8238-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8238-110">Remarks</span></span>  
 <span data-ttu-id="d8238-111">Tato metoda poskytuje způsob, jak určit úplný řetěz kořenové pro každý spravovaný objekt v procesu a je možné zjistit, proč je objekt stále aktivní.</span><span class="sxs-lookup"><span data-stu-id="d8238-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8238-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8238-112">Requirements</span></span>  
 <span data-ttu-id="d8238-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8238-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8238-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8238-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8238-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8238-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8238-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8238-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8238-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8238-117">See also</span></span>

- [<span data-ttu-id="d8238-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8238-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="d8238-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d8238-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
