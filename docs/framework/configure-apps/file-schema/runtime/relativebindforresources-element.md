---
title: Element <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153903"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="4894c-102">Element \<relativeBindForResources></span><span class="sxs-lookup"><span data-stu-id="4894c-102">\<relativeBindForResources> Element</span></span>
<span data-ttu-id="4894c-103">Optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-103">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="4894c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4894c-104">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4894c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4894c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4894c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4894c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4894c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="4894c-107">Attributes</span></span>  
  
|<span data-ttu-id="4894c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="4894c-108">Attribute</span></span>|<span data-ttu-id="4894c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4894c-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4894c-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="4894c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="4894c-111">Určuje, zda modul CLR (Common Language Runtime) optimalizuje test pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-111">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="4894c-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="4894c-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="4894c-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4894c-113">Value</span></span>|<span data-ttu-id="4894c-114">Description</span><span class="sxs-lookup"><span data-stu-id="4894c-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="4894c-115">Modul runtime neoptimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-115">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="4894c-116">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="4894c-116">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="4894c-117">Modul runtime optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-117">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4894c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4894c-118">Child Elements</span></span>  
 <span data-ttu-id="4894c-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="4894c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4894c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4894c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4894c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4894c-121">Element</span></span>|<span data-ttu-id="4894c-122">Description</span><span class="sxs-lookup"><span data-stu-id="4894c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4894c-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4894c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4894c-124">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4894c-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4894c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4894c-125">Remarks</span></span>  
 <span data-ttu-id="4894c-126">Obecně Správce prostředků sondy pro prostředky, jak je popsáno v tématu [balení a nasazení prostředků](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="4894c-126">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="4894c-127">To znamená, že když Správce prostředků sondy pro určitou lokalizovanou verzi prostředku, může to vypadat v globální mezipaměti sestavení (GAC), vyhledat složku specifickou pro jazykovou verzi v základu kódu aplikace, dotazovat Instalační služba systému Windows pro satelitní sestavení a vyvolat <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.</span><span class="sxs-lookup"><span data-stu-id="4894c-127">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="4894c-128">`<relativeBindForResources>`Prvek optimalizuje způsob, jakým Správce prostředků sondy pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-128">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="4894c-129">Může zvýšit výkon při zjišťování prostředků za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="4894c-129">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="4894c-130">Když satelitní sestavení je nasazeno ve stejném umístění jako sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="4894c-130">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="4894c-131">Jinými slovy, pokud je sestavení kódu nainstalováno v globální mezipaměti sestavení (GAC), musí být také nainstalovaná satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-131">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="4894c-132">Pokud je sestavení kódu nainstalováno v základu kódu aplikace, musí být satelitní sestavení také nainstalována do složky specifické pro jazykovou verzi v základu kódu.</span><span class="sxs-lookup"><span data-stu-id="4894c-132">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="4894c-133">Pokud se Instalační služba systému Windows nepoužívá nebo se používá jenom zřídka pro instalaci satelitních sestavení na vyžádání.</span><span class="sxs-lookup"><span data-stu-id="4894c-133">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="4894c-134">Když kód aplikace událost nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4894c-134">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="4894c-135">Nastavení `enabled` atributu `<relativeBindForResources>` elementu pro `true` optimalizaci správce prostředků sondy pro satelitní sestavení následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4894c-135">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="4894c-136">Používá umístění sestavení nadřazeného kódu pro testování satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-136">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="4894c-137">Nedotazuje se Instalační služba systému Windows pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="4894c-137">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="4894c-138">Událost nevyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4894c-138">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4894c-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="4894c-139">See also</span></span>

- [<span data-ttu-id="4894c-140">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="4894c-140">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="4894c-141">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="4894c-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4894c-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="4894c-142">Configuration File Schema</span></span>](../index.md)
