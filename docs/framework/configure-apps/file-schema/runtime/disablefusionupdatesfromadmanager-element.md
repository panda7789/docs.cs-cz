---
title: "&lt;disablefusionupdatesfromadmanager –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d3a1214b4aecf56c9a6440e31459573a5922676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a><span data-ttu-id="f845c-102">&lt;disablefusionupdatesfromadmanager –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="f845c-102">&lt;disableFusionUpdatesFromADManager&gt; Element</span></span>
<span data-ttu-id="f845c-103">Určuje, zda je výchozí chování, které je umožnit runtime hostitelů pro přepsání nastavení konfigurace pro doménu aplikace, zakázána.</span><span class="sxs-lookup"><span data-stu-id="f845c-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="f845c-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="f845c-104">\<configuration> Element</span></span>  
<span data-ttu-id="f845c-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="f845c-105">\<runtime> Element</span></span>  
<span data-ttu-id="f845c-106">\<disablefusionupdatesfromadmanager – ></span><span class="sxs-lookup"><span data-stu-id="f845c-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f845c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f845c-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f845c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f845c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f845c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f845c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f845c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f845c-110">Attributes</span></span>  
  
|<span data-ttu-id="f845c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f845c-111">Attribute</span></span>|<span data-ttu-id="f845c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f845c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f845c-113">povoleno</span><span class="sxs-lookup"><span data-stu-id="f845c-113">enabled</span></span>|<span data-ttu-id="f845c-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f845c-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f845c-115">Určuje, zda je výchozí možnost pro přepsání nastavení Fusion zakázána.</span><span class="sxs-lookup"><span data-stu-id="f845c-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f845c-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="f845c-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f845c-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f845c-117">Value</span></span>|<span data-ttu-id="f845c-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f845c-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f845c-119">0</span><span class="sxs-lookup"><span data-stu-id="f845c-119">0</span></span>|<span data-ttu-id="f845c-120">Možnost pro přepsání nastavení Fusion nezakazujte.</span><span class="sxs-lookup"><span data-stu-id="f845c-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="f845c-121">Toto je výchozí chování, počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f845c-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="f845c-122">1</span><span class="sxs-lookup"><span data-stu-id="f845c-122">1</span></span>|<span data-ttu-id="f845c-123">Zakažte možnost pro přepsání nastavení Fusion.</span><span class="sxs-lookup"><span data-stu-id="f845c-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="f845c-124">To obnoví chování starší verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f845c-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f845c-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f845c-125">Child Elements</span></span>  
 <span data-ttu-id="f845c-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="f845c-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f845c-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f845c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f845c-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="f845c-128">Element</span></span>|<span data-ttu-id="f845c-129">Popis</span><span class="sxs-lookup"><span data-stu-id="f845c-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f845c-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f845c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f845c-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f845c-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f845c-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f845c-132">Remarks</span></span>  
 <span data-ttu-id="f845c-133">Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], výchozí chování je umožnit <xref:System.AppDomainManager> objekt, který chcete přepsat nastavení konfigurace pomocí <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodu <xref:System.AppDomainSetup> objekt, který je předán do vaší implementace z <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda ve vašem podtřídou třídy <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="f845c-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="f845c-134">Pro výchozí doménu aplikace potlačí nastavení, která můžete změnit nastavení, která měla určeného konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f845c-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="f845c-135">Pro ostatní domény aplikace, se přepíší nastavení konfigurace, které byly předány <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="f845c-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f845c-136">Můžete předat nové informace o konfiguraci, nebo zadejte hodnotu null (`Nothing` v jazyce Visual Basic) k odstranění informace o konfiguraci, která byla předána.</span><span class="sxs-lookup"><span data-stu-id="f845c-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="f845c-137">Nepředávejte informace o konfiguraci na obě <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost a <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f845c-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="f845c-138">Pokud předáte i informace o konfiguraci, informace můžete předat <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost je ignorována, protože <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda přepsání informace o konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f845c-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="f845c-139">Pokud použijete <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost, můžete předat hodnotu null (`Nothing` v jazyce Visual Basic) k <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda odstranit všechny konfigurace bajtů, které byly zadány ve volání <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="f845c-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f845c-140">Kromě informací o konfiguraci, můžete změnit na následující nastavení <xref:System.AppDomainSetup> objekt, který je předán do vaší implementace nástroje <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, a <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="f845c-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="f845c-141">Jako alternativu k použití `<disableFusionUpdatesFromADManager>` elementu, můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="f845c-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="f845c-142">V registru, vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` pod `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1.</span><span class="sxs-lookup"><span data-stu-id="f845c-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="f845c-143">Na příkazovém řádku, nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na 1.</span><span class="sxs-lookup"><span data-stu-id="f845c-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f845c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f845c-144">Example</span></span>  
 <span data-ttu-id="f845c-145">Následující příklad ukazuje, jak zakázat možnost pro přepsání nastavení Fusion pomocí `<disableFusionUpdatesFromADManager>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f845c-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f845c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="f845c-146">See Also</span></span>  
 [<span data-ttu-id="f845c-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="f845c-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f845c-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f845c-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f845c-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="f845c-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
