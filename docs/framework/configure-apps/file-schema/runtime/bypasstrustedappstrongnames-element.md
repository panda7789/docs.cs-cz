---
title: Element <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 50e67e97d74b896a680cc18270d32aa7a8eb8035
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118178"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="1e4de-102">\<element > bypassTrustedAppStrongNames</span><span class="sxs-lookup"><span data-stu-id="1e4de-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="1e4de-103">Určuje, zda se má obejít ověření silných názvů u sestavení s úplnou důvěryhodností, která jsou načtena do plně důvěryhodného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1e4de-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

<span data-ttu-id="1e4de-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1e4de-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e4de-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e4de-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1e4de-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<bypassTrustedAppStrongNames >**</span><span class="sxs-lookup"><span data-stu-id="1e4de-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**</span></span>

## <a name="syntax"></a><span data-ttu-id="1e4de-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e4de-107">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e4de-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1e4de-108">Attributes and Elements</span></span>

<span data-ttu-id="1e4de-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1e4de-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e4de-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1e4de-110">Attributes</span></span>

|<span data-ttu-id="1e4de-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1e4de-111">Attribute</span></span>|<span data-ttu-id="1e4de-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1e4de-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1e4de-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1e4de-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1e4de-114">Určuje, zda je povolena funkce obcházení, která zabraňuje ověřování silných názvů pro sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1e4de-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="1e4de-115">Když je tato funkce povolená, silné názvy se při načtení sestavení neověřují na správnost.</span><span class="sxs-lookup"><span data-stu-id="1e4de-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="1e4de-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="1e4de-116">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="1e4de-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="1e4de-117">enabled Attribute</span></span>

|<span data-ttu-id="1e4de-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1e4de-118">Value</span></span>|<span data-ttu-id="1e4de-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1e4de-119">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="1e4de-120">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud jsou sestavení načtena do <xref:System.AppDomain>s plnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="1e4de-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="1e4de-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1e4de-121">This is the default.</span></span>|
|`false`|<span data-ttu-id="1e4de-122">Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti jsou ověřovány, když jsou sestavení načtena do <xref:System.AppDomain>plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1e4de-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="1e4de-123">Podpis silného názvu je kontrolován pouze pro správnost signatury; Nejedná se o porovnání s jiným silným názvem pro porovnání.</span><span class="sxs-lookup"><span data-stu-id="1e4de-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1e4de-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1e4de-124">Child Elements</span></span>

<span data-ttu-id="1e4de-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="1e4de-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1e4de-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e4de-126">Parent Elements</span></span>

|<span data-ttu-id="1e4de-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="1e4de-127">Element</span></span>|<span data-ttu-id="1e4de-128">Popis</span><span class="sxs-lookup"><span data-stu-id="1e4de-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1e4de-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1e4de-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1e4de-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1e4de-130">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e4de-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e4de-131">Remarks</span></span>

<span data-ttu-id="1e4de-132">Funkce obcházení silného názvu nezpůsobí režii ověřování podpisů silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1e4de-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="1e4de-133">Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1e4de-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="1e4de-134">Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimace zóny).</span><span class="sxs-lookup"><span data-stu-id="1e4de-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="1e4de-135">Načteno do plně důvěryhodného <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1e4de-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="1e4de-136">Načteno z umístění pod vlastností <xref:System.AppDomainSetup.ApplicationBase%2A> této <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1e4de-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="1e4de-137">Nepodepsaná se zpožděním.</span><span class="sxs-lookup"><span data-stu-id="1e4de-137">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="1e4de-138">Pokud byla funkce obcházení vypnutá pro všechny aplikace v počítači pomocí klíče registru, nemá tento nastavení konfiguračního souboru žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="1e4de-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="1e4de-139">Další informace najdete v tématu [Postup: zákaz funkce obcházení silného názvu](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="1e4de-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="1e4de-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e4de-140">Example</span></span>

<span data-ttu-id="1e4de-141">Následující příklad ukazuje, jak určit chování, které ověřuje signaturu silného názvu u sestavení s úplným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="1e4de-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="1e4de-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e4de-142">See also</span></span>

- [<span data-ttu-id="1e4de-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="1e4de-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1e4de-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="1e4de-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1e4de-145">Postupy: zákaz funkce obcházení silného názvu</span><span class="sxs-lookup"><span data-stu-id="1e4de-145">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
