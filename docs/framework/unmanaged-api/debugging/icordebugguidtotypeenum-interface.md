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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138535"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="deb11-102">ICorDebugGuidToTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="deb11-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="deb11-103">Poskytuje enumerátor definující mapování mezi sadou identifikátorů GUID a jejich odpovídajícími typy, které jsou reprezentovány instancemi ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="deb11-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="deb11-104">Toto rozhraní dědí metody z rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="deb11-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="deb11-105">Metody</span><span class="sxs-lookup"><span data-stu-id="deb11-105">Methods</span></span>  
  
|<span data-ttu-id="deb11-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="deb11-106">Method</span></span>|<span data-ttu-id="deb11-107">Popis</span><span class="sxs-lookup"><span data-stu-id="deb11-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="deb11-108">ICorDebugGuidToTypeEnum –:: Next</span><span class="sxs-lookup"><span data-stu-id="deb11-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="deb11-109">Získá zadaný počet instancí [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , které mapují identifikátory GUID na informace typu.</span><span class="sxs-lookup"><span data-stu-id="deb11-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="deb11-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="deb11-110">Remarks</span></span>  
 <span data-ttu-id="deb11-111">Objekt rozhraní `ICorDebugGuidToTypeEnum` lze načíst voláním metody [ICorDebugAppDomain3:: GetCachedWinRTTypes –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="deb11-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="deb11-112">Ladicí program může zavolat [následující](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodu rozhraní k načtení objektů [CorDebugGuidToTypeMapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , které představují mapování spravovaných typů prostředí Windows Runtimeů načtených v doméně aplikace používané pro volání [ ICorDebugAppDomain3:: GetCachedWinRTTypes – –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metoda</span><span class="sxs-lookup"><span data-stu-id="deb11-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deb11-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="deb11-113">Requirements</span></span>  
 <span data-ttu-id="deb11-114">**Platformy:** prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="deb11-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="deb11-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="deb11-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="deb11-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="deb11-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="deb11-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deb11-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deb11-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="deb11-118">See also</span></span>

- [<span data-ttu-id="deb11-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="deb11-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
