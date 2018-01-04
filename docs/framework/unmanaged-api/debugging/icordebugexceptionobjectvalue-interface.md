---
title: "ICorDebugExceptionObjectValue – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6ee743a5e3e28b5d8b864f325239725ca6c0042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="2df79-102">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df79-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="2df79-103">Rozšiřuje rozhraní "ICorDebugObjectValue" poskytnout informace trasování zásobníku z objektu spravovaného výjimka.</span><span class="sxs-lookup"><span data-stu-id="2df79-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2df79-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2df79-104">Methods</span></span>  
  
|<span data-ttu-id="2df79-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2df79-105">Method</span></span>|<span data-ttu-id="2df79-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2df79-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2df79-107">EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="2df79-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="2df79-108">Získá enumerátor do zásobníku volání vložených v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="2df79-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2df79-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2df79-109">Remarks</span></span>  
 <span data-ttu-id="2df79-110">Volání `QueryInterface` bude úspěšné pro spravované objekty, které jsou odvozeny od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2df79-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df79-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2df79-111">Requirements</span></span>  
 <span data-ttu-id="2df79-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df79-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2df79-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2df79-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df79-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df79-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df79-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2df79-116">See Also</span></span>  
 [<span data-ttu-id="2df79-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2df79-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2df79-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="2df79-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
