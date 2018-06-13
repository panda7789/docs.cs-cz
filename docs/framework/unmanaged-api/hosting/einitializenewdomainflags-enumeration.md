---
title: EInitializeNewDomainFlags – výčet
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0175ab1d06a8166a5bbfd0c42018085a801740f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431446"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="3834d-102">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="3834d-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="3834d-103">Umožňuje hostitele modulu runtime poskytnout informace o inicializaci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3834d-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3834d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3834d-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="3834d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3834d-105">Members</span></span>  
  
|<span data-ttu-id="3834d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3834d-106">Member</span></span>|<span data-ttu-id="3834d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3834d-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="3834d-108">Žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="3834d-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="3834d-109">Modul CLR (CLR) informuje, že hostitel nebude provádět změny stavu zabezpečení v doméně aplikace <xref:System.AppDomainManager.InitializeNewDomain%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3834d-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3834d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3834d-110">Remarks</span></span>  
 <span data-ttu-id="3834d-111">[Iclrdomainmanager::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda přebírá parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="3834d-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3834d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3834d-112">Requirements</span></span>  
 <span data-ttu-id="3834d-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3834d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3834d-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3834d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3834d-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3834d-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3834d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3834d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3834d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3834d-117">See Also</span></span>  
 [<span data-ttu-id="3834d-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="3834d-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="3834d-119">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="3834d-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
