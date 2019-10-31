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
ms.openlocfilehash: a5762079861f04e1869b206c3200c3a024c1b77a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091011"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="bd232-102">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd232-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="bd232-103">Rozšiřuje rozhraní "ICorDebugObjectValue", aby poskytovala informace o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="bd232-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd232-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd232-104">Methods</span></span>  
  
|<span data-ttu-id="bd232-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd232-105">Method</span></span>|<span data-ttu-id="bd232-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bd232-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd232-107">EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="bd232-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="bd232-108">Načte enumerátor do zásobníku volání vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="bd232-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd232-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd232-109">Remarks</span></span>  
 <span data-ttu-id="bd232-110">Volání `QueryInterface` bude úspěšné pro spravované objekty, které jsou odvozeny z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bd232-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd232-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd232-111">Requirements</span></span>  
 <span data-ttu-id="bd232-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd232-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd232-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bd232-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd232-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bd232-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd232-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd232-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd232-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd232-116">See also</span></span>

- [<span data-ttu-id="bd232-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bd232-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bd232-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="bd232-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
