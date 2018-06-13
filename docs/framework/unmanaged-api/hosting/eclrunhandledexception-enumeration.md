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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eeff8aa0336c0c497e306825c6c77f4f8745ca7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431802"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="aa87c-102">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="aa87c-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="aa87c-103">Popisuje dostupné možnosti pro správu výjimky, které jsou neošetřené v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="aa87c-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa87c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa87c-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="aa87c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="aa87c-105">Members</span></span>  
  
|<span data-ttu-id="aa87c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="aa87c-106">Member</span></span>|<span data-ttu-id="aa87c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aa87c-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="aa87c-108">Určuje, že dochází k výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="aa87c-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="aa87c-109">Proces odpojí.</span><span class="sxs-lookup"><span data-stu-id="aa87c-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="aa87c-110">Určuje, že modul CLR (CLR) ignoruje neošetřených výjimek a umožňuje hostiteli určení žádné další akce.</span><span class="sxs-lookup"><span data-stu-id="aa87c-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa87c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa87c-111">Remarks</span></span>  
 <span data-ttu-id="aa87c-112">K určení, že modulu CLR chovat jako předchozí verze, použijte `eHostDeterminedPolicy` člen.</span><span class="sxs-lookup"><span data-stu-id="aa87c-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa87c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa87c-113">Requirements</span></span>  
 <span data-ttu-id="aa87c-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa87c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa87c-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa87c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa87c-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa87c-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa87c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa87c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa87c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa87c-118">See Also</span></span>  
 [<span data-ttu-id="aa87c-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="aa87c-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="aa87c-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="aa87c-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="aa87c-121">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa87c-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="aa87c-122">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="aa87c-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="aa87c-123">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa87c-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="aa87c-124">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="aa87c-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
