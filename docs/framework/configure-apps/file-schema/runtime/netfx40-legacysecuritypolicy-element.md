---
title: Element <NetFx40_LegacySecurityPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
ms.openlocfilehash: d5192eb56bb8b640544bdc52a0bb9d8a5277efef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116256"
---
# <a name="netfx40_legacysecuritypolicy-element"></a><span data-ttu-id="e675c-102">Element \<NetFx40_LegacySecurityPolicy></span><span class="sxs-lookup"><span data-stu-id="e675c-102">\<NetFx40_LegacySecurityPolicy> Element</span></span>

<span data-ttu-id="e675c-103">Určuje, zda modul runtime používá starší zásady zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="e675c-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_LegacySecurityPolicy>**  

## <a name="syntax"></a><span data-ttu-id="e675c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e675c-104">Syntax</span></span>

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e675c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e675c-105">Attributes and Elements</span></span>

<span data-ttu-id="e675c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e675c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e675c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e675c-107">Attributes</span></span>

|<span data-ttu-id="e675c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="e675c-108">Attribute</span></span>|<span data-ttu-id="e675c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e675c-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e675c-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e675c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="e675c-111">Určuje, zda modul runtime používá starší zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="e675c-111">Specifies whether the runtime uses legacy CAS policy.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="e675c-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="e675c-112">enabled Attribute</span></span>

|<span data-ttu-id="e675c-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e675c-113">Value</span></span>|<span data-ttu-id="e675c-114">Description</span><span class="sxs-lookup"><span data-stu-id="e675c-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e675c-115">Modul runtime nepoužívá starší zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="e675c-115">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="e675c-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="e675c-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="e675c-117">Modul runtime používá starší zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="e675c-117">The runtime uses legacy CAS policy.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e675c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e675c-118">Child Elements</span></span>

<span data-ttu-id="e675c-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="e675c-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e675c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e675c-120">Parent Elements</span></span>

|<span data-ttu-id="e675c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e675c-121">Element</span></span>|<span data-ttu-id="e675c-122">Description</span><span class="sxs-lookup"><span data-stu-id="e675c-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e675c-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e675c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e675c-124">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e675c-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e675c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e675c-125">Remarks</span></span>

<span data-ttu-id="e675c-126">V .NET Framework verze 3,5 a starších verzích je zásada CAS vždy platná.</span><span class="sxs-lookup"><span data-stu-id="e675c-126">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="e675c-127">V .NET Framework 4 musí být povolená zásada CAS.</span><span class="sxs-lookup"><span data-stu-id="e675c-127">In the .NET Framework 4, CAS policy must be enabled.</span></span>

<span data-ttu-id="e675c-128">Zásada CAS je specifická pro verzi.</span><span class="sxs-lookup"><span data-stu-id="e675c-128">CAS policy is version-specific.</span></span> <span data-ttu-id="e675c-129">Vlastní zásady CAS, které existují v dřívějších verzích .NET Framework, je nutné přezadat v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e675c-129">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the .NET Framework 4.</span></span>

<span data-ttu-id="e675c-130">Použití `<NetFx40_LegacySecurityPolicy>` elementu na sestavení .NET Framework 4 nemá vliv na [Kód transparentní z zabezpečení](../../../misc/security-transparent-code.md); pravidla transparentnosti jsou stále používána.</span><span class="sxs-lookup"><span data-stu-id="e675c-130">Applying the `<NetFx40_LegacySecurityPolicy>` element to a .NET Framework 4 assembly does not affect [security-transparent code](../../../misc/security-transparent-code.md); the transparency rules still apply.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e675c-131">Použití `<NetFx40_LegacySecurityPolicy>` prvku může mít za následek výrazné snížení výkonu pro sestavení nativních imagí vytvořená [generátorem nativních bitových kopií (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) , které nejsou nainstalované v [globální mezipaměti sestavení (GAC](../../../app-domains/gac.md)).</span><span class="sxs-lookup"><span data-stu-id="e675c-131">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../app-domains/gac.md).</span></span> <span data-ttu-id="e675c-132">Snížení výkonu je způsobeno neschopností modulu runtime načíst sestavení jako nativní bitové kopie, pokud je atribut použit, což vede k tomu, že jsou načítána jako sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="e675c-132">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>

> [!NOTE]
> <span data-ttu-id="e675c-133">Zadáte-li cílovou verzi .NET Framework, která je starší než .NET Framework 4 v nastavení projektu pro projekt aplikace Visual Studio, bude zásada CAS povolena, včetně všech vlastních zásad CAS, které jste zadali pro danou verzi.</span><span class="sxs-lookup"><span data-stu-id="e675c-133">If you specify a target .NET Framework version that is earlier than the .NET Framework 4 in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="e675c-134">Nebudete však moci použít nové typy a členy .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e675c-134">However, you will not be able to use new .NET Framework 4 types and members.</span></span> <span data-ttu-id="e675c-135">Můžete také zadat starší verzi .NET Framework pomocí [ \<supportedRuntime> elementu](../startup/supportedruntime-element.md) ve schématu nastavení spouštění v [konfiguračním souboru aplikace](../../index.md).</span><span class="sxs-lookup"><span data-stu-id="e675c-135">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e675c-136">Syntaxe konfiguračního souboru rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="e675c-136">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="e675c-137">Měli byste použít syntaxi, jak je uvedeno v části syntaxe a příklady.</span><span class="sxs-lookup"><span data-stu-id="e675c-137">You should use the syntax as provided in the Syntax and Example sections.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="e675c-138">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="e675c-138">Configuration File</span></span>

<span data-ttu-id="e675c-139">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="e675c-139">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="e675c-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="e675c-140">Example</span></span>

<span data-ttu-id="e675c-141">Následující příklad ukazuje, jak u aplikace povolit starší zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="e675c-141">The following example shows how to enable legacy CAS policy for an application.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e675c-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="e675c-142">See also</span></span>

- [<span data-ttu-id="e675c-143">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="e675c-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e675c-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e675c-144">Configuration File Schema</span></span>](../index.md)
