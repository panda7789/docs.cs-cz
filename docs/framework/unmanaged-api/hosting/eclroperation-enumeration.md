---
title: EClrOperation – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9bbff8bb1f095502f27b649639434010453ffe1
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423846"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="8c345-102">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="8c345-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="8c345-103">Popisuje sadu operací, u které můžete použít hostitele akce zásad.</span><span class="sxs-lookup"><span data-stu-id="8c345-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c345-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c345-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8c345-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8c345-105">Members</span></span>  
  
|<span data-ttu-id="8c345-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8c345-106">Member</span></span>|<span data-ttu-id="8c345-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8c345-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="8c345-108">Hostitele můžete určit akce zásad, které mají být provedeny, když <xref:System.AppDomain> uvolnění způsobem řádné (pravidla).</span><span class="sxs-lookup"><span data-stu-id="8c345-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="8c345-109">Hostitele můžete určit akce zásad, které mají být provedeny, když <xref:System.AppDomain> je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="8c345-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="8c345-110">Hostitele můžete určit akce zásad, které mají být provedeny, když spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="8c345-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="8c345-111">Hostitele můžete určit akce zásad, které mají být provedeny při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="8c345-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="8c345-112">Hostitele můžete určit akce zásad, které mají být provedeny, když je přerušeno vlákno.</span><span class="sxs-lookup"><span data-stu-id="8c345-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="8c345-113">Hostitele můžete určit akce zásad, které mají být provedeny, když dojde k přerušení článku neslušní vlákna v důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="8c345-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="8c345-114">Hostitele můžete určit akce zásad má provést, když dojde k přerušení článku neslušní vlákna v méně důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="8c345-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c345-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c345-115">Remarks</span></span>  
 <span data-ttu-id="8c345-116">Common language runtime (CLR) spolehlivost infrastructure rozlišuje mezi přeruší a prostředků, ke kterým dochází v důležité oblasti kódu a těch, ke kterým dochází v méně důležité oblasti kódu chyby v přidělení.</span><span class="sxs-lookup"><span data-stu-id="8c345-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="8c345-117">Toto rozlišení je navržena k umožnění hostitelů nastavit různé zásady v závislosti na tom, kde dojde k chybě v kódu.</span><span class="sxs-lookup"><span data-stu-id="8c345-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="8c345-118">A *důležité oblasti kódu* je jakýkoli prostor, kde nemůže zaručit CLR dané přeruší úlohu nebo selhání žádost pro prostředky ovlivní pouze aktuální úloha dokončí.</span><span class="sxs-lookup"><span data-stu-id="8c345-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="8c345-119">Například pokud úloha drží zámek a přijímá HRESULT označující selhání při vytváření požadavku přidělení paměti, je jednoduše k přerušení tento úkol zajistit stabilitu <xref:System.AppDomain>, protože <xref:System.AppDomain> může obsahovat jiné Čekání na zámek stejné úkoly.</span><span class="sxs-lookup"><span data-stu-id="8c345-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="8c345-120">Pokud chcete opustit aktuální úloha může způsobit tyto úlohy přestane reagovat.</span><span class="sxs-lookup"><span data-stu-id="8c345-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="8c345-121">V takovém případě hostitele musí být schopné uvolnit celý <xref:System.AppDomain> místo nestabilitu potenciální riziko.</span><span class="sxs-lookup"><span data-stu-id="8c345-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="8c345-122">A *méně důležité oblasti kódu*, na druhé straně je oblast, ve kterém CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohy, na kterém dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="8c345-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="8c345-123">CLR také rozlišuje mezi bezproblémové a jiné řádné přerušení (pravidla).</span><span class="sxs-lookup"><span data-stu-id="8c345-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="8c345-124">Obecně platí normální nebo řádné přerušení snaží spustit před přerušením úlohy, zatímco hrubé přerušení nezaručuje tyto rutiny zpracování výjimek a finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="8c345-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c345-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c345-125">Requirements</span></span>  
 <span data-ttu-id="8c345-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c345-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c345-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c345-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c345-128">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8c345-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c345-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c345-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c345-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c345-130">See also</span></span>

- [<span data-ttu-id="8c345-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="8c345-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="8c345-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="8c345-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="8c345-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c345-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="8c345-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c345-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="8c345-135">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="8c345-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
