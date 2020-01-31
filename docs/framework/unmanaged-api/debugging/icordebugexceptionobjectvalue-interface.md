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
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782737"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="05ade-102">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ade-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="05ade-103">Rozšiřuje rozhraní "ICorDebugObjectValue", aby poskytovala informace o trasování zásobníku z objektu spravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="05ade-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05ade-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05ade-104">Methods</span></span>  
  
|<span data-ttu-id="05ade-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05ade-105">Method</span></span>|<span data-ttu-id="05ade-106">Popis</span><span class="sxs-lookup"><span data-stu-id="05ade-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05ade-107">EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="05ade-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="05ade-108">Načte enumerátor do zásobníku volání vložený v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="05ade-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ade-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05ade-109">Remarks</span></span>  
 <span data-ttu-id="05ade-110">Volání `QueryInterface` bude úspěšné pro spravované objekty, které jsou odvozeny z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="05ade-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ade-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05ade-111">Requirements</span></span>  
 <span data-ttu-id="05ade-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ade-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ade-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05ade-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05ade-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05ade-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05ade-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ade-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ade-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05ade-116">See also</span></span>

- [<span data-ttu-id="05ade-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="05ade-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="05ade-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="05ade-118">Debugging</span></span>](index.md)
