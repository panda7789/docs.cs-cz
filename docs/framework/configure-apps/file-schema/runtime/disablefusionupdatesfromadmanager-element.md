---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27c8c1cac68aca1c40826ff549d62d9636d9b0c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085880"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="9492f-102">\<disableFusionUpdatesFromADManager> Element</span><span class="sxs-lookup"><span data-stu-id="9492f-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="9492f-103">Určuje, zda je výchozí chování, které je umožnit hostitelský modul runtime pro přepsání nastavení konfigurace pro doménu aplikace, zakázáno.</span><span class="sxs-lookup"><span data-stu-id="9492f-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="9492f-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="9492f-104">\<configuration> Element</span></span>  
<span data-ttu-id="9492f-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="9492f-105">\<runtime> Element</span></span>  
<span data-ttu-id="9492f-106">\<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="9492f-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9492f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9492f-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9492f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9492f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9492f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9492f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9492f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9492f-110">Attributes</span></span>  
  
|<span data-ttu-id="9492f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="9492f-111">Attribute</span></span>|<span data-ttu-id="9492f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9492f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9492f-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="9492f-113">enabled</span></span>|<span data-ttu-id="9492f-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9492f-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9492f-115">Určuje, zda je výchozí možnost přepsat nastavení Fusion zakázaný.</span><span class="sxs-lookup"><span data-stu-id="9492f-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9492f-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="9492f-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="9492f-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9492f-117">Value</span></span>|<span data-ttu-id="9492f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9492f-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9492f-119">0</span><span class="sxs-lookup"><span data-stu-id="9492f-119">0</span></span>|<span data-ttu-id="9492f-120">Nezakazujte přepsat nastavení Fusion.</span><span class="sxs-lookup"><span data-stu-id="9492f-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="9492f-121">Jedná se o výchozí chování, počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9492f-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="9492f-122">1</span><span class="sxs-lookup"><span data-stu-id="9492f-122">1</span></span>|<span data-ttu-id="9492f-123">Zakážete možnost přepsat nastavení Fusion.</span><span class="sxs-lookup"><span data-stu-id="9492f-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="9492f-124">To obnoví na chování starších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9492f-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9492f-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9492f-125">Child Elements</span></span>  
 <span data-ttu-id="9492f-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="9492f-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9492f-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9492f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9492f-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="9492f-128">Element</span></span>|<span data-ttu-id="9492f-129">Popis</span><span class="sxs-lookup"><span data-stu-id="9492f-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9492f-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9492f-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9492f-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9492f-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9492f-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9492f-132">Remarks</span></span>  
 <span data-ttu-id="9492f-133">Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], výchozí chování je umožnit <xref:System.AppDomainManager> určeného k přepsání nastavení konfigurace s použitím <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodu <xref:System.AppDomainSetup> objekt, který je předán vaší implementace nástroje <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metodu do vaší podtřídy aplikace <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="9492f-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="9492f-134">Pro výchozí domény aplikace přepíší nastavení, které můžete změnit nastavení zadané v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9492f-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="9492f-135">Pro další aplikační domény, mohou přepsat nastavení konfigurace, které bylo předáno <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9492f-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9492f-136">Můžete předat nové informace o konfiguraci, nebo předat hodnotu null (`Nothing` v jazyce Visual Basic) Chcete-li odstranit informace o konfiguraci, která byla předána.</span><span class="sxs-lookup"><span data-stu-id="9492f-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="9492f-137">Nepředávejte informace o konfiguraci pro obě <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost a <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9492f-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="9492f-138">Pokud předáte informace o konfiguraci na obě, informace můžete předat <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost se ignoruje, protože <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda přepíše informace o konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9492f-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="9492f-139">Pokud používáte <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastností, můžete předat hodnotu null (`Nothing` v jazyce Visual Basic) na <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody, chcete-li odstranit všechny konfigurace bajtů, které byly zadány při volání <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> – metoda.</span><span class="sxs-lookup"><span data-stu-id="9492f-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9492f-140">Kromě informací o konfiguraci, můžete změnit následující nastavení na <xref:System.AppDomainSetup> objekt, který je předán implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, a <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="9492f-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="9492f-141">Jako alternativu k použití `<disableFusionUpdatesFromADManager>` element, můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="9492f-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="9492f-142">V registru, vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` pod `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1.</span><span class="sxs-lookup"><span data-stu-id="9492f-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="9492f-143">Na příkazovém řádku, nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="9492f-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9492f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="9492f-144">Example</span></span>  
 <span data-ttu-id="9492f-145">Následující příklad ukazuje, jak zakázat pomocí přepsání nastavení Fusion `<disableFusionUpdatesFromADManager>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9492f-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9492f-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9492f-146">See also</span></span>

- [<span data-ttu-id="9492f-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="9492f-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="9492f-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9492f-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="9492f-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="9492f-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
