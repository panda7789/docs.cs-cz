---
title: ICorDebugExceptionObjectValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5328442ceaee05b3f81466b785f04a361d456a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098478"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="9f2d0-102">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f2d0-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="9f2d0-103">Rozšiřuje rozhraní "ICorDebugObjectValue" k poskytnutí informací o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="9f2d0-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f2d0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9f2d0-104">Methods</span></span>  
  
|<span data-ttu-id="9f2d0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9f2d0-105">Method</span></span>|<span data-ttu-id="9f2d0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9f2d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f2d0-107">EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="9f2d0-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="9f2d0-108">Získá enumerátor pro zásobník volání, které jsou součástí objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="9f2d0-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f2d0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f2d0-109">Remarks</span></span>  
 <span data-ttu-id="9f2d0-110">Volání `QueryInterface` bude úspěšné pro spravované objekty, které jsou odvozeny z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9f2d0-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f2d0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f2d0-111">Requirements</span></span>  
 <span data-ttu-id="9f2d0-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f2d0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f2d0-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f2d0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f2d0-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f2d0-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9f2d0-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9f2d0-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f2d0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f2d0-116">See also</span></span>

- [<span data-ttu-id="9f2d0-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f2d0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9f2d0-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="9f2d0-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
