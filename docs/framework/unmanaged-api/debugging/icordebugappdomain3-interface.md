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
ms.openlocfilehash: 7c141ca9a8e1c74015883f45cb2eaa9183bb3d89
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177525"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="d77b9-102">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d77b9-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="d77b9-103">Poskytuje metody pro načtení informací o spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy aktuálně načtené v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d77b9-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="d77b9-104">Toto rozhraní je rozšířením ICorDebugAppDomain a icordebugappdomain2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d77b9-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d77b9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d77b9-105">Methods</span></span>  
  
|<span data-ttu-id="d77b9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d77b9-106">Method</span></span>|<span data-ttu-id="d77b9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d77b9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d77b9-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="d77b9-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="d77b9-109">Získá enumerátor pro všechny uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy.</span><span class="sxs-lookup"><span data-stu-id="d77b9-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="d77b9-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="d77b9-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="d77b9-111">Získá enumerátor pro uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v doméně aplikace podle jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d77b9-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d77b9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d77b9-112">Remarks</span></span>  
 <span data-ttu-id="d77b9-113">Toto rozhraní je určen pro použití pomocí ladicího programu ve spojení s voláním funkce vyhodnocení `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="d77b9-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="d77b9-114">Když metoda načte identifikátory rozhraní nepodporuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objekt serveru, ladicí program může používat metody definované v tomto rozhraní pro mapování na spravované typy, které odpovídají těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d77b9-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="d77b9-115">Pokud chcete načíst instanci tohoto rozhraní, spusťte `QueryInterface` instance ICorDebugAppDomain nebo icordebugappdomain2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d77b9-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d77b9-116">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d77b9-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d77b9-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d77b9-117">Requirements</span></span>  
 **<span data-ttu-id="d77b9-118">Platformy:</span><span class="sxs-lookup"><span data-stu-id="d77b9-118">Platforms:</span></span>** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 <span data-ttu-id="d77b9-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d77b9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d77b9-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d77b9-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d77b9-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d77b9-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d77b9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d77b9-122">See also</span></span>

- [<span data-ttu-id="d77b9-123">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d77b9-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
