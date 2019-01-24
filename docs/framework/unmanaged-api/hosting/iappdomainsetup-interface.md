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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef967039450c77b5927d501de63d53a245c90be0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509828"
---
# <a name="iappdomainsetup-interface"></a><span data-ttu-id="81abd-102">IAppDomainSetup – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81abd-102">IAppDomainSetup Interface</span></span>
<span data-ttu-id="81abd-103">Poskytne vlastnosti, které povolí hostitelské ke konfiguraci <xref:System.AppDomain?displayProperty=nameWithType> typ před voláním [icorruntimehost::createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoda k jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="81abd-103">Provides properties that allow the host to configure an <xref:System.AppDomain?displayProperty=nameWithType> type before calling the [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method to create it.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81abd-104">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="81abd-104">Properties</span></span>  
  
|<span data-ttu-id="81abd-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="81abd-105">Property</span></span>|<span data-ttu-id="81abd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="81abd-106">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|<span data-ttu-id="81abd-107">Získá nebo nastaví název adresáře, který obsahuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81abd-107">Gets or sets the name of the directory that contains the application.</span></span>|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|<span data-ttu-id="81abd-108">Získá nebo nastaví název aplikace.</span><span class="sxs-lookup"><span data-stu-id="81abd-108">Gets or sets the name of the application.</span></span>|  
|<xref:System.AppDomainSetup.CachePath%2A>|<span data-ttu-id="81abd-109">Získá nebo nastaví název oblasti konkrétní aplikaci kde soubory jsou vytvořena stínová kopie.</span><span class="sxs-lookup"><span data-stu-id="81abd-109">Gets or sets the name of an area specific to the application where files are shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|<span data-ttu-id="81abd-110">Získá nebo nastaví název konfiguračního souboru pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81abd-110">Gets or sets the name of the configuration file for an application.</span></span>|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|<span data-ttu-id="81abd-111">Získá nebo nastaví název adresáře, kde se ukládají a získávají dynamicky generované soubory.</span><span class="sxs-lookup"><span data-stu-id="81abd-111">Gets or sets the name of the directory where dynamically generated files are stored and accessed.</span></span>|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|<span data-ttu-id="81abd-112">Získá nebo nastaví cestu k souboru licencí, který je přidružený k této doméně.</span><span class="sxs-lookup"><span data-stu-id="81abd-112">Gets or sets the path to the license file that is associated with this domain.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|<span data-ttu-id="81abd-113">Získá nebo nastaví seznam adresářů, v kombinaci s <xref:System.AppDomainSetup.ApplicationBase%2A> adresář pro sběr dat pro soukromá sestavení.</span><span class="sxs-lookup"><span data-stu-id="81abd-113">Gets or sets the list of directories combined with the <xref:System.AppDomainSetup.ApplicationBase%2A> directory to probe for private assemblies.</span></span>|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|<span data-ttu-id="81abd-114">Získá nebo nastaví řetězcovou hodnotu, která zahrnutí nebo vyloučení <xref:System.AppDomainSetup.ApplicationBase%2A> z cesty pro hledání pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81abd-114">Gets or sets a string value that includes or excludes <xref:System.AppDomainSetup.ApplicationBase%2A> from the search path for the application.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|<span data-ttu-id="81abd-115">Získá nebo nastaví názvy adresářů, které obsahují sestavení bude vytvořena stínová kopie.</span><span class="sxs-lookup"><span data-stu-id="81abd-115">Gets or sets the names of the directories that contain assemblies to be shadow-copied.</span></span>|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|<span data-ttu-id="81abd-116">Získá nebo nastaví řetězec, který označuje, zda stínové kopírování sestavení je zapnout nebo vypnout.</span><span class="sxs-lookup"><span data-stu-id="81abd-116">Gets or sets a string that indicates whether shadow-copying is turned on or off.</span></span> <span data-ttu-id="81abd-117">Platné hodnoty jsou "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="81abd-117">Valid values are "true" or "false".</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81abd-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81abd-118">Remarks</span></span>  
 <span data-ttu-id="81abd-119">`IAppDomainSetup` Rozhraní odpovídá spravovanou <xref:System.IAppDomainSetup> rozhraní, které <xref:System.AppDomainSetup> typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="81abd-119">The `IAppDomainSetup` interface corresponds to the managed <xref:System.IAppDomainSetup> interface, which the <xref:System.AppDomainSetup> type implements.</span></span> <span data-ttu-id="81abd-120">Zobrazit <xref:System.IAppDomainSetup?displayProperty=nameWithType> podrobný popis jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81abd-120">See <xref:System.IAppDomainSetup?displayProperty=nameWithType> for detailed descriptions of its properties.</span></span>  
  
 <span data-ttu-id="81abd-121">`IAppDomainSetup` představuje informace o vazbu sestavení lze přidat do <xref:System.AppDomain> instance před její vytvoření.</span><span class="sxs-lookup"><span data-stu-id="81abd-121">`IAppDomainSetup` represents assembly binding information that can be added to an <xref:System.AppDomain> instance before its creation.</span></span> <span data-ttu-id="81abd-122">Například můžete nastavit hostitele <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost vytvořit kořenový adresář, který modul CLR (CLR) sondy pro spravovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="81abd-122">For example, a host can set the <xref:System.AppDomainSetup.ApplicationBase%2A> property to establish a root directory, which the common language runtime (CLR) probes for managed assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81abd-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81abd-123">Requirements</span></span>  
 <span data-ttu-id="81abd-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81abd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81abd-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81abd-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81abd-126">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81abd-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81abd-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81abd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81abd-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81abd-128">See also</span></span>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [<span data-ttu-id="81abd-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="81abd-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
