---
title: <startup> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153725"
---
# <a name="startup-element"></a><span data-ttu-id="b7366-102">\<spouštěcí> prvek</span><span class="sxs-lookup"><span data-stu-id="b7366-102">\<startup> element</span></span>

<span data-ttu-id="b7366-103">Určuje informace o spuštění běžného jazyka.</span><span class="sxs-lookup"><span data-stu-id="b7366-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="b7366-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="b7366-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b7366-105">&nbsp;&nbsp;**\<>pro spuštění**</span><span class="sxs-lookup"><span data-stu-id="b7366-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="b7366-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7366-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7366-107">Atributy a prvky</span><span class="sxs-lookup"><span data-stu-id="b7366-107">Attributes and elements</span></span>

 <span data-ttu-id="b7366-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7366-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7366-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="b7366-109">Attributes</span></span>

|<span data-ttu-id="b7366-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="b7366-110">Attribute</span></span>|<span data-ttu-id="b7366-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b7366-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="b7366-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b7366-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b7366-113">Určuje, zda má být povolena zásada aktivace za běhu rozhraní .NET Framework 2.0 nebo zda se mají použít zásady aktivace rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b7366-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="b7366-114">useLegacyV2RuntimeActivationPolicy, atribut</span><span class="sxs-lookup"><span data-stu-id="b7366-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="b7366-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b7366-115">Value</span></span>|<span data-ttu-id="b7366-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b7366-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="b7366-117">Povolte zásady aktivace runtime rozhraní .NET Framework 2.0 pro zvolený běhový čas, kterým je svázání starších technik aktivace runtime (například [funkce CorBindToRuntimeEx)](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)s runtime vybraným z konfiguračního souboru namísto jejich omezení pomocí clr verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="b7366-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="b7366-118">Pokud je tedy z konfiguračního souboru vybrána verze CLR verze 4 nebo novější, jsou sestavení v kombinovaném režimu vytvořená s dřívějšími verzemi rozhraní .NET Framework načtena s vybranou verzí CLR.</span><span class="sxs-lookup"><span data-stu-id="b7366-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="b7366-119">Nastavení této hodnoty zabrání clr verze 1.1 nebo CLR verze 2.0 z načtení do stejného procesu, účinně zakázání funkce v procesu side-by-side.</span><span class="sxs-lookup"><span data-stu-id="b7366-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="b7366-120">Použijte výchozí zásady aktivace pro rozhraní .NET Framework 4 a novější, což je umožnit starší mandatorní aktivační techniky pro načtení CLR verze 1.1 nebo 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="b7366-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="b7366-121">Nastavení této hodnoty zabrání načtení sestavení v smíšeném režimu do rozhraní .NET Framework 4 nebo novější, pokud nebyly vytvořeny s rozhraním .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="b7366-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="b7366-122">Tato hodnota je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b7366-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b7366-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b7366-123">Child elements</span></span>

|<span data-ttu-id="b7366-124">Element</span><span class="sxs-lookup"><span data-stu-id="b7366-124">Element</span></span>|<span data-ttu-id="b7366-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b7366-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7366-126">\<požadovaná>běhu</span><span class="sxs-lookup"><span data-stu-id="b7366-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="b7366-127">Určuje, že aplikace podporuje pouze verzi 1.0 běžného jazykového běhu.</span><span class="sxs-lookup"><span data-stu-id="b7366-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="b7366-128">Aplikace vytvořené s runtime verze 1.1 nebo novější by měl y použít \*\* \<supportedRuntime>\*\* element.</span><span class="sxs-lookup"><span data-stu-id="b7366-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="b7366-129">\<podporované>modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="b7366-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="b7366-130">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="b7366-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7366-131">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b7366-131">Parent elements</span></span>

|<span data-ttu-id="b7366-132">Element</span><span class="sxs-lookup"><span data-stu-id="b7366-132">Element</span></span>|<span data-ttu-id="b7366-133">Popis</span><span class="sxs-lookup"><span data-stu-id="b7366-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b7366-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7366-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7366-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b7366-135">Remarks</span></span>

 <span data-ttu-id="b7366-136">Prvek \*\* \<supportedRuntime>\*\* by měl být používán všemi aplikacemi vytvořenými pomocí verze 1.1 nebo novější modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b7366-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="b7366-137">Aplikace vytvořené pro podporu pouze verze 1.0 runtime musí používat \*\* \<prvek requiredRuntime>.\*\*</span><span class="sxs-lookup"><span data-stu-id="b7366-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="b7366-138">Spouštěcí kód aplikace hostované v aplikaci Microsoft Internet Explorer ignoruje \*\* \<spouštěcí>\*\* prvek a jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="b7366-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="b7366-139">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="b7366-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="b7366-140">Tento atribut je užitečný, pokud vaše aplikace používá starší aktivační cesty, jako je například [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty aktivovaly verzi 4 CLR namísto starší verze, nebo pokud je aplikace vytvořena s rozhraním .NET Framework 4, ale má závislost na sestavení ve smíšeném režimu vytvořeném se starší verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b7366-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="b7366-141">V těchto scénářích nastavte `true`atribut .</span><span class="sxs-lookup"><span data-stu-id="b7366-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="b7366-142">Nastavení atributu `true` zabránit CLR verze 1.1 nebo CLR verze 2.0 z načtení do stejného procesu, účinně zakázání v procesu side-by-side funkce (viz [Side-by-Side provedení pro COM Interop).](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b7366-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="b7366-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7366-143">Example</span></span>

 <span data-ttu-id="b7366-144">Následující příklad ukazuje, jak zadat verzi runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b7366-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b7366-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="b7366-145">See also</span></span>

- [<span data-ttu-id="b7366-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="b7366-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b7366-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b7366-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b7366-148">Postup: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="b7366-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="b7366-149">[Souběžné provádění pro kominterop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b7366-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="b7366-150">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="b7366-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
