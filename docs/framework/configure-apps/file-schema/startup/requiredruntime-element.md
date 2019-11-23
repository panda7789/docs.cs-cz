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
# <a name="requiredruntime-element"></a><span data-ttu-id="0639d-102">\<element > requiredRuntime</span><span class="sxs-lookup"><span data-stu-id="0639d-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="0639d-103">Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="0639d-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="0639d-104">Tento prvek je zastaralý a neměl by se už používat.</span><span class="sxs-lookup"><span data-stu-id="0639d-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="0639d-105">Místo toho by se měl použít element [`supportedRuntime`](supportedruntime-element.md) .</span><span class="sxs-lookup"><span data-stu-id="0639d-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="0639d-106">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="0639d-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0639d-107">&nbsp;&nbsp;[ **\<po spuštění >** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="0639d-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="0639d-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="0639d-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0639d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0639d-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0639d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0639d-110">Attributes and elements</span></span>

<span data-ttu-id="0639d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0639d-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0639d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0639d-112">Attributes</span></span>

|<span data-ttu-id="0639d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0639d-113">Attribute</span></span>|<span data-ttu-id="0639d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0639d-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="0639d-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0639d-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0639d-116">Řetězcová hodnota, která určuje verzi .NET Framework, kterou tato aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="0639d-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="0639d-117">Hodnota řetězce se musí shodovat s názvem adresáře, který se nachází v kořenovém adresáři instalace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0639d-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="0639d-118">Obsah řetězcové hodnoty není analyzován.</span><span class="sxs-lookup"><span data-stu-id="0639d-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="0639d-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="0639d-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0639d-120">Určuje, zda běhový kód spuštění vyhledá v registru, aby bylo možné zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0639d-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="0639d-121">safemode – atribut</span><span class="sxs-lookup"><span data-stu-id="0639d-121">safemode attribute</span></span>

|<span data-ttu-id="0639d-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0639d-122">Value</span></span>|<span data-ttu-id="0639d-123">Popis</span><span class="sxs-lookup"><span data-stu-id="0639d-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0639d-124">Spouštěcí kód modulu runtime vyhledá v registru.</span><span class="sxs-lookup"><span data-stu-id="0639d-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="0639d-125">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0639d-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="0639d-126">Spouštěcí kód modulu runtime nevypadá v registru.</span><span class="sxs-lookup"><span data-stu-id="0639d-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0639d-127">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0639d-127">Child elements</span></span>

<span data-ttu-id="0639d-128">Žádné.</span><span class="sxs-lookup"><span data-stu-id="0639d-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0639d-129">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="0639d-129">Parent elements</span></span>

|<span data-ttu-id="0639d-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="0639d-130">Element</span></span>|<span data-ttu-id="0639d-131">Popis</span><span class="sxs-lookup"><span data-stu-id="0639d-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0639d-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0639d-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="0639d-133">Obsahuje element `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="0639d-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0639d-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0639d-134">Remarks</span></span>
 <span data-ttu-id="0639d-135">Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat prvek `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="0639d-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="0639d-136">Aplikace sestavené pomocí verze 1,1 nebo vyšší v modulu runtime musí používat element `<supportedRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="0639d-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="0639d-137">Použijete-li funkci [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) k určení konfiguračního souboru, je nutné použít element `<requiredRuntime>` pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0639d-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="0639d-138">Element `<supportedRuntime>` se při použití [CorBindToRuntimeByCfg –](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)ignoruje.</span><span class="sxs-lookup"><span data-stu-id="0639d-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="0639d-139">Řetězec atributu `version` musí odpovídat názvu instalační složky pro zadanou verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0639d-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="0639d-140">Tento řetězec není interpretován.</span><span class="sxs-lookup"><span data-stu-id="0639d-140">This string is not interpreted.</span></span> <span data-ttu-id="0639d-141">Pokud spouštěcí kód modulu runtime nenajde shodnou složku, modul runtime není načten. spouštěcí kód ukazuje chybovou zprávu a ukončí se.</span><span class="sxs-lookup"><span data-stu-id="0639d-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="0639d-142">Spouštěcí kód pro aplikaci, která je hostována v aplikaci Microsoft Internet Explorer, ignoruje prvek `<requiredRuntime>`.</span><span class="sxs-lookup"><span data-stu-id="0639d-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="0639d-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="0639d-143">Example</span></span>

<span data-ttu-id="0639d-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="0639d-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0639d-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0639d-145">See also</span></span>

- [<span data-ttu-id="0639d-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="0639d-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0639d-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0639d-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0639d-148">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="0639d-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
