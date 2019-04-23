---
title: EPolicyAction – výčet
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bd7da67cbac958f0b34c8295454a719962c7ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201725"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="b66d7-102">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="b66d7-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="b66d7-103">Popisuje akce zásad hostitele můžete nastavit pro operace popsal [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a selhání popsal [eclrfailure –](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b66d7-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b66d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b66d7-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="b66d7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b66d7-105">Members</span></span>  
  
|<span data-ttu-id="b66d7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b66d7-106">Member</span></span>|<span data-ttu-id="b66d7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b66d7-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="b66d7-108">Určuje, že modul CLR (CLR) by měl přerušit vlákno bez výpadku.</span><span class="sxs-lookup"><span data-stu-id="b66d7-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="b66d7-109">Bezproblémové přerušení zahrnuje pokusy o spuštění všech `finally` blokuje všechny `catch` bloky týkající se přeruší vlákna a finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b66d7-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="b66d7-110">Určuje, že modul CLR by měla zadat zakázaném stavu.</span><span class="sxs-lookup"><span data-stu-id="b66d7-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="b66d7-111">Žádné další spravovaného kódu mohou být provedeny v procesu ovlivněná a jsou blokovaná vlákna vstupují do platformy CLR.</span><span class="sxs-lookup"><span data-stu-id="b66d7-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="b66d7-112">Určuje, že modul CLR pokusit o řádné ukončení procesu, včetně spuštění finalizační metody a vyčištění a operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="b66d7-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="b66d7-113">Určuje, že modul CLR by měla opustí proces okamžitě, bez spuštění finalizační metody nebo vyčištění a operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="b66d7-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="b66d7-114">Nicméně je oznámení odeslané ladicímu programu.</span><span class="sxs-lookup"><span data-stu-id="b66d7-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="b66d7-115">Určuje, že by měla být provedena žádná akce.</span><span class="sxs-lookup"><span data-stu-id="b66d7-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="b66d7-116">Určuje, že modul CLR by měl provádět přerušení článku neslušní vlákna.</span><span class="sxs-lookup"><span data-stu-id="b66d7-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="b66d7-117">Pouze ty `catch` a `finally` bloky označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provádějí.</span><span class="sxs-lookup"><span data-stu-id="b66d7-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="b66d7-118">Určuje, že modul CLR má ukončit proces bez spuštění finalizační metody nebo protokolování operations.</span><span class="sxs-lookup"><span data-stu-id="b66d7-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="b66d7-119">Určuje, že modul CLR by měl provádět článku neslušní uvolnění <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="b66d7-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="b66d7-120">Pouze finalizační metody označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provádějí.</span><span class="sxs-lookup"><span data-stu-id="b66d7-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="b66d7-121">Podobně platí, všechna vlákna s tímto <xref:System.AppDomain> v jejich zásobníku přijímat `ThreadAbortException`, ale jenom na ty `catch` a `finally` bloky označené <xref:System.EnterpriseServices.MustRunInClientContextAttribute> provádějí.</span><span class="sxs-lookup"><span data-stu-id="b66d7-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="b66d7-122">Určuje, že by měl vyvolána výjimka pro podmínku, třeba na více instancí z důvodu nedostatku paměti, přetečení vyrovnávací paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b66d7-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="b66d7-123">Určuje, že <xref:System.AppDomain> by měla být uvolněna.</span><span class="sxs-lookup"><span data-stu-id="b66d7-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="b66d7-124">Modul CLR se pokusí o spuštění finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="b66d7-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b66d7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b66d7-125">Remarks</span></span>  
 <span data-ttu-id="b66d7-126">Hostitel nastaví akce zásad voláním metod [iclrpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b66d7-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="b66d7-127">Informace o článku neslušní a bezproblémové přeruší, najdete v článku [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="b66d7-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b66d7-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b66d7-128">Requirements</span></span>  
 <span data-ttu-id="b66d7-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b66d7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b66d7-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b66d7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b66d7-131">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b66d7-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b66d7-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b66d7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66d7-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b66d7-133">See also</span></span>

- [<span data-ttu-id="b66d7-134">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="b66d7-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="b66d7-135">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b66d7-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="b66d7-136">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b66d7-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="b66d7-137">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="b66d7-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
