---
title: ICorDebugGuidToTypeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 2663e5604cdd55472cc148b2d2b38599df81f11e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794443"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="144e7-102">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="144e7-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="144e7-103">Poskytuje enumerátor definující mapování mezi sadou identifikátorů GUID a jejich odpovídajícími typy, které jsou reprezentovány instancemi ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="144e7-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="144e7-104">Toto rozhraní dědí metody z rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="144e7-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="144e7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="144e7-105">Methods</span></span>  
  
|<span data-ttu-id="144e7-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="144e7-106">Method</span></span>|<span data-ttu-id="144e7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="144e7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="144e7-108">ICorDebugGuidToTypeEnum –:: Next</span><span class="sxs-lookup"><span data-stu-id="144e7-108">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="144e7-109">Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.</span><span class="sxs-lookup"><span data-stu-id="144e7-109">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="144e7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="144e7-110">Remarks</span></span>  
 <span data-ttu-id="144e7-111">Objekt rozhraní `ICorDebugGuidToTypeEnum` lze načíst voláním metody [ICorDebugAppDomain3:: GetCachedWinRTTypes –](icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="144e7-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="144e7-112">Ladicí program může zavolat metodu [Next](icordebugguidtotypeenum-next-method.md) tohoto rozhraní k načtení objektů [CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) , které představují mapování spravovaných typů prostředí Windows Runtimeů načtených v doméně aplikace používané pro volání metody [ICorDebugAppDomain3:: GetCachedWinRTTypes –](icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="144e7-112">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144e7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="144e7-113">Requirements</span></span>  
 <span data-ttu-id="144e7-114">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="144e7-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="144e7-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="144e7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="144e7-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="144e7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="144e7-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144e7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144e7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="144e7-118">See also</span></span>

- [<span data-ttu-id="144e7-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="144e7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
