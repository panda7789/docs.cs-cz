---
title: ICorDebugHandleValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794461"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="63c93-102">ICorDebugHandleValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63c93-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="63c93-103">Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="63c93-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63c93-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63c93-104">Methods</span></span>  
  
|<span data-ttu-id="63c93-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63c93-105">Method</span></span>|<span data-ttu-id="63c93-106">Popis</span><span class="sxs-lookup"><span data-stu-id="63c93-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63c93-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="63c93-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="63c93-108">Uvolňuje popisovač, na který odkazuje tento objekt `ICorDebugHandleValue`, bez explicitního uvolnění ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="63c93-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="63c93-109">GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="63c93-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="63c93-110">Získá hodnotu CorDebugHandleType –, která popisuje druh popisovače, na který odkazuje tento `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="63c93-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c93-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63c93-111">Remarks</span></span>  
 <span data-ttu-id="63c93-112">Objekt `ICorDebugReferenceValue` je po přerušení v provádění laděného kódu neplatný.</span><span class="sxs-lookup"><span data-stu-id="63c93-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="63c93-113">`ICorDebugHandleValue` udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud není explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="63c93-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63c93-114">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="63c93-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c93-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63c93-115">Requirements</span></span>  
 <span data-ttu-id="63c93-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c93-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c93-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63c93-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63c93-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="63c93-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c93-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c93-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c93-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63c93-120">See also</span></span>

- [<span data-ttu-id="63c93-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="63c93-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
