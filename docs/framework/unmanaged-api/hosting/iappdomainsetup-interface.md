---
title: IAppDomainSetup – rozhraní
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617058"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="b88e2-102">IAppDomainSetup – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b88e2-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="b88e2-103">Poskytne vlastnosti, které umožňují hostiteli nakonfigurovat <xref:System.AppDomain?displayProperty=nameWithType> typ před voláním metody [ICorRuntimeHost:: CreateDomainEx –](icorruntimehost-createdomainex-method.md) , aby ji bylo možné vytvořit.</span><span class="sxs-lookup"><span data-stu-id="b88e2-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b88e2-104">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b88e2-104">Properties</span></span>  
  
|<span data-ttu-id="b88e2-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b88e2-105">Property</span></span>|<span data-ttu-id="b88e2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b88e2-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="b88e2-107">Získá nebo nastaví název adresáře, který obsahuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b88e2-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="b88e2-108">Získá nebo nastaví název aplikace.</span><span class="sxs-lookup"><span data-stu-id="b88e2-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="b88e2-109">Získá nebo nastaví název oblasti specifické pro aplikaci, ve které jsou soubory kopírovány stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="b88e2-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="b88e2-110">Získá nebo nastaví název konfiguračního souboru pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b88e2-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="b88e2-111">Získá nebo nastaví název adresáře, kde jsou uloženy a otevřeny dynamicky generované soubory.</span><span class="sxs-lookup"><span data-stu-id="b88e2-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="b88e2-112">Získá nebo nastaví cestu k souboru s licencí, který je přidružený k této doméně.</span><span class="sxs-lookup"><span data-stu-id="b88e2-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="b88e2-113">Získá nebo nastaví seznam adresářů v kombinaci s <xref:System.AppDomainSetup.ApplicationBase%2A> adresářem pro testování privátních sestavení.</span><span class="sxs-lookup"><span data-stu-id="b88e2-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="b88e2-114">Získává nebo nastavuje řetězcovou hodnotu, která zahrnuje nebo vylučuje <xref:System.AppDomainSetup.ApplicationBase%2A> cestu pro hledání aplikace.</span><span class="sxs-lookup"><span data-stu-id="b88e2-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="b88e2-115">Získá nebo nastaví názvy adresářů, které obsahují sestavení pro vytváření stínových kopií.</span><span class="sxs-lookup"><span data-stu-id="b88e2-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="b88e2-116">Získá nebo nastaví řetězec, který označuje, zda je stínové kopírování zapnuto nebo vypnuto.</span><span class="sxs-lookup"><span data-stu-id="b88e2-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="b88e2-117">Platné hodnoty jsou "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="b88e2-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b88e2-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b88e2-118">Remarks</span></span>  
 <span data-ttu-id="b88e2-119">`IAppDomainSetup`Rozhraní odpovídá spravovanému <xref:System.IAppDomainSetup> rozhraní, které <xref:System.AppDomainSetup> typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="b88e2-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="b88e2-120"><xref:System.IAppDomainSetup?displayProperty=nameWithType>Podrobné popisy jeho vlastností najdete v tématu.</span><span class="sxs-lookup"><span data-stu-id="b88e2-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="b88e2-121">`IAppDomainSetup`představuje informace o vazbě sestavení, které mohou být přidány do <xref:System.AppDomain> instance před jeho vytvořením.</span><span class="sxs-lookup"><span data-stu-id="b88e2-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="b88e2-122">Například hostitel může nastavit <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost tak, aby navázala kořenový adresář, který modul CLR (Common Language Runtime) pro spravovaná sestavení vyhledá.</span><span class="sxs-lookup"><span data-stu-id="b88e2-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b88e2-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b88e2-123">Requirements</span></span>  
 <span data-ttu-id="b88e2-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b88e2-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b88e2-125">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b88e2-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b88e2-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b88e2-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b88e2-127">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b88e2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88e2-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b88e2-128">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="b88e2-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b88e2-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
