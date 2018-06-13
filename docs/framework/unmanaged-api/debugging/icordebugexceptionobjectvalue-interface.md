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
ms.openlocfilehash: d6805b7b49f76b80161aef5051fe3c284192f582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413771"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="e5607-102">ICorDebugExceptionObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5607-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="e5607-103">Rozšiřuje rozhraní "ICorDebugObjectValue" poskytnout informace trasování zásobníku z objektu spravovaného výjimka.</span><span class="sxs-lookup"><span data-stu-id="e5607-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5607-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e5607-104">Methods</span></span>  
  
|<span data-ttu-id="e5607-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e5607-105">Method</span></span>|<span data-ttu-id="e5607-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e5607-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5607-107">EnumerateExceptionCallStack – metoda</span><span class="sxs-lookup"><span data-stu-id="e5607-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="e5607-108">Získá enumerátor do zásobníku volání vložených v objektu výjimky.</span><span class="sxs-lookup"><span data-stu-id="e5607-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5607-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5607-109">Remarks</span></span>  
 <span data-ttu-id="e5607-110">Volání `QueryInterface` bude úspěšné pro spravované objekty, které jsou odvozeny od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5607-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5607-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5607-111">Requirements</span></span>  
 <span data-ttu-id="e5607-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5607-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5607-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5607-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5607-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5607-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5607-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5607-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5607-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5607-116">See Also</span></span>  
 [<span data-ttu-id="e5607-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e5607-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e5607-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="e5607-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
