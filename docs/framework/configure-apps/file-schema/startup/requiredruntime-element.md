---
title: '&lt;requiredRuntime –&gt; – Element'
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
manager: markl
ms.openlocfilehash: 184547dd47e728f17f28105e74b2ca67c1436efc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="f4ebb-102">&lt;requiredRuntime –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="f4ebb-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="f4ebb-103">Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f4ebb-104">Tento element je zastaralá a již by nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="f4ebb-105">[ `supportedRuntime` ](supportedruntime-element.md) Element by měl být místo toho použít.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="f4ebb-106">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f4ebb-106">\<configuration></span></span>  
<span data-ttu-id="f4ebb-107">\<spuštění ></span><span class="sxs-lookup"><span data-stu-id="f4ebb-107">\<startup></span></span>  
<span data-ttu-id="f4ebb-108">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="f4ebb-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ebb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4ebb-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4ebb-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f4ebb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f4ebb-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4ebb-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f4ebb-112">Attributes</span></span>  
  
|<span data-ttu-id="f4ebb-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f4ebb-113">Attribute</span></span>|<span data-ttu-id="f4ebb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f4ebb-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="f4ebb-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f4ebb-116">Hodnotu řetězce, který určuje verzi rozhraní .NET Framework, který podporuje tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="f4ebb-117">Řetězcová hodnota musí odpovídat názvu adresáře najít v kořenovém adresáři instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="f4ebb-118">Nejsou analyzovat obsah hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="f4ebb-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f4ebb-120">Určuje, zda kód pro spuštění modulu runtime hledat zjistěte verzi modulu runtime v registru.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="f4ebb-121">safemode atribut</span><span class="sxs-lookup"><span data-stu-id="f4ebb-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="f4ebb-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f4ebb-122">Value</span></span>|<span data-ttu-id="f4ebb-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f4ebb-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f4ebb-124">Kód spuštění modulu runtime hledá v registru.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="f4ebb-125">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="f4ebb-126">Kód spuštění modulu runtime nezjišťuje v registru.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4ebb-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f4ebb-127">Child Elements</span></span>  
 <span data-ttu-id="f4ebb-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="f4ebb-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4ebb-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f4ebb-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f4ebb-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="f4ebb-130">Element</span></span>|<span data-ttu-id="f4ebb-131">Popis</span><span class="sxs-lookup"><span data-stu-id="f4ebb-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f4ebb-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="f4ebb-133">Obsahuje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4ebb-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4ebb-134">Remarks</span></span>  
 <span data-ttu-id="f4ebb-135">Musíte použít aplikace založené na podporu pouze verze 1.0 modulu runtime `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="f4ebb-136">Musíte použít aplikace vytvořené pomocí verze 1.1 nebo novější modulu runtime `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ebb-137">Pokud použijete [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadat konfigurační soubor, je nutné použít `<requiredRuntime>` element pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="f4ebb-138">`<supportedRuntime>` Element se ignoruje, pokud používáte [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="f4ebb-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="f4ebb-139">`version` Řetězec atributu musí odpovídat názvu instalační složku pro určenou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="f4ebb-140">Tento řetězec nebyl interpretován.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-140">This string is not interpreted.</span></span> <span data-ttu-id="f4ebb-141">Pokud kód pro spuštění modulu runtime nenajde odpovídající složku, není načítání modulu runtime; kód spuštění zobrazí chybovou zprávu a ukončí.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4ebb-142">Kód spuštění pro aplikaci, která je hostitelem aplikace Microsoft Internet Explorer ignoruje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4ebb-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4ebb-143">Example</span></span>  
 <span data-ttu-id="f4ebb-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f4ebb-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4ebb-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4ebb-145">See Also</span></span>  
 [<span data-ttu-id="f4ebb-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="f4ebb-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="f4ebb-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f4ebb-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f4ebb-148">\<PaveOver > Zadání kterou verzi modulu Runtime pro použití</span><span class="sxs-lookup"><span data-stu-id="f4ebb-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
