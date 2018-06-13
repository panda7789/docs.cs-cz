---
title: ICorDebugReferenceValue Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6cdfa9f3717e4025ff6f4fe6da3c1457cdebf7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422328"
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="a1cae-102">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="a1cae-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="a1cae-103">Poskytuje metody, které spravují hodnotu, která je odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="a1cae-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="a1cae-104">(To znamená, toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="a1cae-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1cae-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a1cae-105">Methods</span></span>  
  
|<span data-ttu-id="a1cae-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1cae-106">Method</span></span>|<span data-ttu-id="a1cae-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a1cae-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1cae-108">Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="a1cae-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="a1cae-109">Získá objekt, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="a1cae-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="a1cae-110">DereferenceStrong – metoda</span><span class="sxs-lookup"><span data-stu-id="a1cae-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="a1cae-111">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="a1cae-111">Not implemented.</span></span> <span data-ttu-id="a1cae-112">Tato metoda není volána.</span><span class="sxs-lookup"><span data-stu-id="a1cae-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="a1cae-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a1cae-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="a1cae-114">Získá aktuální adresa paměti odkazovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="a1cae-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="a1cae-115">IsNull – metoda</span><span class="sxs-lookup"><span data-stu-id="a1cae-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="a1cae-116">Získá hodnotu, která určuje, jestli to `ICorDebugReferenceValue` v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.</span><span class="sxs-lookup"><span data-stu-id="a1cae-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="a1cae-117">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="a1cae-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="a1cae-118">Nastaví aktuální adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="a1cae-118">Sets the current memory address.</span></span> <span data-ttu-id="a1cae-119">To znamená, tato metoda nastaví to `ICorDebugReferenceValue` tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="a1cae-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1cae-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1cae-120">Remarks</span></span>  
 <span data-ttu-id="a1cae-121">Modul CLR (CLR) může proveďte uvolňování u objektů, pokud proces vyladěnou pokračuje.</span><span class="sxs-lookup"><span data-stu-id="a1cae-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="a1cae-122">Kolekce paměti může pohyb objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="a1cae-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="a1cae-123">`ICorDebugReferenceValue` Budou buď spolupracovat s uvolnění paměti tak, aby se aktualizuje jeho informace po uvolnění paměti, nebo bude byla zneplatněna implicitně před uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a1cae-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="a1cae-124">`ICorDebugReferenceValue` Objektu může být implicitně zneplatněné, po vyladěnou proces pokračuje.</span><span class="sxs-lookup"><span data-stu-id="a1cae-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="a1cae-125">Odvozené icordebughandlevalue "–" není zrušena, dokud nebude explicitně vydané nebo vystavené.</span><span class="sxs-lookup"><span data-stu-id="a1cae-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1cae-126">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a1cae-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1cae-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1cae-127">Requirements</span></span>  
 <span data-ttu-id="a1cae-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1cae-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1cae-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1cae-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1cae-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1cae-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1cae-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1cae-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1cae-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1cae-132">See Also</span></span>  
    
    
 [<span data-ttu-id="a1cae-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1cae-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
