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
ms.openlocfilehash: c901e21521e941c51939958175a5316808890e9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208613"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="e372a-102">ICorDebugHandleValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e372a-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="e372a-103">Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e372a-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e372a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e372a-104">Methods</span></span>  
  
|<span data-ttu-id="e372a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e372a-105">Method</span></span>|<span data-ttu-id="e372a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e372a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e372a-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="e372a-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="e372a-108">Uvolňuje popisovač, na který odkazuje tento `ICorDebugHandleValue` objekt, bez explicitního uvolnění ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e372a-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="e372a-109">GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="e372a-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="e372a-110">Získá hodnotu CorDebugHandleType –, která popisuje druh popisovače, na který odkazuje `ICorDebugHandleValue` .</span><span class="sxs-lookup"><span data-stu-id="e372a-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e372a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e372a-111">Remarks</span></span>  
 <span data-ttu-id="e372a-112">V případě, že došlo k `ICorDebugReferenceValue` narušení objektu při provádění laděného kódu, je zrušeno jeho platnost.</span><span class="sxs-lookup"><span data-stu-id="e372a-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="e372a-113">`ICorDebugHandleValue`Udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud není explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="e372a-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e372a-114">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e372a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e372a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e372a-115">Requirements</span></span>  
 <span data-ttu-id="e372a-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e372a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e372a-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e372a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e372a-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e372a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e372a-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e372a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e372a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e372a-120">See also</span></span>

- [<span data-ttu-id="e372a-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e372a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
