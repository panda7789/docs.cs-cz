---
title: <requiredRuntime> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697489"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="34bdb-102">\<requiredRuntime> – element</span><span class="sxs-lookup"><span data-stu-id="34bdb-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="34bdb-103">Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="34bdb-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="34bdb-104">Tento prvek je zastaralý a neměl by se už používat.</span><span class="sxs-lookup"><span data-stu-id="34bdb-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="34bdb-105">[`supportedRuntime`](supportedruntime-element.md)Místo toho by se měl použít element.</span><span class="sxs-lookup"><span data-stu-id="34bdb-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="34bdb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34bdb-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34bdb-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34bdb-107">Attributes and elements</span></span>

<span data-ttu-id="34bdb-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34bdb-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="34bdb-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="34bdb-109">Attributes</span></span>

|<span data-ttu-id="34bdb-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="34bdb-110">Attribute</span></span>|<span data-ttu-id="34bdb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="34bdb-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="34bdb-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="34bdb-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="34bdb-113">Řetězcová hodnota, která určuje verzi .NET Framework, kterou tato aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="34bdb-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="34bdb-114">Hodnota řetězce se musí shodovat s názvem adresáře, který se nachází v kořenovém adresáři instalace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34bdb-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="34bdb-115">Obsah řetězcové hodnoty není analyzován.</span><span class="sxs-lookup"><span data-stu-id="34bdb-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="34bdb-116">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="34bdb-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="34bdb-117">Určuje, zda běhový kód spuštění vyhledá v registru, aby bylo možné zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="34bdb-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="34bdb-118">safemode – atribut</span><span class="sxs-lookup"><span data-stu-id="34bdb-118">safemode attribute</span></span>

|<span data-ttu-id="34bdb-119">Hodnota</span><span class="sxs-lookup"><span data-stu-id="34bdb-119">Value</span></span>|<span data-ttu-id="34bdb-120">Description</span><span class="sxs-lookup"><span data-stu-id="34bdb-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="34bdb-121">Spouštěcí kód modulu runtime vyhledá v registru.</span><span class="sxs-lookup"><span data-stu-id="34bdb-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="34bdb-122">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="34bdb-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="34bdb-123">Spouštěcí kód modulu runtime nevypadá v registru.</span><span class="sxs-lookup"><span data-stu-id="34bdb-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="34bdb-124">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="34bdb-124">Child elements</span></span>

<span data-ttu-id="34bdb-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="34bdb-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34bdb-126">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="34bdb-126">Parent elements</span></span>

|<span data-ttu-id="34bdb-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="34bdb-127">Element</span></span>|<span data-ttu-id="34bdb-128">Description</span><span class="sxs-lookup"><span data-stu-id="34bdb-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="34bdb-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34bdb-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="34bdb-130">Obsahuje `<requiredRuntime>` element.</span><span class="sxs-lookup"><span data-stu-id="34bdb-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="34bdb-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34bdb-131">Remarks</span></span>
 <span data-ttu-id="34bdb-132">Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat `<requiredRuntime>` element.</span><span class="sxs-lookup"><span data-stu-id="34bdb-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="34bdb-133">Aplikace sestavené pomocí verze 1,1 nebo novější v modulu runtime musí používat `<supportedRuntime>` element.</span><span class="sxs-lookup"><span data-stu-id="34bdb-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="34bdb-134">Použijete-li funkci [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) k určení konfiguračního souboru, je nutné použít `<requiredRuntime>` element pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="34bdb-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="34bdb-135">`<supportedRuntime>`Element je ignorován při použití [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="34bdb-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="34bdb-136">`version`Řetězec atributu musí odpovídat názvu instalační složky pro zadanou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34bdb-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="34bdb-137">Tento řetězec není interpretován.</span><span class="sxs-lookup"><span data-stu-id="34bdb-137">This string is not interpreted.</span></span> <span data-ttu-id="34bdb-138">Pokud spouštěcí kód modulu runtime nenajde shodnou složku, modul runtime není načten. spouštěcí kód ukazuje chybovou zprávu a ukončí se.</span><span class="sxs-lookup"><span data-stu-id="34bdb-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="34bdb-139">Spouštěcí kód pro aplikaci, která je hostována v aplikaci Microsoft Internet Explorer, ignoruje `<requiredRuntime>` prvek.</span><span class="sxs-lookup"><span data-stu-id="34bdb-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="34bdb-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="34bdb-140">Example</span></span>

<span data-ttu-id="34bdb-141">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="34bdb-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="34bdb-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="34bdb-142">See also</span></span>

- [<span data-ttu-id="34bdb-143">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="34bdb-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="34bdb-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="34bdb-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="34bdb-145">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="34bdb-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
