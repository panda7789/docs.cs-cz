---
title: "EClrOperation – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="43d2a-102">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="43d2a-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="43d2a-103">Popisuje sadu operací, pro které můžete použít hostitele akce zásad.</span><span class="sxs-lookup"><span data-stu-id="43d2a-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43d2a-104">Syntax</span></span>  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="43d2a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="43d2a-105">Members</span></span>  
  
|<span data-ttu-id="43d2a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="43d2a-106">Member</span></span>|<span data-ttu-id="43d2a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="43d2a-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="43d2a-108">Hostitele můžete určit zásady akce, které mají být provedeny, když <xref:System.AppDomain> je odpojeno způsobem řádně (článku neslušní).</span><span class="sxs-lookup"><span data-stu-id="43d2a-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="43d2a-109">Hostitele můžete určit zásady akce, které mají být provedeny, když <xref:System.AppDomain> je odpojen.</span><span class="sxs-lookup"><span data-stu-id="43d2a-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="43d2a-110">Hostitele můžete zadat zásady akce prováděné při spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="43d2a-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="43d2a-111">Hostitele můžete určit zásady akce, které mají být provedeny, když proces bude ukončen.</span><span class="sxs-lookup"><span data-stu-id="43d2a-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="43d2a-112">Hostitele můžete určit zásady akce, které mají být provedeny, když byl přerušen vlákna.</span><span class="sxs-lookup"><span data-stu-id="43d2a-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="43d2a-113">Hostitele můžete určit zásady akce, které mají být provedeny, když dojde k přerušení článku neslušní vláken v kritické oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="43d2a-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="43d2a-114">Hostitele můžete určit zásady akce provést, když dojde k přerušení článku neslušní vláken v méně důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="43d2a-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43d2a-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43d2a-115">Remarks</span></span>  
 <span data-ttu-id="43d2a-116">Common language runtime (CLR) spolehlivost infrastructure rozlišuje mezi přerušení a prostředků, ke kterým došlo v kritické oblastech kódu a soubory, ke kterým došlo v oblasti nekritické kódu chyby v přidělení.</span><span class="sxs-lookup"><span data-stu-id="43d2a-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="43d2a-117">Tento rozdíl je navržena k umožnění hostitelů nastavit různé zásady v závislosti na tom, kde dojde k chybě v kódu.</span><span class="sxs-lookup"><span data-stu-id="43d2a-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="43d2a-118">A *kód důležité oblasti* je veškeré místo, kde modulu CLR nemůže zaručit, že přerušení úlohu nebo nedaří dokončit žádost o pro prostředky ovlivní pouze aktuální úlohy.</span><span class="sxs-lookup"><span data-stu-id="43d2a-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="43d2a-119">Například pokud úloha je zámek a dostane HRESULT označující selhání při vytváření požadavku přidělení paměti, je nedostatečné jednoduše na tento úkol zajistit stabilitu zrušení <xref:System.AppDomain>, protože <xref:System.AppDomain> může obsahovat jiné Čekání na zámek stejné úlohy.</span><span class="sxs-lookup"><span data-stu-id="43d2a-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="43d2a-120">Ukončil aktuální úloha může způsobit, že ty dalších úloh přestane reagovat (nebo zablokování) po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="43d2a-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="43d2a-121">V takovém případě musí hostitel znát schopnost uvolnit celý <xref:System.AppDomain> místo nestabilitu potenciální riziko.</span><span class="sxs-lookup"><span data-stu-id="43d2a-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="43d2a-122">A *nekritické kód oblasti*, na druhé straně je oblast, kde modulu CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohy, při kterém dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="43d2a-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="43d2a-123">Modul CLR také rozlišuje řádně a řádně přerušení (článku neslušní).</span><span class="sxs-lookup"><span data-stu-id="43d2a-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="43d2a-124">Obecně platí normální nebo řádně přerušení neustále snaží spustit rutiny zpracování výjimek a finalizační metody před ukončením úlohy, zatímco článku neslušní přerušení díky žádné záruky.</span><span class="sxs-lookup"><span data-stu-id="43d2a-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43d2a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43d2a-125">Requirements</span></span>  
 <span data-ttu-id="43d2a-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43d2a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43d2a-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43d2a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43d2a-128">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43d2a-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43d2a-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43d2a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43d2a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="43d2a-130">See Also</span></span>  
 [<span data-ttu-id="43d2a-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="43d2a-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="43d2a-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="43d2a-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="43d2a-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43d2a-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="43d2a-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43d2a-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="43d2a-135">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="43d2a-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
