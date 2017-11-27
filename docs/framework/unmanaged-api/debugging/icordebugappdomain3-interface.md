---
title: "ICorDebugAppDomain3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3
helpviewer_keywords: ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 08f125d7fc388a9b2d31c9cc1cebf2605ffa7e23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="24e73-102">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24e73-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="24e73-103">Poskytuje metody k načtení informací o spravovaných reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy momentálně načtených v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="24e73-103">Provides methods to retrieve information about the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in an application domain.</span></span> <span data-ttu-id="24e73-104">Toto rozhraní je rozšířením ICorDebugAppDomain a icordebugappdomain2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="24e73-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24e73-105">Metody</span><span class="sxs-lookup"><span data-stu-id="24e73-105">Methods</span></span>  
  
|<span data-ttu-id="24e73-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="24e73-106">Method</span></span>|<span data-ttu-id="24e73-107">Popis</span><span class="sxs-lookup"><span data-stu-id="24e73-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24e73-108">Icordebugappdomain3::getcachedwinrttypes –</span><span class="sxs-lookup"><span data-stu-id="24e73-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="24e73-109">Získá enumerátor pro všechny uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy.</span><span class="sxs-lookup"><span data-stu-id="24e73-109">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>|  
|[<span data-ttu-id="24e73-110">Icordebugappdomain3::getcachedwinrttypesforiids –</span><span class="sxs-lookup"><span data-stu-id="24e73-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="24e73-111">Získá enumerátor pro uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v doméně aplikace podle jejich identifikátory rozhraní.</span><span class="sxs-lookup"><span data-stu-id="24e73-111">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24e73-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24e73-112">Remarks</span></span>  
 <span data-ttu-id="24e73-113">Toto rozhraní je určen pro použití ve ladicí program ve spojení s vyhodnocení volání funkce `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="24e73-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="24e73-114">Když metoda načte identifikátory rozhraní nepodporuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] objektu serveru ladicí program může používat metody definované v tomto rozhraní mapování na spravované typy, které odpovídají těchto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="24e73-114">When the method retrieves the interface identifiers supported by a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="24e73-115">Chcete-li načíst instanci tohoto rozhraní, spusťte `QueryInterface` v instanci ICorDebugAppDomain nebo icordebugappdomain2 – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="24e73-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24e73-116">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="24e73-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e73-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24e73-117">Requirements</span></span>  
 <span data-ttu-id="24e73-118">**Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e73-118">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="24e73-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24e73-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24e73-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24e73-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24e73-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24e73-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e73-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="24e73-122">See Also</span></span>  
 [<span data-ttu-id="24e73-123">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="24e73-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
