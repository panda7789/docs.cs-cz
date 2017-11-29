---
title: ICorDebugReferenceValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue
helpviewer_keywords: ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d11cb4cbd6baa1e0d381c9fb11d5a3343287cf55
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="c197f-102">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="c197f-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="c197f-103">Poskytuje metody, které spravují hodnotu, která je odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="c197f-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="c197f-104">(To znamená, toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="c197f-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c197f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c197f-105">Methods</span></span>  
  
|<span data-ttu-id="c197f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c197f-106">Method</span></span>|<span data-ttu-id="c197f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c197f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c197f-108">Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="c197f-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="c197f-109">Získá objekt, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="c197f-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="c197f-110">Dereferencestrong – metoda</span><span class="sxs-lookup"><span data-stu-id="c197f-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="c197f-111">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="c197f-111">Not implemented.</span></span> <span data-ttu-id="c197f-112">Tato metoda není volána.</span><span class="sxs-lookup"><span data-stu-id="c197f-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="c197f-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c197f-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="c197f-114">Získá aktuální adresa paměti odkazovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="c197f-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="c197f-115">IsNull – metoda</span><span class="sxs-lookup"><span data-stu-id="c197f-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="c197f-116">Získá hodnotu, která určuje, jestli to `ICorDebugReferenceValue` v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.</span><span class="sxs-lookup"><span data-stu-id="c197f-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="c197f-117">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="c197f-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="c197f-118">Nastaví aktuální adresa paměti.</span><span class="sxs-lookup"><span data-stu-id="c197f-118">Sets the current memory address.</span></span> <span data-ttu-id="c197f-119">To znamená, tato metoda nastaví to `ICorDebugReferenceValue` tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="c197f-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c197f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c197f-120">Remarks</span></span>  
 <span data-ttu-id="c197f-121">Modul CLR (CLR) může proveďte uvolňování u objektů, pokud proces vyladěnou pokračuje.</span><span class="sxs-lookup"><span data-stu-id="c197f-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="c197f-122">Kolekce paměti může pohyb objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="c197f-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="c197f-123">`ICorDebugReferenceValue` Budou buď spolupracovat s uvolnění paměti tak, aby se aktualizuje jeho informace po uvolnění paměti, nebo bude byla zneplatněna implicitně před uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c197f-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="c197f-124">`ICorDebugReferenceValue` Objektu může být implicitně zneplatněné, po vyladěnou proces pokračuje.</span><span class="sxs-lookup"><span data-stu-id="c197f-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="c197f-125">Odvozené icordebughandlevalue "–" není zrušena, dokud nebude explicitně vydané nebo vystavené.</span><span class="sxs-lookup"><span data-stu-id="c197f-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c197f-126">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c197f-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c197f-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c197f-127">Requirements</span></span>  
 <span data-ttu-id="c197f-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c197f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c197f-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c197f-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c197f-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c197f-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c197f-131">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c197f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c197f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="c197f-132">See Also</span></span>  
    
    
 [<span data-ttu-id="c197f-133">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="c197f-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
