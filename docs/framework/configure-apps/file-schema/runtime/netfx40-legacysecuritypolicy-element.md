---
title: <NetFx40_LegacySecurityPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5bfa5449ece1b24d4f47fe3e77e36b26bbe430c
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689845"
---
# <a name="netfx40legacysecuritypolicy-element"></a><span data-ttu-id="a37fa-102">\<NetFx40_LegacySecurityPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="a37fa-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="a37fa-103">Určuje, zda modul runtime používá starší verzi kódu zásady zabezpečení přístupu (CAS).</span><span class="sxs-lookup"><span data-stu-id="a37fa-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

<span data-ttu-id="a37fa-104">\<Konfigurace > </span><span class="sxs-lookup"><span data-stu-id="a37fa-104">\<configuration></span></span>\
<span data-ttu-id="a37fa-105">\<modul runtime > </span><span class="sxs-lookup"><span data-stu-id="a37fa-105">\<runtime></span></span>\
<span data-ttu-id="a37fa-106">\<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="a37fa-106">\<NetFx40_LegacySecurityPolicy></span></span>

## <a name="syntax"></a><span data-ttu-id="a37fa-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a37fa-107">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a37fa-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a37fa-108">Attributes and Elements</span></span>

<span data-ttu-id="a37fa-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a37fa-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a37fa-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a37fa-110">Attributes</span></span>

|<span data-ttu-id="a37fa-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a37fa-111">Attribute</span></span>|<span data-ttu-id="a37fa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a37fa-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="a37fa-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a37fa-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a37fa-114">Určuje, zda modul runtime používá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="a37fa-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="a37fa-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a37fa-115">enabled Attribute</span></span>

|<span data-ttu-id="a37fa-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a37fa-116">Value</span></span>|<span data-ttu-id="a37fa-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a37fa-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a37fa-118">Modul runtime nepoužívá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="a37fa-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="a37fa-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a37fa-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="a37fa-120">Modul runtime používá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="a37fa-120">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a37fa-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a37fa-121">Child Elements</span></span>

<span data-ttu-id="a37fa-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="a37fa-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a37fa-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a37fa-123">Parent Elements</span></span>

|<span data-ttu-id="a37fa-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="a37fa-124">Element</span></span>|<span data-ttu-id="a37fa-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a37fa-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a37fa-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a37fa-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="a37fa-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a37fa-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a37fa-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a37fa-128">Remarks</span></span>

<span data-ttu-id="a37fa-129">V rozhraní .NET Framework verze 3.5 a starší verze zásad CAS je vždy v vliv.</span><span class="sxs-lookup"><span data-stu-id="a37fa-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="a37fa-130">V rozhraní .NET Framework 4 musí být povolené zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="a37fa-130">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="a37fa-131">Zásady CAS je specifické pro verzi.</span><span class="sxs-lookup"><span data-stu-id="a37fa-131">CAS policy is version-specific.</span></span> <span data-ttu-id="a37fa-132">Vlastní zásady CAS, které existují v dřívějších verzích rozhraní .NET Framework musí být zadány znovu v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a37fa-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="a37fa-133">Použití `<NetFx40_LegacySecurityPolicy>` nemá vliv na element na sestavení rozhraní .NET Framework 4 [kód transparentní pro zabezpečení](../../../../../docs/framework/misc/security-transparent-code.md); stále platí pravidla transparentnosti.</span><span class="sxs-lookup"><span data-stu-id="a37fa-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a37fa-134">Použití `<NetFx40_LegacySecurityPolicy>` element může způsobit snížení výkonu pro sestavení nativních bitových kopií, které jsou vytvořené [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) , která nejsou v nainstalovaná [globální mezipaměti sestavení ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="a37fa-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="a37fa-135">Snížení výkonu způsobuje nemožnost modul runtime k načtení sestavení jako nativní bitové kopie, když se atribut používá, což vede k jejich načtených sestavení jako just-in-time.</span><span class="sxs-lookup"><span data-stu-id="a37fa-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="a37fa-136">Pokud chcete zadat cílovou verzi rozhraní .NET Framework, která je starší než rozhraní .NET Framework 4 v nastavení projektu pro projekt sady Visual Studio, zásady CAS se povolí, včetně všechny vlastní zásady CAS, které jste zadali pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="a37fa-136">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="a37fa-137">Ale nebudete moct používat nové rozhraní .NET Framework 4 typy a členy.</span><span class="sxs-lookup"><span data-stu-id="a37fa-137">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="a37fa-138">Starší verzi rozhraní .NET Framework můžete také zadat pomocí [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) v schéma nastavení spouštění ve vaší [konfiguračního souboru aplikace](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="a37fa-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a37fa-139">Syntaxe konfigurační soubor je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="a37fa-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="a37fa-140">Jak je uvedeno v části Syntaxe a příkladu, měli byste použít syntaxi.</span><span class="sxs-lookup"><span data-stu-id="a37fa-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="a37fa-141">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a37fa-141">Configuration File</span></span>

<span data-ttu-id="a37fa-142">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a37fa-142">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="a37fa-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="a37fa-143">Example</span></span>

<span data-ttu-id="a37fa-144">Následující příklad ukazuje, jak povolte starší zásadu CAS pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a37fa-144">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a37fa-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a37fa-145">See also</span></span>

- [<span data-ttu-id="a37fa-146">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a37fa-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a37fa-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a37fa-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
