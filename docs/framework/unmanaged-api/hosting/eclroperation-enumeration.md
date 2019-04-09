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
ms.openlocfilehash: 7d5f24d7415ff7ecceba6b0a5fbd3098d70dcd0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190350"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="d3ebf-102">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="d3ebf-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="d3ebf-103">Popisuje sadu operací, u které můžete použít hostitele akce zásad.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ebf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3ebf-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d3ebf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d3ebf-105">Members</span></span>  
  
|<span data-ttu-id="d3ebf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d3ebf-106">Member</span></span>|<span data-ttu-id="d3ebf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d3ebf-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="d3ebf-108">Hostitele můžete určit akce zásad, které mají být provedeny, když <xref:System.AppDomain> uvolnění způsobem řádné (pravidla).</span><span class="sxs-lookup"><span data-stu-id="d3ebf-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="d3ebf-109">Hostitele můžete určit akce zásad, které mají být provedeny, když <xref:System.AppDomain> je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="d3ebf-110">Hostitele můžete určit akce zásad, které mají být provedeny, když spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="d3ebf-111">Hostitele můžete určit akce zásad, které mají být provedeny při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="d3ebf-112">Hostitele můžete určit akce zásad, které mají být provedeny, když je přerušeno vlákno.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="d3ebf-113">Hostitele můžete určit akce zásad, které mají být provedeny, když dojde k přerušení článku neslušní vlákna v důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="d3ebf-114">Hostitele můžete určit akce zásad má provést, když dojde k přerušení článku neslušní vlákna v méně důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3ebf-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3ebf-115">Remarks</span></span>  
 <span data-ttu-id="d3ebf-116">Common language runtime (CLR) spolehlivost infrastructure rozlišuje mezi přeruší a prostředků, ke kterým dochází v důležité oblasti kódu a těch, ke kterým dochází v méně důležité oblasti kódu chyby v přidělení.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="d3ebf-117">Toto rozlišení je navržena k umožnění hostitelů nastavit různé zásady v závislosti na tom, kde dojde k chybě v kódu.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="d3ebf-118">A *důležité oblasti kódu* je jakýkoli prostor, kde nemůže zaručit CLR dané přeruší úlohu nebo selhání žádost pro prostředky ovlivní pouze aktuální úloha dokončí.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="d3ebf-119">Například pokud úloha drží zámek a přijímá HRESULT označující selhání při vytváření požadavku přidělení paměti, je jednoduše k přerušení tento úkol zajistit stabilitu <xref:System.AppDomain>, protože <xref:System.AppDomain> může obsahovat jiné Čekání na zámek stejné úkoly.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="d3ebf-120">Pokud chcete opustit aktuální úloha může způsobit, že ty další úlohy přestane reagovat (nebo přestane reagovat) po neomezenou dobu.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="d3ebf-121">V takovém případě hostitele musí být schopné uvolnit celý <xref:System.AppDomain> místo nestabilitu potenciální riziko.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="d3ebf-122">A *méně důležité oblasti kódu*, na druhé straně je oblast, ve kterém CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohy, na kterém dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="d3ebf-123">CLR také rozlišuje mezi bezproblémové a jiné řádné přerušení (pravidla).</span><span class="sxs-lookup"><span data-stu-id="d3ebf-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="d3ebf-124">Obecně platí normální nebo řádné přerušení snaží spustit před přerušením úlohy, zatímco hrubé přerušení nezaručuje tyto rutiny zpracování výjimek a finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="d3ebf-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3ebf-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3ebf-125">Requirements</span></span>  
 <span data-ttu-id="d3ebf-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3ebf-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ebf-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3ebf-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3ebf-128">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3ebf-128">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d3ebf-129">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d3ebf-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d3ebf-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3ebf-130">See also</span></span>

- [<span data-ttu-id="d3ebf-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="d3ebf-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="d3ebf-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="d3ebf-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="d3ebf-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3ebf-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d3ebf-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d3ebf-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="d3ebf-135">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="d3ebf-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
