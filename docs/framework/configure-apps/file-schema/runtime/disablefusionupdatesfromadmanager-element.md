---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117447"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="11a93-102">Element \<disableFusionUpdatesFromADManager></span><span class="sxs-lookup"><span data-stu-id="11a93-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="11a93-103">Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.</span><span class="sxs-lookup"><span data-stu-id="11a93-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="11a93-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11a93-104">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11a93-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11a93-105">Attributes and Elements</span></span>  
 <span data-ttu-id="11a93-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11a93-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11a93-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="11a93-107">Attributes</span></span>  
  
|<span data-ttu-id="11a93-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="11a93-108">Attribute</span></span>|<span data-ttu-id="11a93-109">Popis</span><span class="sxs-lookup"><span data-stu-id="11a93-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11a93-110">enabled</span><span class="sxs-lookup"><span data-stu-id="11a93-110">enabled</span></span>|<span data-ttu-id="11a93-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="11a93-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="11a93-112">Určuje, jestli je zakázaná výchozí možnost přepsat nastavení fúze.</span><span class="sxs-lookup"><span data-stu-id="11a93-112">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="11a93-113">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="11a93-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="11a93-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="11a93-114">Value</span></span>|<span data-ttu-id="11a93-115">Description</span><span class="sxs-lookup"><span data-stu-id="11a93-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11a93-116">0</span><span class="sxs-lookup"><span data-stu-id="11a93-116">0</span></span>|<span data-ttu-id="11a93-117">Nepovolujte možnost přepsat nastavení fúze.</span><span class="sxs-lookup"><span data-stu-id="11a93-117">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="11a93-118">Toto je výchozí chování, počínaje .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="11a93-118">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="11a93-119">1</span><span class="sxs-lookup"><span data-stu-id="11a93-119">1</span></span>|<span data-ttu-id="11a93-120">Zakáže možnost přepsat nastavení fúze.</span><span class="sxs-lookup"><span data-stu-id="11a93-120">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="11a93-121">Tím se vrátí chování dřívějších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11a93-121">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11a93-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11a93-122">Child Elements</span></span>  
 <span data-ttu-id="11a93-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="11a93-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11a93-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11a93-124">Parent Elements</span></span>  
  
|<span data-ttu-id="11a93-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="11a93-125">Element</span></span>|<span data-ttu-id="11a93-126">Description</span><span class="sxs-lookup"><span data-stu-id="11a93-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="11a93-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11a93-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="11a93-128">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="11a93-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11a93-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11a93-129">Remarks</span></span>  
 <span data-ttu-id="11a93-130">Počínaje .NET Framework 4 je výchozím chováním umožnit <xref:System.AppDomainManager> objektu přepsat konfigurační nastavení pomocí <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> objektu, který je předán vaší implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody, v podtřídě třídy <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="11a93-130">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="11a93-131">U výchozí domény aplikace nastavení, které změníte, přepíše nastavení, která byla určena konfiguračním souborem aplikace.</span><span class="sxs-lookup"><span data-stu-id="11a93-131">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="11a93-132">Pro jiné aplikační domény přepíše nastavení konfigurace, která byla předána <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metodě nebo.</span><span class="sxs-lookup"><span data-stu-id="11a93-132">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="11a93-133">Můžete buď předat nové konfigurační informace, nebo předat hodnotu null ( `Nothing` v Visual Basic), aby se vyloučily informace o konfiguraci, které byly předány.</span><span class="sxs-lookup"><span data-stu-id="11a93-133">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="11a93-134">Nedávejte informace o konfiguraci do <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti i do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="11a93-134">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="11a93-135">Pokud předáte informace o konfiguraci do obou, informace, které předáte do <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti, budou ignorovány, protože <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda přepisuje informace o konfiguraci z konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="11a93-135">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="11a93-136">Použijete-li <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost, můžete metodě předat hodnotu null ( `Nothing` v Visual Basic), <xref:System.AppDomainSetup.SetConfigurationBytes%2A> aby se vyloučily všechny konfigurační bajty, které byly zadány ve volání <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody nebo.</span><span class="sxs-lookup"><span data-stu-id="11a93-136">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="11a93-137">Kromě informací o konfiguraci můžete změnit následující nastavení <xref:System.AppDomainSetup> objektu, který je předán vaší implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody: <xref:System.AppDomainSetup.ApplicationBase%2A> , <xref:System.AppDomainSetup.ApplicationName%2A> , <xref:System.AppDomainSetup.CachePath%2A> , <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> , <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A> , <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> , <xref:System.AppDomainSetup.DynamicBase%2A> , <xref:System.AppDomainSetup.LoaderOptimization%2A> , <xref:System.AppDomainSetup.PrivateBinPath%2A> , <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> , <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> a <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="11a93-137">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="11a93-138">Jako alternativu k použití `<disableFusionUpdatesFromADManager>` elementu můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="11a93-138">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="11a93-139">V registru vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework` a nastavte hodnotu na 1.</span><span class="sxs-lookup"><span data-stu-id="11a93-139">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="11a93-140">Na příkazovém řádku nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na 1.</span><span class="sxs-lookup"><span data-stu-id="11a93-140">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11a93-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="11a93-141">Example</span></span>  
 <span data-ttu-id="11a93-142">Následující příklad ukazuje, jak zakázat možnost přepsat nastavení fúze pomocí `<disableFusionUpdatesFromADManager>` elementu.</span><span class="sxs-lookup"><span data-stu-id="11a93-142">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11a93-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="11a93-143">See also</span></span>

- [<span data-ttu-id="11a93-144">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="11a93-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="11a93-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="11a93-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="11a93-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="11a93-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
