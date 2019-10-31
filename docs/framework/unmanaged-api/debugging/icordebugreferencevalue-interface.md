---
title: ICorDebugReferenceValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 16d7b89ee441e8d634c36fb87185b3f2846860b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137711"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="01178-102">ICorDebugReferenceValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01178-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="01178-103">Poskytuje metody, které spravují hodnotu, která je odkazem na objekt.</span><span class="sxs-lookup"><span data-stu-id="01178-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="01178-104">(To znamená, že toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="01178-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01178-105">Metody</span><span class="sxs-lookup"><span data-stu-id="01178-105">Methods</span></span>  
  
|<span data-ttu-id="01178-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="01178-106">Method</span></span>|<span data-ttu-id="01178-107">Popis</span><span class="sxs-lookup"><span data-stu-id="01178-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01178-108">Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="01178-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="01178-109">Načte objekt, na který je odkazováno.</span><span class="sxs-lookup"><span data-stu-id="01178-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="01178-110">DereferenceStrong – metoda</span><span class="sxs-lookup"><span data-stu-id="01178-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="01178-111">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="01178-111">Not implemented.</span></span> <span data-ttu-id="01178-112">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="01178-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="01178-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="01178-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="01178-114">Získá aktuální adresu paměti odkazovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="01178-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="01178-115">IsNull – metoda</span><span class="sxs-lookup"><span data-stu-id="01178-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="01178-116">Získá hodnotu, která označuje, zda je tato `ICorDebugReferenceValue` hodnotou null. v takovém případě `ICorDebugReferenceValue` neodkazuje na objekt.</span><span class="sxs-lookup"><span data-stu-id="01178-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="01178-117">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="01178-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="01178-118">Nastaví aktuální adresu paměti.</span><span class="sxs-lookup"><span data-stu-id="01178-118">Sets the current memory address.</span></span> <span data-ttu-id="01178-119">To znamená, že tato metoda nastaví tuto `ICorDebugReferenceValue` tak, aby odkazovala na objekt.</span><span class="sxs-lookup"><span data-stu-id="01178-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01178-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01178-120">Remarks</span></span>  
 <span data-ttu-id="01178-121">Modul CLR (Common Language Runtime) může provést uvolňování paměti objektů, když probíhá laděný proces.</span><span class="sxs-lookup"><span data-stu-id="01178-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="01178-122">Uvolňování paměti může přesunout objekty kolem paměti.</span><span class="sxs-lookup"><span data-stu-id="01178-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="01178-123">`ICorDebugReferenceValue` bude spolupracovat s uvolňováním paměti, takže jeho informace budou aktualizovány po uvolnění paměti nebo implicitně neověřeny před uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="01178-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="01178-124">Po pokračování procesu ladění může být objekt `ICorDebugReferenceValue` implicitně neověřený.</span><span class="sxs-lookup"><span data-stu-id="01178-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="01178-125">Odvozená "ICorDebugHandleValue" není neověřená, dokud není explicitně uvolněna nebo vystavena.</span><span class="sxs-lookup"><span data-stu-id="01178-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01178-126">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="01178-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01178-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01178-127">Requirements</span></span>  
 <span data-ttu-id="01178-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01178-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01178-129">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="01178-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01178-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01178-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01178-131">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01178-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01178-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01178-132">See also</span></span>

- [<span data-ttu-id="01178-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="01178-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
