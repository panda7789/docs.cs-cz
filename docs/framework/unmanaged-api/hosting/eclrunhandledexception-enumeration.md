---
title: "EClrUnhandledException – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrUnhandledException
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrUnhandledException
helpviewer_keywords: EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67787072779e0cb22a339c2d13c972ba36f3ed61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="7bb72-102">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="7bb72-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="7bb72-103">Popisuje dostupné možnosti pro správu výjimky, které jsou neošetřené v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="7bb72-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bb72-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="7bb72-105">Členové</span><span class="sxs-lookup"><span data-stu-id="7bb72-105">Members</span></span>  
  
|<span data-ttu-id="7bb72-106">Člen</span><span class="sxs-lookup"><span data-stu-id="7bb72-106">Member</span></span>|<span data-ttu-id="7bb72-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7bb72-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="7bb72-108">Určuje, že dochází k výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="7bb72-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="7bb72-109">Proces odpojí.</span><span class="sxs-lookup"><span data-stu-id="7bb72-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="7bb72-110">Určuje, že modul CLR (CLR) ignoruje neošetřených výjimek a umožňuje hostiteli určení žádné další akce.</span><span class="sxs-lookup"><span data-stu-id="7bb72-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb72-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bb72-111">Remarks</span></span>  
 <span data-ttu-id="7bb72-112">K určení, že modulu CLR chovat jako předchozí verze, použijte `eHostDeterminedPolicy` člen.</span><span class="sxs-lookup"><span data-stu-id="7bb72-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb72-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7bb72-113">Requirements</span></span>  
 <span data-ttu-id="7bb72-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb72-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb72-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7bb72-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bb72-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bb72-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb72-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb72-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb72-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bb72-118">See Also</span></span>  
 [<span data-ttu-id="7bb72-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="7bb72-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="7bb72-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="7bb72-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="7bb72-121">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7bb72-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="7bb72-122">Setunhandledexceptionpolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="7bb72-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)  
 [<span data-ttu-id="7bb72-123">Ihostpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7bb72-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="7bb72-124">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="7bb72-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
