---
title: "&lt;requiredRuntime –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 12be2350cb123407b2f71d1f5f07e836ccddb9c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="f6816-102">&lt;requiredRuntime –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="f6816-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="f6816-103">Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f6816-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f6816-104">Tento element je zastaralá a již by nelze použít.</span><span class="sxs-lookup"><span data-stu-id="f6816-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="f6816-105">[ `supportedRuntime` ](supportedruntime-element.md) Element by měl být místo toho použít.</span><span class="sxs-lookup"><span data-stu-id="f6816-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="f6816-106">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f6816-106">\<configuration></span></span>  
<span data-ttu-id="f6816-107">\<spuštění ></span><span class="sxs-lookup"><span data-stu-id="f6816-107">\<startup></span></span>  
<span data-ttu-id="f6816-108">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="f6816-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6816-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6816-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6816-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6816-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6816-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f6816-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6816-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6816-112">Attributes</span></span>  
  
|<span data-ttu-id="f6816-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f6816-113">Attribute</span></span>|<span data-ttu-id="f6816-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f6816-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="f6816-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f6816-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f6816-116">Hodnotu řetězce, který určuje verzi rozhraní .NET Framework, který podporuje tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f6816-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="f6816-117">Řetězcová hodnota musí odpovídat názvu adresáře najít v kořenovém adresáři instalace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6816-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="f6816-118">Nejsou analyzovat obsah hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="f6816-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="f6816-119">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f6816-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f6816-120">Určuje, zda kód pro spuštění modulu runtime hledat zjistěte verzi modulu runtime v registru.</span><span class="sxs-lookup"><span data-stu-id="f6816-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="f6816-121">safemode atribut</span><span class="sxs-lookup"><span data-stu-id="f6816-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="f6816-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f6816-122">Value</span></span>|<span data-ttu-id="f6816-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f6816-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f6816-124">Kód spuštění modulu runtime hledá v registru.</span><span class="sxs-lookup"><span data-stu-id="f6816-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="f6816-125">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6816-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="f6816-126">Kód spuštění modulu runtime nezjišťuje v registru.</span><span class="sxs-lookup"><span data-stu-id="f6816-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6816-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6816-127">Child Elements</span></span>  
 <span data-ttu-id="f6816-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6816-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6816-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6816-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f6816-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6816-130">Element</span></span>|<span data-ttu-id="f6816-131">Popis</span><span class="sxs-lookup"><span data-stu-id="f6816-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f6816-132">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6816-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="f6816-133">Obsahuje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f6816-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6816-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6816-134">Remarks</span></span>  
 <span data-ttu-id="f6816-135">Musíte použít aplikace založené na podporu pouze verze 1.0 modulu runtime `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f6816-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="f6816-136">Musíte použít aplikace vytvořené pomocí verze 1.1 nebo novější modulu runtime `<supportedRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f6816-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6816-137">Pokud použijete [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) funkce zadat konfigurační soubor, je nutné použít `<requiredRuntime>` element pro všechny verze modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f6816-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="f6816-138">`<supportedRuntime>` Element se ignoruje, pokud používáte [corbindtoruntimebycfg –](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span><span class="sxs-lookup"><span data-stu-id="f6816-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="f6816-139">`version` Řetězec atributu musí odpovídat názvu instalační složku pro určenou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6816-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="f6816-140">Tento řetězec nebyl interpretován.</span><span class="sxs-lookup"><span data-stu-id="f6816-140">This string is not interpreted.</span></span> <span data-ttu-id="f6816-141">Pokud kód pro spuštění modulu runtime nenajde odpovídající složku, není načítání modulu runtime; kód spuštění zobrazí chybovou zprávu a ukončí.</span><span class="sxs-lookup"><span data-stu-id="f6816-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6816-142">Kód spuštění pro aplikaci, která je hostitelem aplikace Microsoft Internet Explorer ignoruje `<requiredRuntime>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f6816-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6816-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6816-143">Example</span></span>  
 <span data-ttu-id="f6816-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f6816-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6816-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6816-145">See Also</span></span>  
 [<span data-ttu-id="f6816-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="f6816-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="f6816-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f6816-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f6816-148">\<PaveOver > Zadání kterou verzi modulu Runtime pro použití</span><span class="sxs-lookup"><span data-stu-id="f6816-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
