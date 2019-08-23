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
ms.openlocfilehash: c3676cb32ceaf6f241672751f0feafbd3cb83e05
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968873"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="2d443-102">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d443-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="2d443-103">Poskytuje metody pro načtení informací o spravovaných reprezentace prostředí Windows Runtime typů, které jsou aktuálně načteny v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d443-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="2d443-104">Toto rozhraní je rozšířením rozhraní ICorDebugAppDomain a ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="2d443-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d443-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2d443-105">Methods</span></span>  
  
|<span data-ttu-id="2d443-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d443-106">Method</span></span>|<span data-ttu-id="2d443-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2d443-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d443-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="2d443-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="2d443-109">Získá enumerátor pro všechny typy prostředí Windows Runtime v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2d443-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="2d443-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="2d443-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="2d443-111">Načte enumerátor pro prostředí Windows Runtime typy v mezipaměti aplikace na základě jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2d443-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d443-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d443-112">Remarks</span></span>  
 <span data-ttu-id="2d443-113">Toto rozhraní je určeno pro použití ladicím programem ve spojení s voláním vyhodnocení funkce na `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="2d443-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="2d443-114">Když metoda načte identifikátory rozhraní podporované objektem prostředí Windows Runtime serveru, ladicí program může použít metody definované v tomto rozhraní k namapování na spravované typy, které odpovídají těmto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="2d443-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="2d443-115">Chcete-li načíst instanci tohoto rozhraní, spusťte `QueryInterface` rutinu v instanci rozhraní ICorDebugAppDomain nebo ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="2d443-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d443-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2d443-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d443-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d443-117">Requirements</span></span>  
 <span data-ttu-id="2d443-118">**Platformu** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="2d443-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="2d443-119">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d443-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d443-120">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d443-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d443-121">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d443-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d443-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d443-122">See also</span></span>

- [<span data-ttu-id="2d443-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d443-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
