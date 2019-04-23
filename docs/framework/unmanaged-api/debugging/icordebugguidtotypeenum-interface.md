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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea67c6e4d860d41cfe67aaab73babb51f3ce45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210656"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="2e0e8-102">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e0e8-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="2e0e8-103">Poskytuje enumerátor, který definuje mapování mezi sadou identifikátorů GUID a jejich odpovídající typy, které jsou znázorněny ICorDebugType instancí.</span><span class="sxs-lookup"><span data-stu-id="2e0e8-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="2e0e8-104">Toto rozhraní dědí z rozhraní ICorDebugEnum metody.</span><span class="sxs-lookup"><span data-stu-id="2e0e8-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e0e8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2e0e8-105">Methods</span></span>  
  
|<span data-ttu-id="2e0e8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2e0e8-106">Method</span></span>|<span data-ttu-id="2e0e8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2e0e8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e0e8-108">Icordebugguidtotypeenum::Next –</span><span class="sxs-lookup"><span data-stu-id="2e0e8-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="2e0e8-109">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.</span><span class="sxs-lookup"><span data-stu-id="2e0e8-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e0e8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e0e8-110">Remarks</span></span>  
 <span data-ttu-id="2e0e8-111">`ICorDebugGuidToTypeEnum` Objektu rozhraní může být načten voláním [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2e0e8-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="2e0e8-112">Ladicí program může volat toto rozhraní [Další](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodu pro načtení [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekty, které představují mapování ze spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] načíst typy v doména aplikace použít pro volání [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2e0e8-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e0e8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e0e8-113">Requirements</span></span>  
 <span data-ttu-id="2e0e8-114">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0e8-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="2e0e8-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e0e8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e0e8-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e0e8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e0e8-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e0e8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e0e8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e0e8-118">See also</span></span>

- [<span data-ttu-id="2e0e8-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e0e8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
