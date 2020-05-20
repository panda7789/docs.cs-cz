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
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615706"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="69dad-102">ICLRDomainManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69dad-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="69dad-103">Umožňuje hostiteli zadat správce aplikační domény, který se použije k inicializaci výchozí domény aplikace, a zadat vlastnosti inicializace.</span><span class="sxs-lookup"><span data-stu-id="69dad-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69dad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="69dad-104">Methods</span></span>  
  
|<span data-ttu-id="69dad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="69dad-105">Method</span></span>|<span data-ttu-id="69dad-106">Popis</span><span class="sxs-lookup"><span data-stu-id="69dad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69dad-107">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="69dad-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="69dad-108">Určuje typ odvozený od <xref:System.AppDomainManager?displayProperty=nameWithType> třídy správce aplikační domény, který se použije k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="69dad-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="69dad-109">SetPropertiesForDefaultAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="69dad-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="69dad-110">Nastaví vlastnosti, které se použijí k inicializaci výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="69dad-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69dad-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69dad-111">Remarks</span></span>  
 <span data-ttu-id="69dad-112">Chcete-li získat instanci tohoto rozhraní, zavolejte metodu [ICLRControl:: GetCLRManager –](iclrcontrol-getclrmanager-method.md) s typem správce IID `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="69dad-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69dad-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69dad-113">Requirements</span></span>  
 <span data-ttu-id="69dad-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69dad-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69dad-115">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="69dad-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="69dad-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="69dad-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69dad-117">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69dad-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69dad-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="69dad-118">See also</span></span>

- [<span data-ttu-id="69dad-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="69dad-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="69dad-120">Hostování</span><span class="sxs-lookup"><span data-stu-id="69dad-120">Hosting</span></span>](index.md)
