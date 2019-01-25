---
title: EClrFailure – výčet
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3109d5ba49b01f25c72aaa1c31c74984a683dd73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746528"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="4f575-102">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="4f575-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="4f575-103">Popisuje sadu selhání, pro které hostitele může nastavit akce zásad.</span><span class="sxs-lookup"><span data-stu-id="4f575-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f575-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f575-104">Syntax</span></span>  
  
```  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="4f575-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4f575-105">Members</span></span>  
  
|<span data-ttu-id="4f575-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4f575-106">Member</span></span>|<span data-ttu-id="4f575-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4f575-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="4f575-108">Došlo k chybě při pokusu o přidělení prostředků (například vlákně, blok paměti nebo zámek) v méně důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="4f575-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="4f575-109">Došlo k chybě při pokusu o přidělení prostředků (například vlákně, blok paměti nebo zámek) v oblasti, kritický kód.</span><span class="sxs-lookup"><span data-stu-id="4f575-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="4f575-110">Modul CLR (CLR) již není možné spouštět spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="4f575-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="4f575-111">Od nynějška volání jakékoli hostitelské funkce vrací hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4f575-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="4f575-112">Vlákno se nepodařilo uvolnit zámek při návratu z <xref:System.AppDomain> objektu.</span><span class="sxs-lookup"><span data-stu-id="4f575-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="4f575-113">Hostitele nelze nastavit této chyby a způsobit, že vlákno pro přerušení.</span><span class="sxs-lookup"><span data-stu-id="4f575-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="4f575-114">Došlo k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4f575-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="4f575-115">Došlo pokusu o čtení nebo zápis v chráněné paměti.</span><span class="sxs-lookup"><span data-stu-id="4f575-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="4f575-116">Není podporováno v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f575-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="4f575-117">Došlo k chybě kontraktu kódu.</span><span class="sxs-lookup"><span data-stu-id="4f575-117">A code contract failure occurred.</span></span> <span data-ttu-id="4f575-118">Zobrazit [kontrakty kódu](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f575-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f575-119">Remarks</span></span>  
 <span data-ttu-id="4f575-120">Zobrazit [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda seznam [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty hostitele můžete použít k určení akce zásad pro podmínky při selhání.</span><span class="sxs-lookup"><span data-stu-id="4f575-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="4f575-121">Další informace o oblastech kritické a nekritické kód, naleznete v tématu [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f575-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f575-122">Requirements</span></span>  
 <span data-ttu-id="4f575-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f575-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f575-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f575-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f575-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f575-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f575-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f575-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f575-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f575-127">See also</span></span>
- [<span data-ttu-id="4f575-128">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f575-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="4f575-129">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="4f575-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="4f575-130">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f575-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="4f575-131">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="4f575-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
