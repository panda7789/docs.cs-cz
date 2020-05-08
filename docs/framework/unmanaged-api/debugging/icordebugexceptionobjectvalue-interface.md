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
ms.openlocfilehash: 8e4f745440936a39e22faf60d10a05a0bb110606
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975950"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="3fba6-102">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fba6-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="3fba6-103">Rozšiřuje rozhraní "ICorDebugObjectValue", aby poskytovala informace o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="3fba6-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3fba6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3fba6-104">Methods</span></span>  
  
|<span data-ttu-id="3fba6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3fba6-105">Method</span></span>|<span data-ttu-id="3fba6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3fba6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3fba6-107">EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="3fba6-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="3fba6-108">Načte enumerátor do zásobníku volání vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="3fba6-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fba6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fba6-109">Remarks</span></span>  
 <span data-ttu-id="3fba6-110">Volání se `QueryInterface` bude podařit pro spravované objekty, které jsou <xref:System.Exception?displayProperty=nameWithType>odvozeny z.</span><span class="sxs-lookup"><span data-stu-id="3fba6-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fba6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fba6-111">Requirements</span></span>  
 <span data-ttu-id="3fba6-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fba6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fba6-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3fba6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fba6-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3fba6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fba6-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fba6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fba6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fba6-116">See also</span></span>

- [<span data-ttu-id="3fba6-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fba6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3fba6-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="3fba6-118">Debugging</span></span>](index.md)
