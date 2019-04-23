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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce53149b92ca40ad50ecbefaf4701940e8567ae5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103919"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="f40dd-102">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f40dd-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="f40dd-103">Umožňuje hostiteli určit, který se použije k inicializaci výchozí domény aplikace a k určení vlastností inicializace správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f40dd-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f40dd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f40dd-104">Methods</span></span>  
  
|<span data-ttu-id="f40dd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f40dd-105">Method</span></span>|<span data-ttu-id="f40dd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f40dd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f40dd-107">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="f40dd-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="f40dd-108">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídu správce domény aplikace, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f40dd-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="f40dd-109">SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="f40dd-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="f40dd-110">Nastaví vlastnosti, které bude sloužit k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f40dd-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f40dd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f40dd-111">Remarks</span></span>  
 <span data-ttu-id="f40dd-112">Chcete-li získat instanci tohoto rozhraní, zavolejte [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda s typem správce IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="f40dd-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40dd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f40dd-113">Requirements</span></span>  
 <span data-ttu-id="f40dd-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f40dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40dd-115">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f40dd-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f40dd-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f40dd-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f40dd-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40dd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f40dd-118">See also</span></span>

- [<span data-ttu-id="f40dd-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f40dd-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f40dd-120">Hostování</span><span class="sxs-lookup"><span data-stu-id="f40dd-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
