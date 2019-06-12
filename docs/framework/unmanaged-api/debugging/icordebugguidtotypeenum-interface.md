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
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025823"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="b9261-102">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9261-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="b9261-103">Poskytuje enumerátor, který definuje mapování mezi sadou identifikátorů GUID a jejich odpovídající typy, které jsou znázorněny ICorDebugType instancí.</span><span class="sxs-lookup"><span data-stu-id="b9261-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="b9261-104">Toto rozhraní dědí z rozhraní ICorDebugEnum metody.</span><span class="sxs-lookup"><span data-stu-id="b9261-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9261-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b9261-105">Methods</span></span>  
  
|<span data-ttu-id="b9261-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b9261-106">Method</span></span>|<span data-ttu-id="b9261-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b9261-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9261-108">Icordebugguidtotypeenum::Next –</span><span class="sxs-lookup"><span data-stu-id="b9261-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="b9261-109">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které se mapují GUID informací o typu.</span><span class="sxs-lookup"><span data-stu-id="b9261-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9261-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9261-110">Remarks</span></span>  
 <span data-ttu-id="b9261-111">`ICorDebugGuidToTypeEnum` Objektu rozhraní může být načten voláním [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b9261-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="b9261-112">Ladicí program může volat toto rozhraní [Další](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodu pro načtení [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) načíst objekty, které představují mapování spravované reprezentace typů prostředí Windows Runtime v doména aplikace použít pro volání [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b9261-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9261-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9261-113">Requirements</span></span>  
 <span data-ttu-id="b9261-114">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="b9261-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="b9261-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9261-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9261-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9261-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9261-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9261-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9261-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9261-118">See also</span></span>

- [<span data-ttu-id="b9261-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b9261-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
