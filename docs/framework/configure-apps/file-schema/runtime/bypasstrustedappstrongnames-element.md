---
title: Element <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb198d6a19e25df4c86186d35aab3330c53121c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252770"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="ad8cc-102">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="ad8cc-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="ad8cc-103">Určuje, zda se má obejít ověření silných názvů u sestavení s úplným vztahem důvěryhodnosti, která jsou <xref:System.AppDomain>načtena do úplného vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
<span data-ttu-id="ad8cc-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad8cc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ad8cc-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ad8cc-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ad8cc-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames>**</span><span class="sxs-lookup"><span data-stu-id="ad8cc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8cc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad8cc-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad8cc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ad8cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ad8cc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad8cc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ad8cc-110">Attributes</span></span>  
  
|<span data-ttu-id="ad8cc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ad8cc-111">Attribute</span></span>|<span data-ttu-id="ad8cc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ad8cc-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ad8cc-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ad8cc-114">Určuje, zda je povolena funkce obcházení, která zabraňuje ověřování silných názvů pro sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="ad8cc-115">Když je tato funkce povolená, silné názvy se při načtení sestavení neověřují na správnost.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="ad8cc-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ad8cc-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ad8cc-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="ad8cc-118">Value</span><span class="sxs-lookup"><span data-stu-id="ad8cc-118">Value</span></span>|<span data-ttu-id="ad8cc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ad8cc-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="ad8cc-120">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud jsou sestavení načtena do plně důvěryhodného vztahu důvěryhodnosti <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="ad8cc-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="ad8cc-122">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti jsou ověřovány, když jsou sestavení <xref:System.AppDomain>načtena do plně důvěryhodného vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="ad8cc-123">Podpis silného názvu je kontrolován pouze pro správnost signatury; Nejedná se o porovnání s jiným silným názvem pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad8cc-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ad8cc-124">Child Elements</span></span>  
 <span data-ttu-id="ad8cc-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="ad8cc-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad8cc-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ad8cc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="ad8cc-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="ad8cc-127">Element</span></span>|<span data-ttu-id="ad8cc-128">Popis</span><span class="sxs-lookup"><span data-stu-id="ad8cc-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ad8cc-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ad8cc-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad8cc-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad8cc-131">Remarks</span></span>  
 <span data-ttu-id="ad8cc-132">Funkce obcházení silného názvu nezpůsobí režii ověřování podpisů silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="ad8cc-133">Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ad8cc-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
- <span data-ttu-id="ad8cc-134">Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimaci zóny).</span><span class="sxs-lookup"><span data-stu-id="ad8cc-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
- <span data-ttu-id="ad8cc-135">Načteno do plně důvěryhodného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="ad8cc-136">Načteno z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastností. <xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="ad8cc-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="ad8cc-137">Nepodepsaná se zpožděním.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-137">Not delay-signed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad8cc-138">Pokud byla funkce obcházení vypnutá pro všechny aplikace v počítači pomocí klíče registru, nemá tento nastavení konfiguračního souboru žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="ad8cc-139">Další informace najdete v tématu [jak: Zakažte funkci](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)obcházení silného názvu.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad8cc-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad8cc-140">Example</span></span>  
 <span data-ttu-id="ad8cc-141">Následující příklad ukazuje, jak určit chování, které ověřuje signaturu silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ad8cc-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad8cc-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad8cc-142">See also</span></span>

- [<span data-ttu-id="ad8cc-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ad8cc-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ad8cc-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ad8cc-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ad8cc-145">Postupy: Zakázat funkci obcházení silného názvu</span><span class="sxs-lookup"><span data-stu-id="ad8cc-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
