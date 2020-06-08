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
ms.openlocfilehash: fa2b5052a1d569487f0c6c72699ff9ab571beefc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504391"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="9c626-102">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="9c626-102">EClrFailure Enumeration</span></span>
<span data-ttu-id="9c626-103">V této části najdete popis sady selhání, pro které může hostitel nastavit akce zásad.</span><span class="sxs-lookup"><span data-stu-id="9c626-103">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c626-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c626-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9c626-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9c626-105">Members</span></span>  
  
|<span data-ttu-id="9c626-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9c626-106">Member</span></span>|<span data-ttu-id="9c626-107">Description</span><span class="sxs-lookup"><span data-stu-id="9c626-107">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="9c626-108">Došlo k chybě při pokusu o přidělení prostředku (například vlákna, bloku paměti nebo zámku) v nekritické oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="9c626-108">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="9c626-109">Došlo k chybě při pokusu o přidělení prostředku (například vlákna, bloku paměti nebo zámku) v kritické oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="9c626-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="9c626-110">Modul CLR (Common Language Runtime) již nemůže v procesu spustit spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="9c626-110">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="9c626-111">Následně volání všech hostujících funkcí vrátí hodnotu HRESULT HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9c626-111">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="9c626-112">Vlákno nedokázalo uvolnit zámek při návratu z <xref:System.AppDomain> objektu.</span><span class="sxs-lookup"><span data-stu-id="9c626-112">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="9c626-113">Hostitel nemůže tuto chybu nastavit, aby mohla způsobit přerušení vlákna.</span><span class="sxs-lookup"><span data-stu-id="9c626-113">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="9c626-114">Došlo k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9c626-114">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="9c626-115">Byl proveden pokus o čtení nebo zápis chráněné paměti.</span><span class="sxs-lookup"><span data-stu-id="9c626-115">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="9c626-116">Nepodporováno v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9c626-116">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="9c626-117">Došlo k chybě kontraktu kódu.</span><span class="sxs-lookup"><span data-stu-id="9c626-117">A code contract failure occurred.</span></span> <span data-ttu-id="9c626-118">Viz [kontrakty kódu](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9c626-118">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c626-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c626-119">Remarks</span></span>  
 <span data-ttu-id="9c626-120">V tématu metoda [ICLRPolicyManager:: SetActionOnFailure –](iclrpolicymanager-setactiononfailure-method.md) najdete seznam hodnot [EPolicyAction –](epolicyaction-enumeration.md) , které může hostitel použít k určení akcí zásad pro podmínky selhání.</span><span class="sxs-lookup"><span data-stu-id="9c626-120">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="9c626-121">Další informace o kritických a nekritických oblastech kódu naleznete v tématu [EClrOperation –](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9c626-121">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c626-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c626-122">Requirements</span></span>  
 <span data-ttu-id="9c626-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c626-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c626-124">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c626-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c626-125">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9c626-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c626-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c626-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c626-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c626-127">See also</span></span>

- [<span data-ttu-id="9c626-128">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c626-128">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="9c626-129">SetActionOnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="9c626-129">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="9c626-130">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9c626-130">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="9c626-131">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="9c626-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
