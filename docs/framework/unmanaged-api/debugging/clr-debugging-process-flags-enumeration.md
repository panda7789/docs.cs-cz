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
ms.openlocfilehash: 8321e5aeba435ca5f1398a9cb827a93ae821d686
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217325"
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="795d0-102">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="795d0-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="795d0-103">Obsahuje hodnoty, které jsou používány [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="795d0-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="795d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="795d0-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="795d0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="795d0-105">Members</span></span>  
  
|<span data-ttu-id="795d0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="795d0-106">Member</span></span>|<span data-ttu-id="795d0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="795d0-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="795d0-108">Tento modul runtime dojde k události catch nahoru spravovanému ladicímu programu k odeslání.</span><span class="sxs-lookup"><span data-stu-id="795d0-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="795d0-109">Rozdíl mezi událostmi catch nahoru a hned v části poznámky.</span><span class="sxs-lookup"><span data-stu-id="795d0-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="795d0-110">Je spravovaná událost, která čeká na vyřízení <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> požadavku.</span><span class="sxs-lookup"><span data-stu-id="795d0-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="795d0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="795d0-111">Remarks</span></span>  
 <span data-ttu-id="795d0-112">Zachytávání událostí zahrnují procesu, aplikační domény, sestavení, modulu a oznámení o vytvoření vlákna, přinášející ladicí program až do aktuálního stavu po má připojení k procesu.</span><span class="sxs-lookup"><span data-stu-id="795d0-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="795d0-113">Non-catch-up události, které jsou označeny `CLR_DEBUGGING_MANAGED_EVENT_PENDING` příznak, zahrnují všechny další události ladicího programu, jako jsou například výjimky a spravovaného ladění (MDA) pomocníka s nastavením oznámení.</span><span class="sxs-lookup"><span data-stu-id="795d0-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="795d0-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Příznak umožňuje modulu runtime rozlišovat mezi ukončující výjimce a žádost o připojení spravovaného ladicího programu, který může být zrušen.</span><span class="sxs-lookup"><span data-stu-id="795d0-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="795d0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="795d0-115">Requirements</span></span>  
 <span data-ttu-id="795d0-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="795d0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="795d0-117">**Záhlaví:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="795d0-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="795d0-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="795d0-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="795d0-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="795d0-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="795d0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="795d0-120">See also</span></span>

- [<span data-ttu-id="795d0-121">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="795d0-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="795d0-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="795d0-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
