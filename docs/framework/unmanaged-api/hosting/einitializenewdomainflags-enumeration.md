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
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129420"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="6b44a-102">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="6b44a-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="6b44a-103">Povolí hostiteli poskytovat modul runtime s informacemi o inicializaci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b44a-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b44a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b44a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6b44a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6b44a-105">Members</span></span>  
  
|<span data-ttu-id="6b44a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6b44a-106">Member</span></span>|<span data-ttu-id="6b44a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6b44a-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="6b44a-108">Žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="6b44a-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="6b44a-109">Informuje modul CLR (Common Language Runtime), který hostitel neprovede, aby v metodě <xref:System.AppDomainManager.InitializeNewDomain%2A> provedl změny stavu zabezpečení domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b44a-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b44a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b44a-110">Remarks</span></span>  
 <span data-ttu-id="6b44a-111">Metoda [ICLRDomainManager:: SetAppDomainManagerType –](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) přebírá parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="6b44a-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b44a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b44a-112">Requirements</span></span>  
 <span data-ttu-id="6b44a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b44a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b44a-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6b44a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b44a-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b44a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b44a-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b44a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b44a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b44a-117">See also</span></span>

- [<span data-ttu-id="6b44a-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="6b44a-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="6b44a-119">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="6b44a-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
