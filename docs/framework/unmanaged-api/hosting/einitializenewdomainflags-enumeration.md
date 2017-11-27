---
title: "EInitializeNewDomainFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EInitializeNewDomainFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: EInitializeNewDomainFlags
helpviewer_keywords: EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bee1c5086502a9675e8149e7d6c9bc72f573815c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="4e7ea-102">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="4e7ea-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="4e7ea-103">Umožňuje hostitele modulu runtime poskytnout informace o inicializaci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4e7ea-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e7ea-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4e7ea-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4e7ea-105">Members</span></span>  
  
|<span data-ttu-id="4e7ea-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4e7ea-106">Member</span></span>|<span data-ttu-id="4e7ea-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4e7ea-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="4e7ea-108">Žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="4e7ea-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="4e7ea-109">Modul CLR (CLR) informuje, že hostitel nebude provádět změny stavu zabezpečení v doméně aplikace <xref:System.AppDomainManager.InitializeNewDomain%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4e7ea-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7ea-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e7ea-110">Remarks</span></span>  
 <span data-ttu-id="4e7ea-111">[Iclrdomainmanager::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda přebírá parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="4e7ea-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e7ea-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e7ea-112">Requirements</span></span>  
 <span data-ttu-id="4e7ea-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e7ea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e7ea-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4e7ea-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e7ea-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e7ea-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e7ea-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e7ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e7ea-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e7ea-117">See Also</span></span>  
 [<span data-ttu-id="4e7ea-118">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="4e7ea-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="4e7ea-119">Setappdomainmanagertype – metoda</span><span class="sxs-lookup"><span data-stu-id="4e7ea-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
