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
ms.openlocfilehash: 8788d6e2220778a3f0926d5ed3dd59142487bcca
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616187"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="2cc9c-102">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="2cc9c-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="2cc9c-103">Popisuje akce zásad, které může hostitel nastavit pro operace popsané v [EClrOperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) a chyby popsané v [EClrFailure –](eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="2cc9c-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cc9c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="2cc9c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2cc9c-105">Members</span></span>  
  
|<span data-ttu-id="2cc9c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2cc9c-106">Member</span></span>|<span data-ttu-id="2cc9c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2cc9c-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="2cc9c-108">Určuje, že modul CLR (Common Language Runtime) by měl plynule přerušit vlákno.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="2cc9c-109">Bezproblémové přerušení zahrnuje pokusy o spuštění všech `finally` bloků, všechny `catch` bloky související s přerušením vlákna a finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="2cc9c-110">Určuje, že CLR by měl vstoupit do zakázaného stavu.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="2cc9c-111">V ovlivněném procesu nelze provádět žádné další spravované kódy a vlákna jsou blokována při zadávání CLR.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="2cc9c-112">Určuje, že se má modul CLR pokusit o řádné ukončení procesu, včetně spuštění finalizační metody a provádění operací vyčištění a protokolování.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="2cc9c-113">Určuje, že modul CLR má okamžitě ukončit proces, aniž by musel spouštět finalizační metody nebo provádět operace vyčištění a protokolování.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="2cc9c-114">Oznámení je však odesláno do ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="2cc9c-115">Určuje, že by neměla být provedena žádná akce.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="2cc9c-116">Určuje, že modul CLR má provést přerušení hrubé vlákna.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="2cc9c-117">`catch` `finally` Jsou spuštěny pouze ty a bloky označené pomocí <xref:System.EnterpriseServices.MustRunInClientContextAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2cc9c-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="2cc9c-118">Určuje, že modul CLR má ukončit proces bez spuštění finalizační metody nebo operací protokolování.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="2cc9c-119">Určuje, že modul CLR má provést hrubé uvolnění <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2cc9c-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="2cc9c-120">Jsou spuštěny pouze finalizační metody označené pomocí <xref:System.EnterpriseServices.MustRunInClientContextAttribute> .</span><span class="sxs-lookup"><span data-stu-id="2cc9c-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="2cc9c-121">Podobně všechny podprocesy s tímto <xref:System.AppDomain> objektem v zásobníku obdrží `ThreadAbortException` , ale pouze ty `catch` a `finally` bloky označené pomocí <xref:System.EnterpriseServices.MustRunInClientContextAttribute> jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="2cc9c-122">Určuje, že by měla být vyvolána výjimka, která je vhodná pro podmínku, jako je například nedostatek paměti, přetečení vyrovnávací paměti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="2cc9c-123">Určuje, že <xref:System.AppDomain> by mělo být uvolněno.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="2cc9c-124">Modul CLR se pokusí spustit finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="2cc9c-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cc9c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cc9c-125">Remarks</span></span>  
 <span data-ttu-id="2cc9c-126">Hostitel nastavuje akce zásad voláním metod rozhraní [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2cc9c-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="2cc9c-127">Informace o hrubé a bezproblémovém přerušení najdete v tématu výčet [EClrOperation –](eclroperation-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="2cc9c-127">For information about rude and graceful aborts, see the [EClrOperation](eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cc9c-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cc9c-128">Requirements</span></span>  
 <span data-ttu-id="2cc9c-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cc9c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cc9c-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2cc9c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cc9c-131">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2cc9c-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cc9c-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cc9c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc9c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cc9c-133">See also</span></span>

- [<span data-ttu-id="2cc9c-134">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="2cc9c-134">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="2cc9c-135">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cc9c-135">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="2cc9c-136">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cc9c-136">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="2cc9c-137">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="2cc9c-137">Hosting Enumerations</span></span>](hosting-enumerations.md)
