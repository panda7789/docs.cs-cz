---
title: Element <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: 6a418fc546313b74bb965a0b223eca9c2e5acc08
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115789"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="01064-102">\<element > relativeBindForResources</span><span class="sxs-lookup"><span data-stu-id="01064-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="01064-103">Optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-103">Optimizes the probe for satellite assemblies.</span></span>  
  
<span data-ttu-id="01064-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="01064-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="01064-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="01064-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="01064-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<relativeBindForResources >**</span><span class="sxs-lookup"><span data-stu-id="01064-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01064-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01064-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01064-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="01064-108">Attributes and Elements</span></span>  
 <span data-ttu-id="01064-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="01064-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01064-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="01064-110">Attributes</span></span>  
  
|<span data-ttu-id="01064-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="01064-111">Attribute</span></span>|<span data-ttu-id="01064-112">Popis</span><span class="sxs-lookup"><span data-stu-id="01064-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="01064-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="01064-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="01064-114">Určuje, zda modul CLR (Common Language Runtime) optimalizuje test pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="01064-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="01064-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="01064-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="01064-116">Value</span></span>|<span data-ttu-id="01064-117">Popis</span><span class="sxs-lookup"><span data-stu-id="01064-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="01064-118">Modul runtime neoptimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="01064-119">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01064-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="01064-120">Modul runtime optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01064-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="01064-121">Child Elements</span></span>  
 <span data-ttu-id="01064-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="01064-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01064-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01064-123">Parent Elements</span></span>  
  
|<span data-ttu-id="01064-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="01064-124">Element</span></span>|<span data-ttu-id="01064-125">Popis</span><span class="sxs-lookup"><span data-stu-id="01064-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="01064-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="01064-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="01064-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="01064-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01064-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01064-128">Remarks</span></span>  
 <span data-ttu-id="01064-129">Obecně Správce prostředků sondy pro prostředky, jak je popsáno v tématu [balení a nasazení prostředků](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="01064-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="01064-130">To znamená, že když Správce prostředků sondy pro určitou lokalizovanou verzi prostředku, může to vypadat v globální mezipaměti sestavení (GAC), vyhledat složku specifickou pro jazykovou verzi v základu kódu aplikace, dotazovat Instalační služba systému Windows pro satelitní sestavení a vyvolat událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01064-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="01064-131">Prvek `<relativeBindForResources>` optimalizuje způsob, jakým Správce prostředků sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="01064-132">Může zvýšit výkon při zjišťování prostředků za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="01064-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="01064-133">Když satelitní sestavení je nasazeno ve stejném umístění jako sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="01064-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="01064-134">Jinými slovy, pokud je sestavení kódu nainstalováno v globální mezipaměti sestavení (GAC), musí být také nainstalovaná satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="01064-135">Pokud je sestavení kódu nainstalováno v základu kódu aplikace, musí být satelitní sestavení také nainstalována do složky specifické pro jazykovou verzi v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="01064-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="01064-136">Pokud se Instalační služba systému Windows nepoužívá nebo se používá jenom zřídka pro instalaci satelitních sestavení na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="01064-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="01064-137">Když kód aplikace nezpracovává událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01064-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="01064-138">Nastavením atributu `enabled` elementu `<relativeBindForResources>` na `true` optimalizuje Správce prostředků sondy pro satelitní sestavení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="01064-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="01064-139">Používá umístění sestavení nadřazeného kódu pro testování satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="01064-140">Nedotazuje se Instalační služba systému Windows pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="01064-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="01064-141">Nevyvolává událost <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01064-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01064-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01064-142">See also</span></span>

- [<span data-ttu-id="01064-143">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="01064-143">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="01064-144">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="01064-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="01064-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="01064-145">Configuration File Schema</span></span>](../index.md)
