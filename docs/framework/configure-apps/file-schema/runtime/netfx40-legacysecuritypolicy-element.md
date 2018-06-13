---
title: '&lt;NetFx40_LegacySecurityPolicy –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d9312d25842ccfcdf84e678d34b9bfde3fe7dd0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753980"
---
# <a name="ltnetfx40legacysecuritypolicygt-element"></a><span data-ttu-id="a02b9-102">&lt;NetFx40_LegacySecurityPolicy –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="a02b9-102">&lt;NetFx40_LegacySecurityPolicy&gt; Element</span></span>
<span data-ttu-id="a02b9-103">Určuje, zda modul runtime používá zásady zabezpečení (CA) přístupu starší verze kódu.</span><span class="sxs-lookup"><span data-stu-id="a02b9-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="a02b9-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a02b9-104">\<configuration></span></span>  
<span data-ttu-id="a02b9-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="a02b9-105">\<runtime></span></span>  
<span data-ttu-id="a02b9-106">< NetFx40_LegacySecurityPolicy – ></span><span class="sxs-lookup"><span data-stu-id="a02b9-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02b9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a02b9-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a02b9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a02b9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a02b9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a02b9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a02b9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a02b9-110">Attributes</span></span>  
  
|<span data-ttu-id="a02b9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a02b9-111">Attribute</span></span>|<span data-ttu-id="a02b9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a02b9-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a02b9-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a02b9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a02b9-114">Určuje, zda modul runtime používá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="a02b9-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a02b9-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a02b9-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="a02b9-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a02b9-116">Value</span></span>|<span data-ttu-id="a02b9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a02b9-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a02b9-118">Modul runtime nepoužívá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="a02b9-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="a02b9-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a02b9-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a02b9-120">Modul runtime používá starší zásadu CAS.</span><span class="sxs-lookup"><span data-stu-id="a02b9-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a02b9-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a02b9-121">Child Elements</span></span>  
 <span data-ttu-id="a02b9-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="a02b9-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a02b9-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a02b9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a02b9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="a02b9-124">Element</span></span>|<span data-ttu-id="a02b9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="a02b9-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a02b9-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a02b9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a02b9-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a02b9-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a02b9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a02b9-128">Remarks</span></span>  
 <span data-ttu-id="a02b9-129">V rozhraní .NET Framework verze 3.5 a starší verze je zásadu CAS vždy v platnost.</span><span class="sxs-lookup"><span data-stu-id="a02b9-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="a02b9-130">V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], musí být povolené zásady CAS.</span><span class="sxs-lookup"><span data-stu-id="a02b9-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="a02b9-131">Zásady CAS jsou specifické pro verzi.</span><span class="sxs-lookup"><span data-stu-id="a02b9-131">CAS policy is version-specific.</span></span> <span data-ttu-id="a02b9-132">Vlastní zásady certifikačních Autorit, které existují v dřívějších verzích rozhraní .NET Framework musí být zadány znovu v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a02b9-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="a02b9-133">Použití `<NetFx40_LegacySecurityPolicy>` elementu, který chcete [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] sestavení nemá vliv na [kód transparentní pro zabezpečení](../../../../../docs/framework/misc/security-transparent-code.md); pravidla transparentnosti platit stále.</span><span class="sxs-lookup"><span data-stu-id="a02b9-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a02b9-134">Použití `<NetFx40_LegacySecurityPolicy>` element může vést k postihy významně zvýšit výkon u nativních bitových kopií sestavení vytvořené [generátor (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) které nejsou nainstalovány v [globální mezipaměť sestavení ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="a02b9-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="a02b9-135">Snížení výkonu je způsobena nemožnost modulu runtime k načtení sestavení jako nativní bitové kopie, když se použije atribut, což vede k jejich se načíst sestavení jako v běhu.</span><span class="sxs-lookup"><span data-stu-id="a02b9-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a02b9-136">Pokud zadáte cílové verze rozhraní .NET Framework, která je starší než [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] v nastavení projektu pro projektu sady Visual Studio, bude možné povolit certifikační Autority zásad, včetně všechny vlastní zásady certifikační Autority, který jste zadali pro tuto verzi.</span><span class="sxs-lookup"><span data-stu-id="a02b9-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="a02b9-137">Ale nebudete moci používat nový [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] typy a členy.</span><span class="sxs-lookup"><span data-stu-id="a02b9-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="a02b9-138">Můžete také zadat dřívější verzi rozhraní .NET Framework pomocí [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) ve schématu nastavení spuštění ve vaší [konfiguračního souboru aplikace](../../../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="a02b9-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a02b9-139">Syntaxe souboru konfigurace je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="a02b9-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="a02b9-140">Jak je uvedené v oddílech syntaxe a příklad, měli byste použít syntaxi.</span><span class="sxs-lookup"><span data-stu-id="a02b9-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a02b9-141">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a02b9-141">Configuration File</span></span>  
 <span data-ttu-id="a02b9-142">Tento element může použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a02b9-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a02b9-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="a02b9-143">Example</span></span>  
 <span data-ttu-id="a02b9-144">Následující příklad ukazuje, jak povolte starší zásadu CAS pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a02b9-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a02b9-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="a02b9-145">See Also</span></span>  
 [<span data-ttu-id="a02b9-146">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a02b9-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="a02b9-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a02b9-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
