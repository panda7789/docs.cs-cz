---
title: "MDAInfo – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: MDAInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: MDAInfo
helpviewer_keywords: MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 53a999028f2677599598caf55e62f10721f61fe3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mdainfo-structure"></a><span data-ttu-id="7bee7-102">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="7bee7-102">MDAInfo Structure</span></span>
<span data-ttu-id="7bee7-103">Poskytuje podrobnosti o `Event_MDAFired` událost, která aktivuje vytvoření Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="7bee7-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bee7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bee7-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="7bee7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7bee7-105">Members</span></span>  
  
|<span data-ttu-id="7bee7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7bee7-106">Member</span></span>|<span data-ttu-id="7bee7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7bee7-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="7bee7-108">Název aktuální (mda).</span><span class="sxs-lookup"><span data-stu-id="7bee7-108">The title of the current MDA.</span></span> <span data-ttu-id="7bee7-109">Nadpis popisuje typ selhání, který aktivoval `Event_MDAFired` událostí.</span><span class="sxs-lookup"><span data-stu-id="7bee7-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="7bee7-110">Výstup zpráva, která poskytuje aktuální (mda).</span><span class="sxs-lookup"><span data-stu-id="7bee7-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bee7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bee7-111">Remarks</span></span>  
 <span data-ttu-id="7bee7-112">Pomocníci spravovaného ladění (mda) jsou ladění pomůcek, které spolupracují se modul CLR (CLR) k provádění úloh, jako je identifikace neplatný podmínky v modulu runtime provádění nebo vypsání Další informace o stavu modul.</span><span class="sxs-lookup"><span data-stu-id="7bee7-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="7bee7-113">Mda generování zpráv XML o událostech, které jsou jinak obtížné depeše.</span><span class="sxs-lookup"><span data-stu-id="7bee7-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="7bee7-114">Jsou užitečné zejména pro ladění přechodů mezi spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="7bee7-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="7bee7-115">Modul runtime provede následující kroky, když je aktivována událost, která aktivuje vytvoření (mda):</span><span class="sxs-lookup"><span data-stu-id="7bee7-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="7bee7-116">Pokud hostitel není registrován [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance voláním [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) upozornit `Event_MDAFired` události modulu runtime pokračuje v jeho výchozí chování bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="7bee7-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="7bee7-117">Pokud hostitel zaregistrovala obslužnou rutinu pro tuto událost, modul runtime zkontroluje, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="7bee7-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="7bee7-118">Pokud se jedná, modul runtime dělí do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="7bee7-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="7bee7-119">Když ladicí program dál, zavolá do hostitele.</span><span class="sxs-lookup"><span data-stu-id="7bee7-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="7bee7-120">Pokud je připojen ladicí žádné program, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předá ukazatel na `MDAInfo` instance jako `data` parametr.</span><span class="sxs-lookup"><span data-stu-id="7bee7-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="7bee7-121">Hostiteli můžete k aktivaci mda a chcete být upozorněni, když se aktivuje (mda).</span><span class="sxs-lookup"><span data-stu-id="7bee7-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="7bee7-122">To dává příležitost přepsat výchozí chování a abort spravované vlákno, které vyvolá událost, aby zabránil jeho poškozování stavu procesu hostitele.</span><span class="sxs-lookup"><span data-stu-id="7bee7-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="7bee7-123">Další informace o používání mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="7bee7-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bee7-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bee7-124">Requirements</span></span>  
 <span data-ttu-id="7bee7-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bee7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bee7-126">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7bee7-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7bee7-127">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bee7-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bee7-128">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bee7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bee7-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bee7-129">See Also</span></span>  
 [<span data-ttu-id="7bee7-130">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="7bee7-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="7bee7-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="7bee7-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
