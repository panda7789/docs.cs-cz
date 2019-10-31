---
title: ICLRDomainManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: aa874205cf14232e7a69ed2215086e33c0beab4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129345"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="eb642-102">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb642-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="eb642-103">Umožňuje hostiteli zadat správce aplikační domény, který se použije k inicializaci výchozí domény aplikace, a zadat vlastnosti inicializace.</span><span class="sxs-lookup"><span data-stu-id="eb642-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb642-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eb642-104">Methods</span></span>  
  
|<span data-ttu-id="eb642-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb642-105">Method</span></span>|<span data-ttu-id="eb642-106">Popis</span><span class="sxs-lookup"><span data-stu-id="eb642-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb642-107">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="eb642-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="eb642-108">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb642-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="eb642-109">SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="eb642-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="eb642-110">Nastaví vlastnosti, které se použijí k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb642-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb642-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb642-111">Remarks</span></span>  
 <span data-ttu-id="eb642-112">Chcete-li získat instanci tohoto rozhraní, zavolejte metodu [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) s typem správce IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="eb642-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb642-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb642-113">Requirements</span></span>  
 <span data-ttu-id="eb642-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb642-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb642-115">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="eb642-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eb642-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eb642-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb642-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb642-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb642-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb642-118">See also</span></span>

- [<span data-ttu-id="eb642-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eb642-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="eb642-120">Hostování</span><span class="sxs-lookup"><span data-stu-id="eb642-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
