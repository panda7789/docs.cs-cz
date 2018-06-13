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
ms.openlocfilehash: c3b8dd67cb7dff4bec5bab192a08461ef13fcbd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436355"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="c81b7-102">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c81b7-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="c81b7-103">Umožňuje na hostiteli a poté zadejte správce domény aplikace, který se použije k chybě při inicializaci výchozí doméně aplikace a k určení inicializační vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c81b7-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c81b7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c81b7-104">Methods</span></span>  
  
|<span data-ttu-id="c81b7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c81b7-105">Method</span></span>|<span data-ttu-id="c81b7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c81b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c81b7-107">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="c81b7-107">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="c81b7-108">Určuje typ odvozený z <xref:System.AppDomainManager?displayProperty=nameWithType> třídu aplikace správce domény, který se použije k chybě při inicializaci výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="c81b7-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="c81b7-109">SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c81b7-109">SetPropertiesForDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="c81b7-110">Nastaví vlastnosti, které se použijí k chybě při inicializaci výchozí doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="c81b7-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c81b7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c81b7-111">Remarks</span></span>  
 <span data-ttu-id="c81b7-112">Chcete-li získat instanci tohoto rozhraní, zavolejte [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda s typem manager IID `IID_ICLRDomainManager`.</span><span class="sxs-lookup"><span data-stu-id="c81b7-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81b7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c81b7-113">Requirements</span></span>  
 <span data-ttu-id="c81b7-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c81b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81b7-115">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c81b7-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c81b7-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c81b7-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c81b7-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81b7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81b7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c81b7-118">See Also</span></span>  
 [<span data-ttu-id="c81b7-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c81b7-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c81b7-120">Hostování</span><span class="sxs-lookup"><span data-stu-id="c81b7-120">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
