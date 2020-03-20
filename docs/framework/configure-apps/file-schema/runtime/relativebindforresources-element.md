---
title: Element <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153903"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="77d63-102">\<relativeBindForResources> Element</span><span class="sxs-lookup"><span data-stu-id="77d63-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="77d63-103">Optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="77d63-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="77d63-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="77d63-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="77d63-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="77d63-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span><span class="sxs-lookup"><span data-stu-id="77d63-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d63-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77d63-107">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77d63-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="77d63-108">Attributes and Elements</span></span>  
 <span data-ttu-id="77d63-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="77d63-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77d63-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="77d63-110">Attributes</span></span>  
  
|<span data-ttu-id="77d63-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="77d63-111">Attribute</span></span>|<span data-ttu-id="77d63-112">Popis</span><span class="sxs-lookup"><span data-stu-id="77d63-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="77d63-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="77d63-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="77d63-114">Určuje, zda běžný jazyk runtime optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="77d63-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="77d63-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="77d63-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="77d63-116">Value</span></span>|<span data-ttu-id="77d63-117">Popis</span><span class="sxs-lookup"><span data-stu-id="77d63-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="77d63-118">Doba běhu neoptimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="77d63-119">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="77d63-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="77d63-120">Za běhu optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77d63-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77d63-121">Child Elements</span></span>  
 <span data-ttu-id="77d63-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="77d63-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77d63-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="77d63-123">Parent Elements</span></span>  
  
|<span data-ttu-id="77d63-124">Element</span><span class="sxs-lookup"><span data-stu-id="77d63-124">Element</span></span>|<span data-ttu-id="77d63-125">Popis</span><span class="sxs-lookup"><span data-stu-id="77d63-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="77d63-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77d63-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="77d63-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="77d63-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77d63-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77d63-128">Remarks</span></span>  
 <span data-ttu-id="77d63-129">Správce prostředků obecně sonduje prostředky, jak je popsáno v tématu [Balení a nasazení prostředků.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)</span><span class="sxs-lookup"><span data-stu-id="77d63-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="77d63-130">To znamená, že když Resource Manager sonduje pro konkrétní lokalizovanou verzi prostředku, může se podívat do globální mezipaměti sestavení, podívat se do složky specifické pro jazykovou verzi v základu kódu aplikace, dotazovat se Instalační služby systému Windows pro satelitní sestavení a vyvolat <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="77d63-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="77d63-131">Prvek `<relativeBindForResources>` optimalizuje způsob, jakým Resource Manager sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="77d63-132">Může zlepšit výkon při zjišťování zdrojů za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="77d63-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="77d63-133">Při satelitní sestavení je nasazen ve stejném umístění jako sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="77d63-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="77d63-134">Jinými slovy, pokud je sestavení kódu nainstalováno v globální mezipaměti sestavení, musí být zde nainstalována také satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="77d63-135">Pokud je sestavení kódu nainstalováno v základu kódu aplikace, satelitní sestavení musí být také nainstalována ve složce specifické pro jazykovou verzi v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="77d63-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="77d63-136">Pokud instalační služba systému Windows není použita nebo se používá pouze zřídka pro instalaci satelitních sestavení na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="77d63-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="77d63-137">Pokud kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="77d63-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="77d63-138">Nastavení `enabled` atributu `<relativeBindForResources>` prvku `true` pro optimalizaci sondy Správce prostředků pro satelitní sestavení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="77d63-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="77d63-139">Používá umístění sestavení nadřazeného kódu ke sondování pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="77d63-140">Nedotazuje se Instalační služba systému Windows na satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="77d63-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="77d63-141">To nevyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="77d63-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d63-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="77d63-142">See also</span></span>

- [<span data-ttu-id="77d63-143">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="77d63-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="77d63-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="77d63-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="77d63-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="77d63-145">Configuration File Schema</span></span>](../index.md)
