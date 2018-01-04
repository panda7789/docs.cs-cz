---
title: "&lt;relativebindforresources –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8409b1fe86776397ceb3db5b338fb8aaadef9cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltrelativebindforresourcesgt-element"></a><span data-ttu-id="0714a-102">&lt;relativebindforresources –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="0714a-102">&lt;relativeBindForResources&gt; Element</span></span>
<span data-ttu-id="0714a-103">Tato kontrola se optimalizuje pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="0714a-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="0714a-104">\<configuration> Element</span></span>  
<span data-ttu-id="0714a-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="0714a-105">\<runtime> Element</span></span>  
<span data-ttu-id="0714a-106">\<relativebindforresources – > elementu</span><span class="sxs-lookup"><span data-stu-id="0714a-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0714a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0714a-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0714a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0714a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0714a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0714a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0714a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0714a-110">Attributes</span></span>  
  
|<span data-ttu-id="0714a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0714a-111">Attribute</span></span>|<span data-ttu-id="0714a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0714a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0714a-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0714a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0714a-114">Určuje, zda modul common language runtime optimalizuje sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0714a-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0714a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0714a-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0714a-116">Value</span></span>|<span data-ttu-id="0714a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0714a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0714a-118">Modul runtime není optimální sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="0714a-119">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0714a-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="0714a-120">Modul runtime optimalizuje sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0714a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0714a-121">Child Elements</span></span>  
 <span data-ttu-id="0714a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0714a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0714a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0714a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0714a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0714a-124">Element</span></span>|<span data-ttu-id="0714a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0714a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0714a-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0714a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0714a-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0714a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0714a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0714a-128">Remarks</span></span>  
 <span data-ttu-id="0714a-129">Obecně platí, Resource Manager sondy pro prostředky, jak je uvedeno v [balení a nasazení prostředků](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="0714a-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="0714a-130">To znamená, že když Resource Manager sondy pro konkrétní lokalizované verze prostředku, může hledat v globální mezipaměti sestavení, ve složce specifické pro jazykovou verzi v základní, dotazu kód aplikace Instalační služby systému Windows vyhledejte satelitní sestavení a zvýšit <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="0714a-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="0714a-131">`<relativeBindForResources>` Element optimalizuje způsob, ve kterém se správce prostředků sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="0714a-132">Se může zlepšit výkon při zjišťování prostředků za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="0714a-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="0714a-133">Satelitní sestavení je při nasazení ve stejném umístění jako sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="0714a-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="0714a-134">Jinými slovy Pokud kód sestavení je nainstalována v globální mezipaměti sestavení, satelitní sestavení musí být nainstalována také existuje.</span><span class="sxs-lookup"><span data-stu-id="0714a-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="0714a-135">Pokud je kód sestavení nainstalováno v kódu aplikace základní, satelitní sestavení musí být také nainstalovaný ve složce specifické pro jazykovou verzi v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="0714a-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="0714a-136">Když instalační služba systému Windows nepoužívá nebo jen zřídka se používá pro instalaci na vyžádání satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="0714a-137">Pokud kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="0714a-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="0714a-138">Nastavení `enabled` atribut `<relativeBindForResources>` element `true` optimalizuje Resource Manager testu pro satelitní sestavení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0714a-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="0714a-139">Umístění nadřazeného kódu sestavení na základě testu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="0714a-140">Neprohledává Instalační služby systému Windows pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="0714a-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="0714a-141">Nelze vyvolat <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.</span><span class="sxs-lookup"><span data-stu-id="0714a-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0714a-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="0714a-142">See Also</span></span>  
 [<span data-ttu-id="0714a-143">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="0714a-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [<span data-ttu-id="0714a-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0714a-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="0714a-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0714a-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
