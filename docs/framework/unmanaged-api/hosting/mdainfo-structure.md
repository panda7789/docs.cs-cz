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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: faa6af54714f7f0b7ac91c7836673c163195d5f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656461"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="15e3e-102">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="15e3e-102">MDAInfo Structure</span></span>
<span data-ttu-id="15e3e-103">Poskytuje podrobnosti o `Event_MDAFired` událost, která se aktivuje vytvořením Pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="15e3e-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15e3e-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="15e3e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="15e3e-105">Members</span></span>  
  
|<span data-ttu-id="15e3e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="15e3e-106">Member</span></span>|<span data-ttu-id="15e3e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="15e3e-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="15e3e-108">Název aktuální MDA.</span><span class="sxs-lookup"><span data-stu-id="15e3e-108">The title of the current MDA.</span></span> <span data-ttu-id="15e3e-109">Název popisuje typ selhání, které aktivuje `Event_MDAFired` událostí.</span><span class="sxs-lookup"><span data-stu-id="15e3e-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="15e3e-110">Výstupní zprávy poskytnuté aktuální MDA.</span><span class="sxs-lookup"><span data-stu-id="15e3e-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15e3e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15e3e-111">Remarks</span></span>  
 <span data-ttu-id="15e3e-112">Asistentů spravovaného ladění (mda) jsou pomůcky, které fungují ve spojení s common language runtime (CLR) k provádění úloh, jako je identifikace neplatné podmínky pro ladění v prováděcí modul runtime nebo vypsání Další informace o stavu modul.</span><span class="sxs-lookup"><span data-stu-id="15e3e-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="15e3e-113">Mda generování zpráv XML o událostech, které jsou jinak obtížné zachytit.</span><span class="sxs-lookup"><span data-stu-id="15e3e-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="15e3e-114">Jsou obzvláště užitečné pro ladění přechody mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="15e3e-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="15e3e-115">Modul runtime provede následující kroky, když se aktivuje událost, která se aktivuje vytvořením MDA:</span><span class="sxs-lookup"><span data-stu-id="15e3e-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="15e3e-116">Pokud nebyla zaregistrována hostitele [iactiononclrevent –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance voláním [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) upozornit `Event_MDAFired` události, modul runtime bude pokračovat jeho výchozí chování bez hostitele.</span><span class="sxs-lookup"><span data-stu-id="15e3e-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="15e3e-117">Pokud hostitel je zaregistrovaná obslužná rutina pro tuto událost, zkontroluje modulu runtime, zda je připojen ladicí program k procesu.</span><span class="sxs-lookup"><span data-stu-id="15e3e-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="15e3e-118">Pokud se jedná, modul runtime se dělí do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="15e3e-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="15e3e-119">Pokud ladicí program bude pokračovat, volá do hostitele.</span><span class="sxs-lookup"><span data-stu-id="15e3e-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="15e3e-120">Pokud je připojen ladicí program nebyl, modul runtime zavolá `IActionOnCLREvent::OnEvent` a předává ukazatel `MDAInfo` instance jako `data` parametr.</span><span class="sxs-lookup"><span data-stu-id="15e3e-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="15e3e-121">K aktivaci mda a která vás upozorní, když MDA aktivováno, můžete zvolit hostitele.</span><span class="sxs-lookup"><span data-stu-id="15e3e-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="15e3e-122">To dává možnost přepsat výchozí chování a na spravovaná vlákna, která vyvolala událost, chcete-li zabránit poškození stav procesu zrušení hostitele.</span><span class="sxs-lookup"><span data-stu-id="15e3e-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="15e3e-123">Další informace o používání mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="15e3e-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e3e-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15e3e-124">Requirements</span></span>  
 <span data-ttu-id="15e3e-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e3e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e3e-126">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="15e3e-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="15e3e-127">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15e3e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15e3e-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e3e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e3e-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15e3e-129">See also</span></span>

- [<span data-ttu-id="15e3e-130">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="15e3e-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="15e3e-131">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="15e3e-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
