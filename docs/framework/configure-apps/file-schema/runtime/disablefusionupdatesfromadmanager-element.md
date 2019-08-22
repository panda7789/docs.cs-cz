---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663774"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="9539a-102">\<disableFusionUpdatesFromADManager> Element</span><span class="sxs-lookup"><span data-stu-id="9539a-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="9539a-103">Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.</span><span class="sxs-lookup"><span data-stu-id="9539a-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="9539a-104">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="9539a-104">\<configuration> Element</span></span>  
<span data-ttu-id="9539a-105">\<Běhový > element</span><span class="sxs-lookup"><span data-stu-id="9539a-105">\<runtime> Element</span></span>  
<span data-ttu-id="9539a-106">\<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="9539a-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9539a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9539a-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9539a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9539a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9539a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9539a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9539a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="9539a-110">Attributes</span></span>  
  
|<span data-ttu-id="9539a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="9539a-111">Attribute</span></span>|<span data-ttu-id="9539a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9539a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9539a-113">enabled</span><span class="sxs-lookup"><span data-stu-id="9539a-113">enabled</span></span>|<span data-ttu-id="9539a-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9539a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="9539a-115">Určuje, jestli je zakázaná výchozí možnost přepsat nastavení fúze.</span><span class="sxs-lookup"><span data-stu-id="9539a-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9539a-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="9539a-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="9539a-117">Value</span><span class="sxs-lookup"><span data-stu-id="9539a-117">Value</span></span>|<span data-ttu-id="9539a-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9539a-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9539a-119">0</span><span class="sxs-lookup"><span data-stu-id="9539a-119">0</span></span>|<span data-ttu-id="9539a-120">Nepovolujte možnost přepsat nastavení fúze.</span><span class="sxs-lookup"><span data-stu-id="9539a-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="9539a-121">Toto je výchozí chování, počínaje .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9539a-121">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="9539a-122">1</span><span class="sxs-lookup"><span data-stu-id="9539a-122">1</span></span>|<span data-ttu-id="9539a-123">Zakáže možnost přepsat nastavení fúze.</span><span class="sxs-lookup"><span data-stu-id="9539a-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="9539a-124">Tím se vrátí chování dřívějších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9539a-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9539a-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9539a-125">Child Elements</span></span>  
 <span data-ttu-id="9539a-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="9539a-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9539a-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9539a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="9539a-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="9539a-128">Element</span></span>|<span data-ttu-id="9539a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="9539a-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9539a-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9539a-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9539a-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9539a-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9539a-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9539a-132">Remarks</span></span>  
 <span data-ttu-id="9539a-133">Počínaje .NET Framework 4 je <xref:System.AppDomainManager> výchozím chováním umožnit objektu přepsat konfigurační nastavení <xref:System.AppDomainSetup.ConfigurationFile%2A> pomocí vlastnosti <xref:System.AppDomainSetup> nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody objektu, který je předán vaší implementaci. metody v podtřídu třídy <xref:System.AppDomainManager>. <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9539a-133">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="9539a-134">U výchozí domény aplikace nastavení, které změníte, přepíše nastavení, která byla určena konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="9539a-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="9539a-135">Pro jiné aplikační domény přepíše nastavení konfigurace, která byla předána <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> metodě nebo. <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9539a-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9539a-136">Můžete buď předat nové konfigurační informace, nebo předat hodnotu null (`Nothing` v Visual Basic), aby se vyloučily informace o konfiguraci, které byly předány.</span><span class="sxs-lookup"><span data-stu-id="9539a-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="9539a-137">Nedávejte informace o konfiguraci do <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti i do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9539a-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="9539a-138">Pokud předáte informace o konfiguraci do obou, informace, které předáte <xref:System.AppDomainSetup.ConfigurationFile%2A> do vlastnosti, budou ignorovány <xref:System.AppDomainSetup.SetConfigurationBytes%2A> , protože metoda přepisuje informace o konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9539a-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="9539a-139">Použijete <xref:System.AppDomainSetup.ConfigurationFile%2A> -li vlastnost, můžete <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodě předat hodnotu null`Nothing` (v Visual Basic), aby se vyloučily všechny konfigurační bajty <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> , které byly zadány ve volání metody <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> nebo.</span><span class="sxs-lookup"><span data-stu-id="9539a-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9539a-140">Kromě informací o konfiguraci můžete změnit <xref:System.AppDomainSetup> následující nastavení objektu, který je předán vaší implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>,, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A> ,<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, ,<xref:System.AppDomainSetup.LoaderOptimization%2A>, ,<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>,a. <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.ShadowCopyFiles%2A></span><span class="sxs-lookup"><span data-stu-id="9539a-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="9539a-141">Jako alternativu k použití `<disableFusionUpdatesFromADManager>` elementu můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="9539a-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="9539a-142">V registru vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1.</span><span class="sxs-lookup"><span data-stu-id="9539a-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="9539a-143">Na příkazovém řádku nastavte proměnnou `COMPLUS_disableFusionUpdatesFromADManager` prostředí na 1.</span><span class="sxs-lookup"><span data-stu-id="9539a-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9539a-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="9539a-144">Example</span></span>  
 <span data-ttu-id="9539a-145">Následující příklad ukazuje, jak zakázat možnost přepsat nastavení fúze pomocí `<disableFusionUpdatesFromADManager>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9539a-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9539a-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9539a-146">See also</span></span>

- [<span data-ttu-id="9539a-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="9539a-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9539a-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9539a-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9539a-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="9539a-149">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
