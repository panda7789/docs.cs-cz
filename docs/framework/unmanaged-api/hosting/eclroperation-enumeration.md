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
ms.openlocfilehash: e7cb1c2070e760258e548d2f45e3b6ed11e046c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616317"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="9d6b1-102">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="9d6b1-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="9d6b1-103">Popisuje sadu operací, pro které může hostitel použít akce zásad.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6b1-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="9d6b1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9d6b1-105">Members</span></span>  
  
|<span data-ttu-id="9d6b1-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9d6b1-106">Member</span></span>|<span data-ttu-id="9d6b1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9d6b1-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="9d6b1-108">Hostitel může určit akce zásad, které se mají provést, když <xref:System.AppDomain> dojde k uvolnění v neúspěšném (hrubé) způsobu.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="9d6b1-109">Hostitel může určit akce zásad, které mají být provedeny při <xref:System.AppDomain> uvolnění.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="9d6b1-110">Hostitel může určit akce zásad, které se mají provést při spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="9d6b1-111">Hostitel může určit akce zásad, které mají být provedeny při ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="9d6b1-112">Hostitel může určit akce zásad, které se mají provést při přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="9d6b1-113">Hostitel může určit akce zásad, které mají být provedeny, když dojde k přerušení hrubé vlákna v kritické oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="9d6b1-114">Hostitel může určit akce zásad, které se mají provést, když dojde k přerušení hrubé vlákna v nekritické oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d6b1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d6b1-115">Remarks</span></span>  
 <span data-ttu-id="9d6b1-116">Infrastruktura spolehlivosti modulu CLR (Common Language Runtime) rozlišuje mezi přerušeními a selháním přidělení prostředků, ke kterým dochází v kritických oblastech kódu a těch, ke kterým dochází v nekritických oblastech kódu.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="9d6b1-117">Toto rozlišení je navrženo tak, aby umožňovalo hostitelům nastavit různé zásady v závislosti na tom, kde v kódu dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="9d6b1-118">*Kritická oblast kódu* je jakékoli místo, kde CLR nemůže zaručit, že přerušení úlohy nebo selhání dokončení žádosti o prostředky ovlivní pouze aktuální úlohu.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="9d6b1-119">Například pokud úloha drží zámek a obdrží HRESULT, která indikuje selhání při vytváření žádosti o přidělení paměti, není nestačí jednoduše tuto úlohu přerušit, aby se zajistila stabilita <xref:System.AppDomain> , protože <xref:System.AppDomain> může obsahovat další úlohy, které čekají na stejný zámek.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="9d6b1-120">Pokud chcete opustit aktuální úlohu, může to způsobit, že tyto další úlohy přestanou reagovat.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="9d6b1-121">V takovém případě hostitel potřebuje možnost uvolnit celé <xref:System.AppDomain> místo rizikového potenciálního nestability.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="9d6b1-122">*Nekritická oblast kódu*na druhé straně je oblast, kde CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohu, na které dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="9d6b1-123">CLR také rozlišuje mezi řádnými a neřádnými (hrubé) přerušeními.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="9d6b1-124">Obecně platí, že normální nebo plynulé přerušení umožňuje spustit rutiny zpracování výjimek a finalizační metody před přerušením úlohy, zatímco hrubé přerušení neprovede žádné takové záruky.</span><span class="sxs-lookup"><span data-stu-id="9d6b1-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6b1-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d6b1-125">Requirements</span></span>  
 <span data-ttu-id="9d6b1-126">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6b1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6b1-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d6b1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d6b1-128">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d6b1-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d6b1-129">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6b1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6b1-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d6b1-130">See also</span></span>

- [<span data-ttu-id="9d6b1-131">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="9d6b1-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="9d6b1-132">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="9d6b1-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="9d6b1-133">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d6b1-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="9d6b1-134">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d6b1-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="9d6b1-135">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="9d6b1-135">Hosting Enumerations</span></span>](hosting-enumerations.md)
