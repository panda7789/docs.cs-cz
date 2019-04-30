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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942542"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="aa857-102">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa857-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="aa857-103">Poskytuje enumerátor, který definuje mapování mezi sadou identifikátorů GUID a jejich odpovídající typy, které jsou znázorněny ICorDebugType instancí.</span><span class="sxs-lookup"><span data-stu-id="aa857-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="aa857-104">Toto rozhraní dědí z rozhraní ICorDebugEnum metody.</span><span class="sxs-lookup"><span data-stu-id="aa857-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa857-105">Metody</span><span class="sxs-lookup"><span data-stu-id="aa857-105">Methods</span></span>  
  
|<span data-ttu-id="aa857-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="aa857-106">Method</span></span>|<span data-ttu-id="aa857-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa857-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa857-108">Icordebugguidtotypeenum::Next –</span><span class="sxs-lookup"><span data-stu-id="aa857-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="aa857-109">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.</span><span class="sxs-lookup"><span data-stu-id="aa857-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa857-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa857-110">Remarks</span></span>  
 <span data-ttu-id="aa857-111">`ICorDebugGuidToTypeEnum` Objektu rozhraní může být načten voláním [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aa857-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="aa857-112">Ladicí program může volat toto rozhraní [Další](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodu pro načtení [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekty, které představují mapování ze spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] načíst typy v doména aplikace použít pro volání [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="aa857-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa857-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa857-113">Requirements</span></span>  
 <span data-ttu-id="aa857-114">**Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa857-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="aa857-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa857-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa857-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa857-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa857-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa857-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa857-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa857-118">See also</span></span>

- [<span data-ttu-id="aa857-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="aa857-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
