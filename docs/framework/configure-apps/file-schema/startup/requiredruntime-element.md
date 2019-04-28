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
ms.openlocfilehash: 5e528a8b81fa3d9abc4f345d18f01e33f483a4a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673833"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="b2781-102">\<requiredRuntime > – element</span><span class="sxs-lookup"><span data-stu-id="b2781-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="b2781-103">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b2781-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="b2781-104">Tento element je zastaralá a již by nelze použít.</span><span class="sxs-lookup"><span data-stu-id="b2781-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="b2781-105">[ `supportedRuntime` ](supportedruntime-element.md) Element by měl místo toho použít.</span><span class="sxs-lookup"><span data-stu-id="b2781-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

<span data-ttu-id="b2781-106">\<configuration> \<startup> \<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="b2781-106">\<configuration> \<startup> \<requiredRuntime></span></span>

## <a name="syntax"></a><span data-ttu-id="b2781-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2781-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2781-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b2781-108">Attributes and elements</span></span>

<span data-ttu-id="b2781-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b2781-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2781-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b2781-110">Attributes</span></span>

|<span data-ttu-id="b2781-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b2781-111">Attribute</span></span>|<span data-ttu-id="b2781-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b2781-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="b2781-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b2781-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b2781-114">Řetězcovou hodnotu, která určuje verzi rozhraní .NET Framework, která podporuje tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b2781-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="b2781-115">Řetězcová hodnota musí odpovídat názvu adresáře v kořenu instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2781-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="b2781-116">Nejsou analyzovat obsah řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2781-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="b2781-117">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="b2781-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b2781-118">Určuje, zda modul runtime spouštěcí kód vyhledá z registru zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b2781-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="b2781-119">safemode – atribut</span><span class="sxs-lookup"><span data-stu-id="b2781-119">safemode attribute</span></span>

|<span data-ttu-id="b2781-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b2781-120">Value</span></span>|<span data-ttu-id="b2781-121">Popis</span><span class="sxs-lookup"><span data-stu-id="b2781-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="b2781-122">Spouštěcí kód modulu runtime hledá v registru.</span><span class="sxs-lookup"><span data-stu-id="b2781-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="b2781-123">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b2781-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="b2781-124">Spouštěcí kód modulu runtime nezjišťuje v registru.</span><span class="sxs-lookup"><span data-stu-id="b2781-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b2781-125">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b2781-125">Child elements</span></span>

<span data-ttu-id="b2781-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="b2781-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2781-127">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b2781-127">Parent elements</span></span>

|<span data-ttu-id="b2781-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="b2781-128">Element</span></span>|<span data-ttu-id="b2781-129">Popis</span><span class="sxs-lookup"><span data-stu-id="b2781-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b2781-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2781-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="b2781-131">Obsahuje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2781-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b2781-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2781-132">Remarks</span></span>
 <span data-ttu-id="b2781-133">Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2781-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="b2781-134">Aplikace vytvořené pomocí verze 1.1 nebo novější modul runtime musí použít `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2781-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="b2781-135">Pokud používáte [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadejte konfigurační soubor, je nutné použít `<requiredRuntime>` – element pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b2781-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="b2781-136">`<supportedRuntime>` Prvek je ignorován při použití [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="b2781-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="b2781-137">`version` Atribut řetězců musí odpovídat názvu instalační složku pro zadaná verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2781-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="b2781-138">Tento řetězec nebyl interpretován.</span><span class="sxs-lookup"><span data-stu-id="b2781-138">This string is not interpreted.</span></span> <span data-ttu-id="b2781-139">Pokud kód při spuštění modulu runtime nelze najít odpovídající složky, modul runtime není načten. spouštěcí kód zobrazí chybovou zprávu a ukončí.</span><span class="sxs-lookup"><span data-stu-id="b2781-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="b2781-140">Ignoruje spouštěcí kód aplikace, která je hostována v aplikaci Internet Explorer `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b2781-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="b2781-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2781-141">Example</span></span>

<span data-ttu-id="b2781-142">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b2781-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b2781-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2781-143">See also</span></span>

- [<span data-ttu-id="b2781-144">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="b2781-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b2781-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b2781-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b2781-146">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="b2781-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)