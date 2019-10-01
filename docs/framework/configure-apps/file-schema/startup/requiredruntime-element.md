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
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697489"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="714cd-102">@no__t – element > 0requiredRuntime</span><span class="sxs-lookup"><span data-stu-id="714cd-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="714cd-103">Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="714cd-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="714cd-104">Tento prvek je zastaralý a neměl by se už používat.</span><span class="sxs-lookup"><span data-stu-id="714cd-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="714cd-105">Místo toho by se měl použít prvek [`supportedRuntime`](supportedruntime-element.md) .</span><span class="sxs-lookup"><span data-stu-id="714cd-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="714cd-106"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="714cd-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="714cd-107">&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="714cd-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="714cd-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="714cd-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="714cd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="714cd-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="714cd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="714cd-110">Attributes and elements</span></span>

<span data-ttu-id="714cd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="714cd-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="714cd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="714cd-112">Attributes</span></span>

|<span data-ttu-id="714cd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="714cd-113">Attribute</span></span>|<span data-ttu-id="714cd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="714cd-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="714cd-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="714cd-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="714cd-116">Řetězcová hodnota, která určuje verzi .NET Framework, kterou tato aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="714cd-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="714cd-117">Hodnota řetězce se musí shodovat s názvem adresáře, který se nachází v kořenovém adresáři instalace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="714cd-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="714cd-118">Obsah řetězcové hodnoty není analyzován.</span><span class="sxs-lookup"><span data-stu-id="714cd-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="714cd-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="714cd-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="714cd-120">Určuje, zda běhový kód spuštění vyhledá v registru, aby bylo možné zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="714cd-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="714cd-121">safemode – atribut</span><span class="sxs-lookup"><span data-stu-id="714cd-121">safemode attribute</span></span>

|<span data-ttu-id="714cd-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="714cd-122">Value</span></span>|<span data-ttu-id="714cd-123">Popis</span><span class="sxs-lookup"><span data-stu-id="714cd-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="714cd-124">Spouštěcí kód modulu runtime vyhledá v registru.</span><span class="sxs-lookup"><span data-stu-id="714cd-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="714cd-125">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="714cd-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="714cd-126">Spouštěcí kód modulu runtime nevypadá v registru.</span><span class="sxs-lookup"><span data-stu-id="714cd-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="714cd-127">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="714cd-127">Child elements</span></span>

<span data-ttu-id="714cd-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="714cd-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="714cd-129">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="714cd-129">Parent elements</span></span>

|<span data-ttu-id="714cd-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="714cd-130">Element</span></span>|<span data-ttu-id="714cd-131">Popis</span><span class="sxs-lookup"><span data-stu-id="714cd-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="714cd-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="714cd-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="714cd-133">Obsahuje prvek `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="714cd-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="714cd-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="714cd-134">Remarks</span></span>
 <span data-ttu-id="714cd-135">Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat prvek `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="714cd-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="714cd-136">Aplikace sestavené pomocí verze 1,1 nebo novější v modulu runtime musí používat prvek `<supportedRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="714cd-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="714cd-137">Použijete-li funkci [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) k určení konfiguračního souboru, je nutné použít prvek `<requiredRuntime>` pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="714cd-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="714cd-138">Element `<supportedRuntime>` se při použití [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)ignoruje.</span><span class="sxs-lookup"><span data-stu-id="714cd-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="714cd-139">Řetězec atributu `version` se musí shodovat s názvem instalační složky pro zadanou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="714cd-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="714cd-140">Tento řetězec není interpretován.</span><span class="sxs-lookup"><span data-stu-id="714cd-140">This string is not interpreted.</span></span> <span data-ttu-id="714cd-141">Pokud spouštěcí kód modulu runtime nenajde shodnou složku, modul runtime není načten. spouštěcí kód ukazuje chybovou zprávu a ukončí se.</span><span class="sxs-lookup"><span data-stu-id="714cd-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="714cd-142">Spouštěcí kód pro aplikaci, která je hostována v aplikaci Microsoft Internet Explorer, ignoruje prvek `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="714cd-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="714cd-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="714cd-143">Example</span></span>

<span data-ttu-id="714cd-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="714cd-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="714cd-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="714cd-145">See also</span></span>

- [<span data-ttu-id="714cd-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="714cd-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="714cd-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="714cd-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="714cd-148">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="714cd-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
