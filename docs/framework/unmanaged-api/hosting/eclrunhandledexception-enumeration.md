---
title: EClrUnhandledException – výčet
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 302db0d029b3811d151473323a7a60bd16a00ec1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131236"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="a8576-102">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="a8576-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="a8576-103">Popisuje dostupné možnosti pro správu výjimek, které jsou v uživatelském kódu neošetřené.</span><span class="sxs-lookup"><span data-stu-id="a8576-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8576-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="a8576-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a8576-105">Members</span></span>  
  
|<span data-ttu-id="a8576-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a8576-106">Member</span></span>|<span data-ttu-id="a8576-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a8576-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="a8576-108">Určuje, že dojde k výchozímu chování.</span><span class="sxs-lookup"><span data-stu-id="a8576-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="a8576-109">Proces se odpojí.</span><span class="sxs-lookup"><span data-stu-id="a8576-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="a8576-110">Určuje, že modul CLR (Common Language Runtime) ignoruje neošetřené výjimky a umožňuje hostiteli určit jakoukoli další akci.</span><span class="sxs-lookup"><span data-stu-id="a8576-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8576-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8576-111">Remarks</span></span>  
 <span data-ttu-id="a8576-112">Chcete-li určit, že se CLR chová jako starší verze, použijte člena `eHostDeterminedPolicy`.</span><span class="sxs-lookup"><span data-stu-id="a8576-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8576-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8576-113">Requirements</span></span>  
 <span data-ttu-id="a8576-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8576-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8576-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8576-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8576-116">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8576-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8576-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8576-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8576-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8576-118">See also</span></span>

- [<span data-ttu-id="a8576-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="a8576-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="a8576-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="a8576-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="a8576-121">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8576-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="a8576-122">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="a8576-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="a8576-123">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a8576-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="a8576-124">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="a8576-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
