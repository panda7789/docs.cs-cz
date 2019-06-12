---
title: ICorDebugAppDomain3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025894"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="fc4c0-102">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc4c0-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="fc4c0-103">Poskytuje metody pro načtení informací o spravované reprezentace typů prostředí Windows Runtime aktuálně načtené v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="fc4c0-104">Toto rozhraní je rozšířením ICorDebugAppDomain a icordebugappdomain2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc4c0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fc4c0-105">Methods</span></span>  
  
|<span data-ttu-id="fc4c0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc4c0-106">Method</span></span>|<span data-ttu-id="fc4c0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fc4c0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc4c0-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="fc4c0-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="fc4c0-109">Získá enumerátor pro všechny typy v mezipaměti prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="fc4c0-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="fc4c0-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="fc4c0-111">Získá enumerátor pro uložené v mezipaměti typy Windows Runtime v doméně aplikace podle jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc4c0-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc4c0-112">Remarks</span></span>  
 <span data-ttu-id="fc4c0-113">Toto rozhraní je určen pro použití pomocí ladicího programu ve spojení s voláním funkce vyhodnocení `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="fc4c0-114">Metoda načte identifikátory rozhraní nepodporuje objekt prostředí Windows Runtime serveru, se může ladicí program je namapovat na spravované typy, které odpovídají těchto rozhraní pomocí metody definované v tomto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="fc4c0-115">Pokud chcete načíst instanci tohoto rozhraní, spusťte `QueryInterface` instance ICorDebugAppDomain nebo icordebugappdomain2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc4c0-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="fc4c0-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc4c0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc4c0-117">Requirements</span></span>  
 <span data-ttu-id="fc4c0-118">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="fc4c0-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="fc4c0-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc4c0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc4c0-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc4c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc4c0-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4c0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc4c0-122">See also</span></span>

- [<span data-ttu-id="fc4c0-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fc4c0-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
