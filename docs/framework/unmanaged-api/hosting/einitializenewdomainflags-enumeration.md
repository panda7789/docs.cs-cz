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
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095357"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="28e0c-102">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="28e0c-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="28e0c-103">Umožňuje hostiteli modul runtime poskytnout informace o inicializaci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="28e0c-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28e0c-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="28e0c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="28e0c-105">Members</span></span>  
  
|<span data-ttu-id="28e0c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="28e0c-106">Member</span></span>|<span data-ttu-id="28e0c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="28e0c-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="28e0c-108">Žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="28e0c-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="28e0c-109">Informuje o tom common language runtime (CLR), hostitele nebudou měnit stav zabezpečení domény aplikace v <xref:System.AppDomainManager.InitializeNewDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="28e0c-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28e0c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28e0c-110">Remarks</span></span>  
 <span data-ttu-id="28e0c-111">[Iclrdomainmanager::setappdomainmanagertype –](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) metoda přijímá parametr typu `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="28e0c-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28e0c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="28e0c-112">Requirements</span></span>  
 <span data-ttu-id="28e0c-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28e0c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28e0c-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28e0c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28e0c-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28e0c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28e0c-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28e0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e0c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28e0c-117">See also</span></span>

- [<span data-ttu-id="28e0c-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="28e0c-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="28e0c-119">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="28e0c-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
