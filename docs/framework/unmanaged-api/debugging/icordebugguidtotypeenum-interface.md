---
title: "ICorDebugGuidToTypeEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum
helpviewer_keywords: ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9993a5aaaef3d5b83d21e3641029af12119188da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="fb96f-102">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb96f-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="fb96f-103">Poskytuje enumerátor, který definuje mapování mezi sadu identifikátory GUID a jejich odpovídající typy, které jsou reprezentované pomocí ICorDebugType instance.</span><span class="sxs-lookup"><span data-stu-id="fb96f-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="fb96f-104">Toto rozhraní dědí z rozhraní ICorDebugEnum metody.</span><span class="sxs-lookup"><span data-stu-id="fb96f-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb96f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fb96f-105">Methods</span></span>  
  
|<span data-ttu-id="fb96f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fb96f-106">Method</span></span>|<span data-ttu-id="fb96f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fb96f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb96f-108">Icordebugguidtotypeenum::Next –</span><span class="sxs-lookup"><span data-stu-id="fb96f-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="fb96f-109">Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které mapují identifikátory GUID na typ informace.</span><span class="sxs-lookup"><span data-stu-id="fb96f-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb96f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb96f-110">Remarks</span></span>  
 <span data-ttu-id="fb96f-111">`ICorDebugGuidToTypeEnum` Objekt rozhraní můžete načíst pomocí volání [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="fb96f-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="fb96f-112">Ladicí program můžete volat toto rozhraní [Další](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metoda pro načtení [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) spravované objekty, které představují mapování reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] načíst typy v doména aplikace použít pro volání [icordebugappdomain3::getcachedwinrttypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="fb96f-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb96f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb96f-113">Requirements</span></span>  
 <span data-ttu-id="fb96f-114">**Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb96f-114">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="fb96f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fb96f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb96f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb96f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb96f-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb96f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb96f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb96f-118">See Also</span></span>  
 [<span data-ttu-id="fb96f-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fb96f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
