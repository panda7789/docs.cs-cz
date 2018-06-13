---
title: CLR_DEBUGGING_PROCESS_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dff6b245c80050a5e85561b8bba6aa9ba8199ba8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407063"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="13d8d-102">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="13d8d-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="13d8d-103">Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="13d8d-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13d8d-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="13d8d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="13d8d-105">Members</span></span>  
  
|<span data-ttu-id="13d8d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="13d8d-106">Member</span></span>|<span data-ttu-id="13d8d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="13d8d-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="13d8d-108">Tento modul runtime má událostí catch až spravované ladicí program k odeslání.</span><span class="sxs-lookup"><span data-stu-id="13d8d-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="13d8d-109">Naleznete v části poznámky o rozdíl mezi událostmi opravný a catch nahoru.</span><span class="sxs-lookup"><span data-stu-id="13d8d-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="13d8d-110">Spravované událost, která čeká na vyřízení je <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> požadavku.</span><span class="sxs-lookup"><span data-stu-id="13d8d-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13d8d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13d8d-111">Remarks</span></span>  
 <span data-ttu-id="13d8d-112">Zachytávání událostí zahrnují procesu, doménu aplikace, sestavení, modulu a oznámení vytvoření přístup z více vláken, která vrátí ladicího programu až do aktuálního stavu po má připojit k procesu.</span><span class="sxs-lookup"><span data-stu-id="13d8d-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="13d8d-113">Události bez catch-up, která jsou zobrazena `CLR_DEBUGGING_MANAGED_EVENT_PENDING` příznak, zahrnují všechny ostatní události ladicí program, jako je například výjimky a spravovaného ladění (MDA) pomocníka oznámení.</span><span class="sxs-lookup"><span data-stu-id="13d8d-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="13d8d-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Příznak umožňuje modulu runtime rozlišit mezi ukončující výjimce a požadavek na připojení spravované ladicí program, který může být zrušen.</span><span class="sxs-lookup"><span data-stu-id="13d8d-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13d8d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13d8d-115">Requirements</span></span>  
 <span data-ttu-id="13d8d-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13d8d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13d8d-117">**Záhlaví:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="13d8d-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="13d8d-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13d8d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13d8d-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13d8d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13d8d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="13d8d-120">See Also</span></span>  
 [<span data-ttu-id="13d8d-121">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="13d8d-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="13d8d-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="13d8d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
