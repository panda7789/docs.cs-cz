---
title: "Icordebugappdomain2 – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c811107fcf32696aee17810af06ac0b2ddc9102d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="9de50-102">Icordebugappdomain2 – Interface1</span><span class="sxs-lookup"><span data-stu-id="9de50-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="9de50-103">Poskytuje metody pro práci s pole, ukazatelů, ukazatelů na funkce a odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="9de50-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="9de50-104">Toto rozhraní je rozšíření rozhraní ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="9de50-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9de50-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9de50-105">Methods</span></span>  
  
|<span data-ttu-id="9de50-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9de50-106">Method</span></span>|<span data-ttu-id="9de50-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9de50-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9de50-108">GetArrayOrPointerType – metoda</span><span class="sxs-lookup"><span data-stu-id="9de50-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="9de50-109">Získá zadaný typ, nebo ukazatel nebo odkaz na zadaný typ pole.</span><span class="sxs-lookup"><span data-stu-id="9de50-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="9de50-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="9de50-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="9de50-111">Získá ukazatel na funkci, která má daný podpis.</span><span class="sxs-lookup"><span data-stu-id="9de50-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9de50-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9de50-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9de50-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9de50-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9de50-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9de50-114">Requirements</span></span>  
 <span data-ttu-id="9de50-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9de50-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9de50-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9de50-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9de50-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9de50-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9de50-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9de50-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de50-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9de50-119">See Also</span></span>  
 [<span data-ttu-id="9de50-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9de50-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
