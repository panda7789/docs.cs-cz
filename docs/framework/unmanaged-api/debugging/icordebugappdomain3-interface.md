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
ms.openlocfilehash: 1aaccb37ec61ed1ba6a7e6e1f508704973117cca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784887"
---
# <a name="icordebugappdomain3-interface"></a><span data-ttu-id="e81b5-102">ICorDebugAppDomain3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e81b5-102">ICorDebugAppDomain3 Interface</span></span>
<span data-ttu-id="e81b5-103">Poskytuje metody pro načtení informací o spravovaných reprezentace prostředí Windows Runtime typů, které jsou aktuálně načteny v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e81b5-103">Provides methods to retrieve information about the managed representations of Windows Runtime types currently loaded in an application domain.</span></span> <span data-ttu-id="e81b5-104">Toto rozhraní je rozšířením rozhraní ICorDebugAppDomain a ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="e81b5-104">This interface is an extension of the ICorDebugAppDomain and ICorDebugAppDomain2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e81b5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e81b5-105">Methods</span></span>  
  
|<span data-ttu-id="e81b5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e81b5-106">Method</span></span>|<span data-ttu-id="e81b5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e81b5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e81b5-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="e81b5-108">ICorDebugAppDomain3::GetCachedWinRTTypes</span></span>](icordebugappdomain3-getcachedwinrttypes-method.md)|<span data-ttu-id="e81b5-109">Získá enumerátor pro všechny typy prostředí Windows Runtime v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e81b5-109">Gets an enumerator for all cached Windows Runtime types.</span></span>|  
|[<span data-ttu-id="e81b5-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="e81b5-110">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span></span>](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|<span data-ttu-id="e81b5-111">Načte enumerátor pro prostředí Windows Runtime typy v mezipaměti aplikace na základě jejich identifikátorů rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e81b5-111">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e81b5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e81b5-112">Remarks</span></span>  
 <span data-ttu-id="e81b5-113">Toto rozhraní je určeno pro použití ladicím programem ve spojení se voláním vyhodnocení funkce pro `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span><span class="sxs-lookup"><span data-stu-id="e81b5-113">This interface is meant to be used by a debugger in conjunction with a function evaluation call to `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`.</span></span> <span data-ttu-id="e81b5-114">Když metoda načte identifikátory rozhraní podporované objektem prostředí Windows Runtime serveru, ladicí program může použít metody definované v tomto rozhraní k namapování na spravované typy, které odpovídají těmto rozhraním.</span><span class="sxs-lookup"><span data-stu-id="e81b5-114">When the method retrieves the interface identifiers supported by a Windows Runtime server object, the debugger may use the methods defined in this interface to map them to managed types that correspond to those interfaces.</span></span>  
  
 <span data-ttu-id="e81b5-115">Chcete-li načíst instanci tohoto rozhraní, spusťte `QueryInterface` v instanci rozhraní ICorDebugAppDomain nebo ICorDebugAppDomain2.</span><span class="sxs-lookup"><span data-stu-id="e81b5-115">To retrieve an instance of this interface, run `QueryInterface` on an instance of the ICorDebugAppDomain or ICorDebugAppDomain2 interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e81b5-116">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e81b5-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e81b5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e81b5-117">Requirements</span></span>  
 <span data-ttu-id="e81b5-118">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="e81b5-118">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="e81b5-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e81b5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e81b5-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e81b5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e81b5-121">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e81b5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e81b5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e81b5-122">See also</span></span>

- [<span data-ttu-id="e81b5-123">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e81b5-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
