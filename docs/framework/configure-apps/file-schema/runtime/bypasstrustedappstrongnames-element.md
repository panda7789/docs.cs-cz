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
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739093"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="df12e-102">\<element > bypassTrustedAppStrongNames</span><span class="sxs-lookup"><span data-stu-id="df12e-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="df12e-103">Určuje, zda se má obejít ověření silných názvů u sestavení s úplnou důvěryhodností, která jsou načtena do plně důvěryhodného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="df12e-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

<span data-ttu-id="df12e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="df12e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="df12e-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="df12e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="df12e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames >**</span><span class="sxs-lookup"><span data-stu-id="df12e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**</span></span>

## <a name="syntax"></a><span data-ttu-id="df12e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df12e-107">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df12e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="df12e-108">Attributes and Elements</span></span>

<span data-ttu-id="df12e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="df12e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="df12e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="df12e-110">Attributes</span></span>

|<span data-ttu-id="df12e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="df12e-111">Attribute</span></span>|<span data-ttu-id="df12e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="df12e-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="df12e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="df12e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="df12e-114">Určuje, zda je povolena funkce obcházení, která zabraňuje ověřování silných názvů pro sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="df12e-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="df12e-115">Když je tato funkce povolená, silné názvy se při načtení sestavení neověřují na správnost.</span><span class="sxs-lookup"><span data-stu-id="df12e-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="df12e-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="df12e-116">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="df12e-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="df12e-117">enabled Attribute</span></span>

|<span data-ttu-id="df12e-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="df12e-118">Value</span></span>|<span data-ttu-id="df12e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="df12e-119">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="df12e-120">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud jsou sestavení načtena do <xref:System.AppDomain>s plnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="df12e-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="df12e-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="df12e-121">This is the default.</span></span>|
|`false`|<span data-ttu-id="df12e-122">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti jsou ověřovány, když jsou sestavení načtena do <xref:System.AppDomain>plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="df12e-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="df12e-123">Podpis silného názvu je kontrolován pouze pro správnost signatury; Nejedná se o porovnání s jiným silným názvem pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="df12e-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="df12e-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="df12e-124">Child Elements</span></span>

<span data-ttu-id="df12e-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="df12e-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df12e-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="df12e-126">Parent Elements</span></span>

|<span data-ttu-id="df12e-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="df12e-127">Element</span></span>|<span data-ttu-id="df12e-128">Popis</span><span class="sxs-lookup"><span data-stu-id="df12e-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="df12e-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df12e-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="df12e-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="df12e-130">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="df12e-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df12e-131">Remarks</span></span>

<span data-ttu-id="df12e-132">Funkce obcházení silného názvu nezpůsobí režii ověřování podpisů silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="df12e-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="df12e-133">Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="df12e-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="df12e-134">Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimace zóny).</span><span class="sxs-lookup"><span data-stu-id="df12e-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="df12e-135">Načteno do plně důvěryhodného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="df12e-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="df12e-136">Načteno z umístění pod vlastností <xref:System.AppDomainSetup.ApplicationBase%2A> této <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="df12e-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="df12e-137">Nepodepsaná se zpožděním.</span><span class="sxs-lookup"><span data-stu-id="df12e-137">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="df12e-138">Pokud byla funkce obcházení vypnutá pro všechny aplikace v počítači pomocí klíče registru, nemá tento nastavení konfiguračního souboru žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="df12e-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="df12e-139">Další informace najdete v tématu [Postup: zákaz funkce obcházení silného názvu](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="df12e-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="df12e-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="df12e-140">Example</span></span>

<span data-ttu-id="df12e-141">Následující příklad ukazuje, jak určit chování, které ověřuje signaturu silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="df12e-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="df12e-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df12e-142">See also</span></span>

- [<span data-ttu-id="df12e-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="df12e-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="df12e-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="df12e-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="df12e-145">Postupy: zákaz funkce obcházení silného názvu</span><span class="sxs-lookup"><span data-stu-id="df12e-145">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
