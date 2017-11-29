---
title: "Icordebughandlevalue – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b56c23caaaed2bc63c724769db1198fd088f7f1a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="48dbc-102">Icordebughandlevalue – Interface1</span><span class="sxs-lookup"><span data-stu-id="48dbc-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="48dbc-103">Podtřídou třídy ICorDebugReferenceValue, který představuje hodnotu odkaz, ke kterému ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="48dbc-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48dbc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="48dbc-104">Methods</span></span>  
  
|<span data-ttu-id="48dbc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="48dbc-105">Method</span></span>|<span data-ttu-id="48dbc-106">Popis</span><span class="sxs-lookup"><span data-stu-id="48dbc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48dbc-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="48dbc-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="48dbc-108">Uvolní popisovač odkazuje toto `ICorDebugHandleValue` objekt explicitně stisknutým ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="48dbc-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="48dbc-109">Gethandletype – metoda</span><span class="sxs-lookup"><span data-stu-id="48dbc-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="48dbc-110">Získá hodnotu CorDebugHandleType, která popisuje typ popisovače odkazuje toto `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="48dbc-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48dbc-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48dbc-111">Remarks</span></span>  
 <span data-ttu-id="48dbc-112">`ICorDebugReferenceValue` Objekt zneplatněna mezerou v provádění vyladěnou kódu.</span><span class="sxs-lookup"><span data-stu-id="48dbc-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="48dbc-113">`ICorDebugHandleValue` Udržuje odkaz na jeho prostřednictvím zalomení a pokračování, dokud ji explicitně vydání.</span><span class="sxs-lookup"><span data-stu-id="48dbc-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48dbc-114">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="48dbc-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48dbc-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48dbc-115">Requirements</span></span>  
 <span data-ttu-id="48dbc-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48dbc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48dbc-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48dbc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48dbc-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48dbc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48dbc-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48dbc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48dbc-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="48dbc-120">See Also</span></span>  
 [<span data-ttu-id="48dbc-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="48dbc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
