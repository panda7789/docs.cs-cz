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
ms.openlocfilehash: 7ff10f84d8d270d31c5d560fb3c9bd3c81cf3e24
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616226"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="26005-102">EInitializeNewDomainFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="26005-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="26005-103">Povolí hostiteli poskytovat modul runtime s informacemi o inicializaci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="26005-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26005-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26005-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="26005-105">Členové</span><span class="sxs-lookup"><span data-stu-id="26005-105">Members</span></span>  
  
|<span data-ttu-id="26005-106">Člen</span><span class="sxs-lookup"><span data-stu-id="26005-106">Member</span></span>|<span data-ttu-id="26005-107">Popis</span><span class="sxs-lookup"><span data-stu-id="26005-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="26005-108">Žádné příznaky.</span><span class="sxs-lookup"><span data-stu-id="26005-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="26005-109">Informuje modul CLR (Common Language Runtime), který hostitel neprovede, aby v metodě provedl změny stavu zabezpečení domény aplikace <xref:System.AppDomainManager.InitializeNewDomain%2A> .</span><span class="sxs-lookup"><span data-stu-id="26005-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26005-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26005-110">Remarks</span></span>  
 <span data-ttu-id="26005-111">Metoda [ICLRDomainManager:: SetAppDomainManagerType –](iclrdomainmanager-setappdomainmanagertype-method.md) přebírá parametr typu `EInitializeNewDomainFlags` .</span><span class="sxs-lookup"><span data-stu-id="26005-111">The [ICLRDomainManager::SetAppDomainManagerType](iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26005-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26005-112">Requirements</span></span>  
 <span data-ttu-id="26005-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26005-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26005-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26005-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26005-115">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26005-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26005-116">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26005-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26005-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="26005-117">See also</span></span>

- [<span data-ttu-id="26005-118">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="26005-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
- [<span data-ttu-id="26005-119">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="26005-119">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)
