---
title: <bypassTrustedAppStrongNames> Prvek
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c39d9a1e3da9cccb2f027e9597a6f2272d187ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179137"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="0a5c8-102">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="0a5c8-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="0a5c8-103">Určuje, zda obejít ověřování silných názvů na plně důvěryhodných sestavení, která jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="0a5c8-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="0a5c8-104">\<configuration></span></span>  
<span data-ttu-id="0a5c8-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="0a5c8-105">\<runtime></span></span>  
<span data-ttu-id="0a5c8-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="0a5c8-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a5c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a5c8-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a5c8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a5c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0a5c8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a5c8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a5c8-110">Attributes</span></span>  
  
|<span data-ttu-id="0a5c8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a5c8-111">Attribute</span></span>|<span data-ttu-id="0a5c8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0a5c8-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0a5c8-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0a5c8-114">Určuje, zda je povolena funkce jednorázové přihlášení, které se vyhýbají ověřování silných názvů pro plně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="0a5c8-115">Pokud je tato funkce povolena, silné názvy nejsou ověřit správnost při sestavení je načteno.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="0a5c8-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0a5c8-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0a5c8-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="0a5c8-118">Value</span><span class="sxs-lookup"><span data-stu-id="0a5c8-118">Value</span></span>|<span data-ttu-id="0a5c8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0a5c8-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="0a5c8-120">Podpisy silného názvu na sestavení s úplnou důvěryhodností nejsou ověřovány při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="0a5c8-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="0a5c8-122">Podpisy silného názvu na sestavení s úplnou důvěryhodností ověřovány při sestavení jsou načtena do plné důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="0a5c8-123">Podpis silného názvu se kontroluje jenom u podpisu správnosti; není porovnání s jinou silným názvem pro shodu.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a5c8-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a5c8-124">Child Elements</span></span>  
 <span data-ttu-id="0a5c8-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="0a5c8-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a5c8-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a5c8-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0a5c8-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a5c8-127">Element</span></span>|<span data-ttu-id="0a5c8-128">Popis</span><span class="sxs-lookup"><span data-stu-id="0a5c8-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0a5c8-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0a5c8-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a5c8-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a5c8-131">Remarks</span></span>  
 <span data-ttu-id="0a5c8-132">Funkce obejití silného názvu se vyhnete režii ověření podpisu se silným názvem sestavení úplného vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="0a5c8-133">Funkce obejití vztahuje na všechny sestavení je podepsáno silným názvem a, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="0a5c8-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="0a5c8-134">Bez plně důvěryhodné <xref:System.Security.Policy.StrongName> důkazy (třeba `MyComputer` legitimace zóny).</span><span class="sxs-lookup"><span data-stu-id="0a5c8-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="0a5c8-135">Načíst do plně důvěryhodné <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="0a5c8-136">Načtené z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost, která <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="0a5c8-137">Není zpožděním.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a5c8-138">Pokud funkce obejití jsou vypnuté pro všechny aplikace na počítači s použitím klíče registru, toto nastavení konfigurační soubor nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="0a5c8-139">Další informace najdete v tématu [jak: Zákaz funkce obejití silného názvu](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="0a5c8-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a5c8-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a5c8-140">Example</span></span>  
 <span data-ttu-id="0a5c8-141">Následující příklad ukazuje, jak můžete určit chování, která ověřuje podpis silného názvu v plně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="0a5c8-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a5c8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a5c8-142">See also</span></span>

- [<span data-ttu-id="0a5c8-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0a5c8-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="0a5c8-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0a5c8-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="0a5c8-145">Postupy: Zákaz funkce obejití silného názvu</span><span class="sxs-lookup"><span data-stu-id="0a5c8-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
