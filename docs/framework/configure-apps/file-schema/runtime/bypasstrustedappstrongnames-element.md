---
title: Element <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739093"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="53ee0-102">Element \<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="53ee0-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="53ee0-103">Určuje, zda se má obejít ověření silných názvů u sestavení s úplným vztahem důvěryhodnosti, která jsou načtena do úplného vztahu důvěryhodnosti <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="53ee0-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="53ee0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53ee0-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53ee0-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53ee0-105">Attributes and Elements</span></span>

<span data-ttu-id="53ee0-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53ee0-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="53ee0-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="53ee0-107">Attributes</span></span>

|<span data-ttu-id="53ee0-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="53ee0-108">Attribute</span></span>|<span data-ttu-id="53ee0-109">Popis</span><span class="sxs-lookup"><span data-stu-id="53ee0-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="53ee0-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="53ee0-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="53ee0-111">Určuje, zda je povolena funkce obcházení, která zabraňuje ověřování silných názvů pro sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="53ee0-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="53ee0-112">Když je tato funkce povolená, silné názvy se při načtení sestavení neověřují na správnost.</span><span class="sxs-lookup"><span data-stu-id="53ee0-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="53ee0-113">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="53ee0-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="53ee0-114">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="53ee0-114">enabled Attribute</span></span>

|<span data-ttu-id="53ee0-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="53ee0-115">Value</span></span>|<span data-ttu-id="53ee0-116">Description</span><span class="sxs-lookup"><span data-stu-id="53ee0-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="53ee0-117">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud jsou sestavení načtena do plně důvěryhodného vztahu důvěryhodnosti <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="53ee0-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="53ee0-118">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="53ee0-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="53ee0-119">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti jsou ověřovány, když jsou sestavení načtena do plně důvěryhodného vztahu důvěryhodnosti <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="53ee0-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="53ee0-120">Podpis silného názvu je kontrolován pouze pro správnost signatury; Nejedná se o porovnání s jiným silným názvem pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="53ee0-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="53ee0-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53ee0-121">Child Elements</span></span>

<span data-ttu-id="53ee0-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="53ee0-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53ee0-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53ee0-123">Parent Elements</span></span>

|<span data-ttu-id="53ee0-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="53ee0-124">Element</span></span>|<span data-ttu-id="53ee0-125">Description</span><span class="sxs-lookup"><span data-stu-id="53ee0-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="53ee0-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53ee0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="53ee0-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="53ee0-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="53ee0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53ee0-128">Remarks</span></span>

<span data-ttu-id="53ee0-129">Funkce obcházení silného názvu nezpůsobí režii ověřování podpisů silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="53ee0-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="53ee0-130">Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="53ee0-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="53ee0-131">Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimaci zóny).</span><span class="sxs-lookup"><span data-stu-id="53ee0-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="53ee0-132">Načteno do plně důvěryhodného <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="53ee0-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="53ee0-133">Načteno z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastností <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="53ee0-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="53ee0-134">Nepodepsaná se zpožděním.</span><span class="sxs-lookup"><span data-stu-id="53ee0-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="53ee0-135">Pokud byla funkce obcházení vypnutá pro všechny aplikace v počítači pomocí klíče registru, nemá tento nastavení konfiguračního souboru žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="53ee0-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="53ee0-136">Další informace najdete v tématu [Postup: zákaz funkce obcházení silného názvu](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="53ee0-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="53ee0-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="53ee0-137">Example</span></span>

<span data-ttu-id="53ee0-138">Následující příklad ukazuje, jak určit chování, které ověřuje signaturu silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="53ee0-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="53ee0-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="53ee0-139">See also</span></span>

- [<span data-ttu-id="53ee0-140">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="53ee0-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="53ee0-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="53ee0-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="53ee0-142">Postupy: zákaz funkce obcházení silného názvu</span><span class="sxs-lookup"><span data-stu-id="53ee0-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
