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
ms.openlocfilehash: b9185600d9d8b2a33830d86642727ac54b87a9cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099647"
---
# <a name="clr_debugging_process_flags-enumeration"></a><span data-ttu-id="2e06c-102">CLR_DEBUGGING_PROCESS_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="2e06c-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="2e06c-103">Poskytuje hodnoty, které jsou používány metodou [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2e06c-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e06c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e06c-104">Syntax</span></span>  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2e06c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2e06c-105">Members</span></span>  
  
|<span data-ttu-id="2e06c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2e06c-106">Member</span></span>|<span data-ttu-id="2e06c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2e06c-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="2e06c-108">Tento modul runtime má k odeslání událost spravovaného ladicího programu bez zachycení.</span><span class="sxs-lookup"><span data-stu-id="2e06c-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="2e06c-109">V části poznámky najdete rozdíl mezi zachycenými a nezachycenými událostmi.</span><span class="sxs-lookup"><span data-stu-id="2e06c-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="2e06c-110">Spravovaná událost, která čeká na vyřízení, je <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> požadavek.</span><span class="sxs-lookup"><span data-stu-id="2e06c-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e06c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e06c-111">Remarks</span></span>  
 <span data-ttu-id="2e06c-112">Mezi zachycené události patří proces, aplikační doména, sestavení, modul a oznámení o vytvoření vlákna, které přinášejí ladicímu programu až do aktuálního stavu poté, co se připojí k procesu.</span><span class="sxs-lookup"><span data-stu-id="2e06c-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="2e06c-113">Nezachycené události, které jsou označeny příznakem `CLR_DEBUGGING_MANAGED_EVENT_PENDING`, zahrnují všechny další události ladicího programu, například výjimky a oznámení o spravovaném ladění pomocníka (MDA).</span><span class="sxs-lookup"><span data-stu-id="2e06c-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="2e06c-114">Příznak `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` umožňuje modulu runtime rozlišovat ukončující výjimku a požadavek na připojení spravovaného ladicího programu, který lze zrušit.</span><span class="sxs-lookup"><span data-stu-id="2e06c-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e06c-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e06c-115">Requirements</span></span>  
 <span data-ttu-id="2e06c-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e06c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e06c-117">**Hlavička:** Metahost. idl, Metahost. h</span><span class="sxs-lookup"><span data-stu-id="2e06c-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="2e06c-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e06c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e06c-119">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e06c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e06c-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e06c-120">See also</span></span>

- [<span data-ttu-id="2e06c-121">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e06c-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="2e06c-122">Ladění</span><span class="sxs-lookup"><span data-stu-id="2e06c-122">Debugging</span></span>](index.md)
