---
title: '&lt;requiredRuntime&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7cb5e29f3d7fc1faffdba01a5322f1883fca8af0
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837386"
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="6bfde-102">&lt;requiredRuntime&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="6bfde-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="6bfde-103">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="6bfde-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="6bfde-104">Tento element je zastaralá a již by nelze použít.</span><span class="sxs-lookup"><span data-stu-id="6bfde-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="6bfde-105">[ `supportedRuntime` ](supportedruntime-element.md) Element by měl místo toho použít.</span><span class="sxs-lookup"><span data-stu-id="6bfde-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="6bfde-106">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="6bfde-106">\<configuration></span></span>  
<span data-ttu-id="6bfde-107">\<Po spuštění ></span><span class="sxs-lookup"><span data-stu-id="6bfde-107">\<startup></span></span>  
<span data-ttu-id="6bfde-108">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="6bfde-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bfde-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bfde-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bfde-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6bfde-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6bfde-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6bfde-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bfde-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="6bfde-112">Attributes</span></span>  
  
|<span data-ttu-id="6bfde-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="6bfde-113">Attribute</span></span>|<span data-ttu-id="6bfde-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6bfde-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="6bfde-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6bfde-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6bfde-116">Řetězcovou hodnotu, která určuje verzi rozhraní .NET Framework, která podporuje tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6bfde-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="6bfde-117">Řetězcová hodnota musí odpovídat názvu adresáře v kořenu instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bfde-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="6bfde-118">Nejsou analyzovat obsah řetězcovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6bfde-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="6bfde-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="6bfde-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="6bfde-120">Určuje, zda modul runtime spouštěcí kód vyhledá z registru zjistit verzi modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6bfde-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="6bfde-121">safemode – atribut</span><span class="sxs-lookup"><span data-stu-id="6bfde-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="6bfde-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6bfde-122">Value</span></span>|<span data-ttu-id="6bfde-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6bfde-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6bfde-124">Spouštěcí kód modulu runtime hledá v registru.</span><span class="sxs-lookup"><span data-stu-id="6bfde-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="6bfde-125">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6bfde-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="6bfde-126">Spouštěcí kód modulu runtime nezjišťuje v registru.</span><span class="sxs-lookup"><span data-stu-id="6bfde-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6bfde-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6bfde-127">Child Elements</span></span>  
 <span data-ttu-id="6bfde-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="6bfde-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6bfde-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6bfde-129">Parent Elements</span></span>  
  
|<span data-ttu-id="6bfde-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="6bfde-130">Element</span></span>|<span data-ttu-id="6bfde-131">Popis</span><span class="sxs-lookup"><span data-stu-id="6bfde-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6bfde-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bfde-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="6bfde-133">Obsahuje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6bfde-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bfde-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bfde-134">Remarks</span></span>  
 <span data-ttu-id="6bfde-135">Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6bfde-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="6bfde-136">Aplikace vytvořené pomocí verze 1.1 nebo novější modul runtime musí použít `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6bfde-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bfde-137">Pokud používáte [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadejte konfigurační soubor, je nutné použít `<requiredRuntime>` – element pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6bfde-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="6bfde-138">`<supportedRuntime>` Prvek je ignorován při použití [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="6bfde-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="6bfde-139">`version` Atribut řetězců musí odpovídat názvu instalační složku pro zadaná verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bfde-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="6bfde-140">Tento řetězec nebyl interpretován.</span><span class="sxs-lookup"><span data-stu-id="6bfde-140">This string is not interpreted.</span></span> <span data-ttu-id="6bfde-141">Pokud kód při spuštění modulu runtime nelze najít odpovídající složky, modul runtime není načten. spouštěcí kód zobrazí chybovou zprávu a ukončí.</span><span class="sxs-lookup"><span data-stu-id="6bfde-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bfde-142">Ignoruje spouštěcí kód aplikace, která je hostována v aplikaci Internet Explorer `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6bfde-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bfde-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bfde-143">Example</span></span>  
 <span data-ttu-id="6bfde-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="6bfde-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bfde-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bfde-145">See Also</span></span>  
 [<span data-ttu-id="6bfde-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="6bfde-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="6bfde-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6bfde-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6bfde-148">\<PaveOver > Určení verze modulu Runtime, která k použití</span><span class="sxs-lookup"><span data-stu-id="6bfde-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
