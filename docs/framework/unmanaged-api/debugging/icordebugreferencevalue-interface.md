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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6575acfb1f75cbc8e3d59ddca5fea0953274cf2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206457"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="9f89a-102">ICorDebugReferenceValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f89a-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="9f89a-103">Poskytuje metody, které spravují hodnotu, která je odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="9f89a-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="9f89a-104">(To znamená, že toto rozhraní poskytuje metody, které spravují ukazatel.) Toto rozhraní implementuje "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="9f89a-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f89a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9f89a-105">Methods</span></span>  
  
|<span data-ttu-id="9f89a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9f89a-106">Method</span></span>|<span data-ttu-id="9f89a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9f89a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f89a-108">Dereference – metoda</span><span class="sxs-lookup"><span data-stu-id="9f89a-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="9f89a-109">Získá objekt, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="9f89a-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="9f89a-110">DereferenceStrong – metoda</span><span class="sxs-lookup"><span data-stu-id="9f89a-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="9f89a-111">Není implementováno.</span><span class="sxs-lookup"><span data-stu-id="9f89a-111">Not implemented.</span></span> <span data-ttu-id="9f89a-112">Nevolejte tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="9f89a-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="9f89a-113">GetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="9f89a-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="9f89a-114">Získá aktuální adresu paměti odkazovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="9f89a-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="9f89a-115">IsNull – metoda</span><span class="sxs-lookup"><span data-stu-id="9f89a-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="9f89a-116">Získá hodnotu, která určuje, jestli to `ICorDebugReferenceValue` v takovém případě je hodnota null, `ICorDebugReferenceValue` neukazuje na objekt.</span><span class="sxs-lookup"><span data-stu-id="9f89a-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="9f89a-117">SetValue – metoda</span><span class="sxs-lookup"><span data-stu-id="9f89a-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="9f89a-118">Nastaví aktuální adresu paměti.</span><span class="sxs-lookup"><span data-stu-id="9f89a-118">Sets the current memory address.</span></span> <span data-ttu-id="9f89a-119">To znamená, že tato metoda nastaví tuto `ICorDebugReferenceValue` tak, aby odkazoval na objekt.</span><span class="sxs-lookup"><span data-stu-id="9f89a-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f89a-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f89a-120">Remarks</span></span>  
 <span data-ttu-id="9f89a-121">Modul CLR (CLR) může provádět uvolňování objektů při pokračování laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="9f89a-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="9f89a-122">Uvolnění paměti může pohyb objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="9f89a-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="9f89a-123">`ICorDebugReferenceValue` Buď spolupracují s kolekcí uvolnění paměti tak, aby se informace aktualizují po uvolnění paměti nebo ho se implicitně zruší před uvolňování.</span><span class="sxs-lookup"><span data-stu-id="9f89a-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="9f89a-124">`ICorDebugReferenceValue` Objekt může být implicitně zneplatněné, po pokračuje laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="9f89a-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="9f89a-125">Odvozené icordebughandlevalue "–" není zrušena, dokud je explicitně vydání nebo vystavené.</span><span class="sxs-lookup"><span data-stu-id="9f89a-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f89a-126">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="9f89a-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f89a-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f89a-127">Requirements</span></span>  
 <span data-ttu-id="9f89a-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f89a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f89a-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f89a-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f89a-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f89a-130">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9f89a-131">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9f89a-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f89a-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f89a-132">See also</span></span>

- [<span data-ttu-id="9f89a-133">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f89a-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
