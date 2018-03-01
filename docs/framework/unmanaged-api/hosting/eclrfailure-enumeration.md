---
title: "EClrFailure – výčet"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e25a5378349dd476321765bb085db958e29670e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="5f133-102">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="5f133-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="5f133-103">Popisuje sadu chyb, pro které hostitele může nastavit zásady akce.</span><span class="sxs-lookup"><span data-stu-id="5f133-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f133-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f133-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5f133-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5f133-105">Members</span></span>  
  
|<span data-ttu-id="5f133-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5f133-106">Member</span></span>|<span data-ttu-id="5f133-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5f133-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="5f133-108">Došlo k chybě při pokusu o přidělení prostředků (například vlákno, blok paměti nebo zámek) v oblasti nekritické kódu.</span><span class="sxs-lookup"><span data-stu-id="5f133-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="5f133-109">Došlo k chybě při pokusu o přidělení prostředků (například vlákno, blok paměti nebo zámek) v oblasti kritické kódu.</span><span class="sxs-lookup"><span data-stu-id="5f133-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="5f133-110">Modul CLR (CLR) je již možné spouštět spravovaného kódu v procesu.</span><span class="sxs-lookup"><span data-stu-id="5f133-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="5f133-111">Volání jakékoli hostování funkce vrací od nynějška, má hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5f133-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="5f133-112">Vlákno se nepodařilo uvolnit zámek při vrácení z <xref:System.AppDomain> objektu.</span><span class="sxs-lookup"><span data-stu-id="5f133-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="5f133-113">Hostitele nelze nastavit této chyby a způsobit, že vlákno k přerušení.</span><span class="sxs-lookup"><span data-stu-id="5f133-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="5f133-114">Došlo k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5f133-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="5f133-115">Došlo k pokusu o čtení nebo zápisu chráněné paměti.</span><span class="sxs-lookup"><span data-stu-id="5f133-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="5f133-116">Není podporováno v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f133-116">Not supported in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="5f133-117">Kontrakt kódu došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="5f133-117">A code contract failure occurred.</span></span> <span data-ttu-id="5f133-118">V tématu [Code kontrakty](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="5f133-118">See [Code Contracts](../../../../docs/framework/debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f133-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f133-119">Remarks</span></span>  
 <span data-ttu-id="5f133-120">Najdete v článku [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metoda seznam [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) hodnoty, které jsou hostiteli můžete použít k určení akce zásad podmínky při selhání.</span><span class="sxs-lookup"><span data-stu-id="5f133-120">See the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="5f133-121">Další informace o oblastech kritické a nekritické kódu najdete v tématu [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5f133-121">For more information about critical and non-critical regions of code, see [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f133-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f133-122">Requirements</span></span>  
 <span data-ttu-id="5f133-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f133-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f133-124">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f133-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f133-125">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f133-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f133-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f133-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f133-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f133-127">See Also</span></span>  
 [<span data-ttu-id="5f133-128">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f133-128">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="5f133-129">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="5f133-129">SetActionOnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)  
 [<span data-ttu-id="5f133-130">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f133-130">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="5f133-131">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="5f133-131">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
