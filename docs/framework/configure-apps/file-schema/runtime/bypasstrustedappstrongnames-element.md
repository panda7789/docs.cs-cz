---
title: "&lt;bypasstrustedappstrongnames –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b3e1cb839e9e7fd81a5452c0e034c3552b230cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a><span data-ttu-id="30f39-102">&lt;bypasstrustedappstrongnames –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="30f39-102">&lt;bypassTrustedAppStrongNames&gt; Element</span></span>
<span data-ttu-id="30f39-103">Určuje, jestli se má vynechat ověřování silné názvy na plné důvěryhodnosti sestavení, která jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="30f39-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="30f39-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="30f39-104">\<configuration></span></span>  
<span data-ttu-id="30f39-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="30f39-105">\<runtime></span></span>  
<span data-ttu-id="30f39-106">\<bypasstrustedappstrongnames – ></span><span class="sxs-lookup"><span data-stu-id="30f39-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30f39-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30f39-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30f39-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="30f39-108">Attributes and Elements</span></span>  
 <span data-ttu-id="30f39-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="30f39-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30f39-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="30f39-110">Attributes</span></span>  
  
|<span data-ttu-id="30f39-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="30f39-111">Attribute</span></span>|<span data-ttu-id="30f39-112">Popis</span><span class="sxs-lookup"><span data-stu-id="30f39-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="30f39-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="30f39-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="30f39-114">Určuje, zda je povolena funkce jednorázové přihlášení, která zabraňuje ověřování silných názvů pro sestavení plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="30f39-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="30f39-115">Pokud je tato funkce povolena, nejsou silné názvy ověřit správnost, když je načteno sestavení.</span><span class="sxs-lookup"><span data-stu-id="30f39-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="30f39-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="30f39-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="30f39-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="30f39-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="30f39-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="30f39-118">Value</span></span>|<span data-ttu-id="30f39-119">Popis</span><span class="sxs-lookup"><span data-stu-id="30f39-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="30f39-120">Nejsou k ověřování podpisů silného názvu sestavení plné důvěryhodnosti při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="30f39-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="30f39-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="30f39-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="30f39-122">Jsou k ověřování podpisů silného názvu sestavení plné důvěryhodnosti při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="30f39-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="30f39-123">Podpis silného názvu, se kontroluje jenom na podpis správnost; není porovná jiné silný název pro shodu.</span><span class="sxs-lookup"><span data-stu-id="30f39-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30f39-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="30f39-124">Child Elements</span></span>  
 <span data-ttu-id="30f39-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="30f39-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30f39-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="30f39-126">Parent Elements</span></span>  
  
|<span data-ttu-id="30f39-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="30f39-127">Element</span></span>|<span data-ttu-id="30f39-128">Popis</span><span class="sxs-lookup"><span data-stu-id="30f39-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30f39-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30f39-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="30f39-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="30f39-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30f39-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30f39-131">Remarks</span></span>  
 <span data-ttu-id="30f39-132">Funkce obejití silného názvu zabraňuje režii ověřit podpis silného názvu sestavení plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="30f39-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="30f39-133">Funkce obcházení vztahuje na všechny sestavení, který je podepsaný se silným názvem, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="30f39-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="30f39-134">Bez plně důvěryhodná <xref:System.Security.Policy.StrongName> důkaz (například má `MyComputer` zónu důkaz).</span><span class="sxs-lookup"><span data-stu-id="30f39-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="30f39-135">Načíst do plně důvěryhodné <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="30f39-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="30f39-136">Načtené z umístění v rámci <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost této <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="30f39-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="30f39-137">Podepsáno bez zpoždění.</span><span class="sxs-lookup"><span data-stu-id="30f39-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30f39-138">Pokud funkce jednorázové přihlášení je vypnutá pro všechny aplikace v počítači pomocí klíče registru, toto nastavení konfigurační soubor nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="30f39-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="30f39-139">Další informace najdete v tématu [postupy: Zákaz funkce obejití silného názvu](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="30f39-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30f39-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="30f39-140">Example</span></span>  
 <span data-ttu-id="30f39-141">Následující příklad ukazuje, jak určit způsob chování, která ověřuje podpis silného názvu sestavení plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="30f39-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30f39-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="30f39-142">See Also</span></span>  
 [<span data-ttu-id="30f39-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="30f39-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="30f39-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="30f39-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="30f39-145">Postupy: Zákaz funkce obejití silného názvu</span><span class="sxs-lookup"><span data-stu-id="30f39-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
