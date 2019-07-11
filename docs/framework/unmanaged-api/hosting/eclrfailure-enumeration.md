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
ms.openlocfilehash: 5f3e39d94996f14f1ae6593b9adaa5db3ef674c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769663"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="c2e20-102">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="c2e20-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="c2e20-103">Popisuje sadu selhání, pro které hostitele může nastavit akce zásad.</span><span class="sxs-lookup"><span data-stu-id="c2e20-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2e20-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="c2e20-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c2e20-105">Members</span></span>  
  
|<span data-ttu-id="c2e20-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c2e20-106">Member</span></span>|<span data-ttu-id="c2e20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c2e20-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="c2e20-108">Došlo k chybě při pokusu o přidělení prostředků (například vlákně, blok paměti nebo zámek) v méně důležité oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="c2e20-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="c2e20-109">Došlo k chybě při pokusu o přidělení prostředků (například vlákně, blok paměti nebo zámek) v oblasti, kritický kód.</span><span class="sxs-lookup"><span data-stu-id="c2e20-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="c2e20-110">Modul CLR (CLR) již není možné spouštět spravovaný kód v procesu.</span><span class="sxs-lookup"><span data-stu-id="c2e20-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="c2e20-111">Od nynějška volání jakékoli hostitelské funkce vrací hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c2e20-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="c2e20-112">Vlákno se nepodařilo uvolnit zámek při návratu z <xref:System.AppDomain> objektu.</span><span class="sxs-lookup"><span data-stu-id="c2e20-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="c2e20-113">Hostitele nelze nastavit této chyby a způsobit, že vlákno pro přerušení.</span><span class="sxs-lookup"><span data-stu-id="c2e20-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="c2e20-114">Došlo k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c2e20-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="c2e20-115">Došlo pokusu o čtení nebo zápis v chráněné paměti.</span><span class="sxs-lookup"><span data-stu-id="c2e20-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="c2e20-116">Není podporován v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c2e20-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="c2e20-117">Došlo k chybě kontraktu kódu.</span><span class="sxs-lookup"><span data-stu-id="c2e20-117">A code contract failure occurred.</span></span> <span data-ttu-id="c2e20-118">Zobrazit [kontrakty kódu](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="c2e20-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2e20-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2e20-119">Remarks</span></span>  
 <span data-ttu-id="c2e20-120">Zobrazit [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda seznam [epolicyaction –](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty hostitele můžete použít k určení akce zásad pro podmínky při selhání.</span><span class="sxs-lookup"><span data-stu-id="c2e20-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="c2e20-121">Další informace o oblastech kritické a nekritické kód, naleznete v tématu [eclroperation –](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="c2e20-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2e20-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2e20-122">Requirements</span></span>  
 <span data-ttu-id="c2e20-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2e20-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2e20-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c2e20-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c2e20-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2e20-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2e20-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2e20-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e20-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2e20-127">See also</span></span>

- [<span data-ttu-id="c2e20-128">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2e20-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="c2e20-129">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="c2e20-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="c2e20-130">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2e20-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="c2e20-131">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="c2e20-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
