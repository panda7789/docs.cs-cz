---
title: MDAInfo – struktura
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
ms.openlocfilehash: 33b3044c7b5237e586fdb993a16b6144c271782c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007712"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="4ffb8-102">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="4ffb8-102">MDAInfo Structure</span></span>
<span data-ttu-id="4ffb8-103">Poskytuje podrobnosti o `Event_MDAFired` události, které aktivují vytváření pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="4ffb8-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ffb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ffb8-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="4ffb8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4ffb8-105">Members</span></span>  
  
|<span data-ttu-id="4ffb8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4ffb8-106">Member</span></span>|<span data-ttu-id="4ffb8-107">Description</span><span class="sxs-lookup"><span data-stu-id="4ffb8-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="4ffb8-108">Název aktuální aplikace MDA</span><span class="sxs-lookup"><span data-stu-id="4ffb8-108">The title of the current MDA.</span></span> <span data-ttu-id="4ffb8-109">Nadpis popisuje druh selhání, který spustil `Event_MDAFired` událost.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="4ffb8-110">Výstupní zpráva poskytnutá aktuálním modulem MDA.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ffb8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ffb8-111">Remarks</span></span>  
 <span data-ttu-id="4ffb8-112">Asistenti spravovaného ladění (MDA) jsou pomocné pomůcky, které fungují ve spojení s modulem CLR (Common Language Runtime) k provádění úloh, jako je určení neplatných podmínek v modulu provádění modulu runtime nebo výpisu dalších informací o stavu modulu.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="4ffb8-113">MDA vygeneruje zprávy XML o událostech, které jsou jinak obtížné depeše.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="4ffb8-114">Jsou zvláště užitečné pro ladění přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="4ffb8-115">Modul runtime provede následující kroky, pokud je vyvolána událost, která spustí vytvoření objektu MDA:</span><span class="sxs-lookup"><span data-stu-id="4ffb8-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="4ffb8-116">Pokud hostitel nezaregistroval instanci [IActionOnCLREvent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) voláním [ICLROnEventManager:: RegisterActionOnEvent –](iclroneventmanager-registeractiononevent-method.md) , aby mohl být upozorněn na `Event_MDAFired` událost, modul runtime pokračuje s výchozím chováním, které nehostuje.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="4ffb8-117">Pokud hostitel zaregistroval obslužnou rutinu pro tuto událost, modul runtime zkontroluje, zda je k procesu připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="4ffb8-118">V takovém případě je modul runtime rozdělen do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="4ffb8-119">V případě, že ladicí program pokračuje, volá do hostitele.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="4ffb8-120">Pokud není připojen ladicí program, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předá ukazatel na `MDAInfo` instanci jako `data` parametr.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="4ffb8-121">Hostitel se může rozhodnout aktivovat MDA a upozornit na aktivaci služby MDA.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="4ffb8-122">Díky tomu může hostitel příležitost přepsat výchozí chování a přerušit spravované vlákno, které událost vyvolalo, aby nedošlo k poškození stavu procesu.</span><span class="sxs-lookup"><span data-stu-id="4ffb8-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="4ffb8-123">Další informace o použití MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="4ffb8-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ffb8-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ffb8-124">Requirements</span></span>  
 <span data-ttu-id="4ffb8-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ffb8-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ffb8-126">**Hlavička:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="4ffb8-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="4ffb8-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ffb8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ffb8-128">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ffb8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ffb8-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ffb8-129">See also</span></span>

- [<span data-ttu-id="4ffb8-130">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="4ffb8-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="4ffb8-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="4ffb8-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
