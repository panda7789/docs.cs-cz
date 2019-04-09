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
ms.openlocfilehash: 7e5fb3ab1d2dedb220fd4a486409512414233021
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176667"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="5f00b-102">EClrUnhandledException – výčet</span><span class="sxs-lookup"><span data-stu-id="5f00b-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="5f00b-103">Popisuje dostupné možnosti pro správu výjimek, které se neošetří v uživatelském kódu.</span><span class="sxs-lookup"><span data-stu-id="5f00b-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f00b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f00b-104">Syntax</span></span>  
  
```  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="5f00b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5f00b-105">Members</span></span>  
  
|<span data-ttu-id="5f00b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5f00b-106">Member</span></span>|<span data-ttu-id="5f00b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5f00b-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="5f00b-108">Určuje, že dochází k výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="5f00b-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="5f00b-109">Proces iframeworkview.</span><span class="sxs-lookup"><span data-stu-id="5f00b-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="5f00b-110">Určuje, že common language runtime (CLR) ignoruje neošetřené výjimky a tato funkce umožňuje hostiteli zjistit žádnou další akci.</span><span class="sxs-lookup"><span data-stu-id="5f00b-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f00b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f00b-111">Remarks</span></span>  
 <span data-ttu-id="5f00b-112">Chcete-li určit, že modul CLR se chovají jako předchozí verze, použijte `eHostDeterminedPolicy` člena.</span><span class="sxs-lookup"><span data-stu-id="5f00b-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f00b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f00b-113">Requirements</span></span>  
 <span data-ttu-id="5f00b-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f00b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f00b-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f00b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f00b-116">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f00b-116">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5f00b-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5f00b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5f00b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f00b-118">See also</span></span>

- [<span data-ttu-id="5f00b-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="5f00b-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="5f00b-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="5f00b-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="5f00b-121">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f00b-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="5f00b-122">SetUnhandledExceptionPolicy – metoda</span><span class="sxs-lookup"><span data-stu-id="5f00b-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="5f00b-123">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f00b-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="5f00b-124">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="5f00b-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
