---
title: "x:Shared – atribut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: "16"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d6a9333b2267e82fc25b2a0ec4bf5dd14f644078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xshared-attribute"></a><span data-ttu-id="b3e96-102">x:Shared – atribut</span><span class="sxs-lookup"><span data-stu-id="b3e96-102">x:Shared Attribute</span></span>
<span data-ttu-id="b3e96-103">Pokud nastavíte hodnotu `false`, mění chování WPF načtení prostředků tak, aby požadavky pro prostředek s atributy vytvoření nové instance pro každý požadavek místo sdílení stejné instanci pro všechny požadavky.</span><span class="sxs-lookup"><span data-stu-id="b3e96-103">When set to `false`, modifies WPF resource-retrieval behavior so that requests for the attributed resource create a new instance for each request instead of sharing the same instance for all requests.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="b3e96-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="b3e96-104">XAML Attribute Usage</span></span>  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3e96-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3e96-105">Remarks</span></span>  
 <span data-ttu-id="b3e96-106">`x:Shared`je namapovaná na oboru názvů jazyka XAML jazyka XAML a je rozpoznat jako platný element jazyka XAML rozhraní .NET Framework XAML Services a jeho čtečky XAML.</span><span class="sxs-lookup"><span data-stu-id="b3e96-106">`x:Shared` is mapped to the XAML language XAML namespace and is recognized as a valid XAML language element by .NET Framework XAML Services and its XAML readers.</span></span> <span data-ttu-id="b3e96-107">Ale stanovené možnosti `x:Shared` jsou pouze relevantní pro aplikace WPF a pro analyzátor WPF XAML.</span><span class="sxs-lookup"><span data-stu-id="b3e96-107">However, the stated capabilities of `x:Shared` are only relevant for WPF applications and for the WPF XAML parser.</span></span> <span data-ttu-id="b3e96-108">V grafickém subsystému WPF `x:Shared` je užitečné jako atribut pouze při použití objektu, která existuje v rámci WPF <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="b3e96-108">In WPF, `x:Shared` is only useful as an attribute when it is applied to an object that exists within a WPF <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="b3e96-109">Další použití nevyvolá výjimku, analýzy výjimky nebo jiné chyby, ale nemají žádný účinek.</span><span class="sxs-lookup"><span data-stu-id="b3e96-109">Other usages do not throw parse exceptions or other errors, but they have no effect.</span></span>  
  
 <span data-ttu-id="b3e96-110">Význam `x:Shared` není zadané v specifikace jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="b3e96-110">The meaning of `x:Shared` is not specified in the XAML language specification.</span></span> <span data-ttu-id="b3e96-111">Jiných implementacích XAML, jako jsou ty, které sestavení v rozhraní .NET Framework XAML Services neposkytují nutně sdílení prostředků podpory.</span><span class="sxs-lookup"><span data-stu-id="b3e96-111">Other XAML implementations, such as those that build on .NET Framework XAML Services, do not necessarily provide resource-sharing support.</span></span> <span data-ttu-id="b3e96-112">Implementace takových XAML poskytovat podobné chování v podpůrné framework, který používá `x:Shared` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b3e96-112">Such XAML implementations could provide similar behavior in the supporting framework that also used `x:Shared` values.</span></span>  
  
 <span data-ttu-id="b3e96-113">V grafickém subsystému WPF, výchozí `x:Shared` podmínka pro prostředky je `true`.</span><span class="sxs-lookup"><span data-stu-id="b3e96-113">In WPF, the default `x:Shared` condition for resources is `true`.</span></span> <span data-ttu-id="b3e96-114">Tento stav znamená, že každá žádost daného prostředku vždy vrátí stejné instanci.</span><span class="sxs-lookup"><span data-stu-id="b3e96-114">This condition means that any given resource request always returns the same instance.</span></span>  
  
 <span data-ttu-id="b3e96-115">Objekt, který je vrácen prostřednictvím API, prostředků, jako úprava <xref:System.Windows.FrameworkElement.FindResource%2A>, nebo úprava objektu přímo v rámci <xref:System.Windows.ResourceDictionary>, změní původní prostředků.</span><span class="sxs-lookup"><span data-stu-id="b3e96-115">Modifying an object that is returned through a resource API, such as <xref:System.Windows.FrameworkElement.FindResource%2A>, or modifying an object directly within a <xref:System.Windows.ResourceDictionary>, changes the original resource.</span></span> <span data-ttu-id="b3e96-116">Dynamické prostředků odkazy kdyby odkazy na tento prostředek uživatelé prostředku získat změněné prostředků.</span><span class="sxs-lookup"><span data-stu-id="b3e96-116">If references to that resource were dynamic resource references, the consumers of that resource get the changed resource.</span></span>  
  
 <span data-ttu-id="b3e96-117">Změní-li odkazy na prostředek měla odkazy statické prostředků, k prostředku po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] doba zpracování jsou důležité.</span><span class="sxs-lookup"><span data-stu-id="b3e96-117">If references to the resource were static resource references, changes to the resource after [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] processing time are irrelevant.</span></span> <span data-ttu-id="b3e96-118">Další informace o statických a dynamických prostředků odkazy najdete v tématu [XAML prostředky](../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="b3e96-118">For more information about static versus dynamic resource references, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="b3e96-119">Explicitní určení `x:Shared="true"` nevyužívá, protože již výchozí.</span><span class="sxs-lookup"><span data-stu-id="b3e96-119">Explicitly specifying `x:Shared="true"` is rarely done, because that is already the default.</span></span> <span data-ttu-id="b3e96-120">Neexistuje žádné přímé kód ekvivalentní `x:Shared` v WPF objektu modelu, lze zadat pouze využití XAML a musí být zpracován jako výchozí chování WPF nebo v zprostředkující datový proud uzlu XAML v cestě zatížení Pokud zpracované pomocí rozhraní .NET Framework XAML Se rvices a jeho čtečky XAML.</span><span class="sxs-lookup"><span data-stu-id="b3e96-120">There is no direct code equivalent for `x:Shared` in the WPF object model; it can only be specified in a XAML usage and must be processed either by the default WPF behavior or in an intermediate XAML node stream on the load path if processed using .NET Framework XAML Services and its XAML readers.</span></span>  
  
 <span data-ttu-id="b3e96-121">Scénář pro `x:Shared="false"` je, pokud definujete <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy jako prostředek a potom zavedení element prostředků do modelu obsahu.</span><span class="sxs-lookup"><span data-stu-id="b3e96-121">A scenario for `x:Shared="false"` is if you define a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class as a resource and then you introduce the element resource into a content model.</span></span> <span data-ttu-id="b3e96-122">`x:Shared="false"`Umožňuje prostředek element potřeba zavést vícekrát ve stejné kolekci (například <xref:System.Windows.Controls.UIElementCollection>).</span><span class="sxs-lookup"><span data-stu-id="b3e96-122">`x:Shared="false"` enables an element resource to be introduced multiple times in the same collection (such as a <xref:System.Windows.Controls.UIElementCollection>).</span></span> <span data-ttu-id="b3e96-123">Bez `x:Shared="false"` to je neplatný, protože kolekce vyžaduje jedinečnost její obsah.</span><span class="sxs-lookup"><span data-stu-id="b3e96-123">Without `x:Shared="false"` this is invalid because the collection enforces uniqueness of its contents.</span></span> <span data-ttu-id="b3e96-124">Ale `x:Shared="false"` chování vytvoří jiná instance stejné prostředku místo vrací stejnou instanci.</span><span class="sxs-lookup"><span data-stu-id="b3e96-124">However, the `x:Shared="false"` behavior creates another identical instance of the resource instead of returning the same instance.</span></span>  
  
 <span data-ttu-id="b3e96-125">Jiné scénáře `x:Shared="false"` je, pokud použijete <xref:System.Windows.Freezable> prostředku pro animace hodnoty, ale chcete upravit prostředek na základě za animace.</span><span class="sxs-lookup"><span data-stu-id="b3e96-125">Another scenario for `x:Shared="false"` is if you use a <xref:System.Windows.Freezable> resource for animation values but want to modify the resource on a per animation basis.</span></span>  
  
 <span data-ttu-id="b3e96-126">Řetězec ošetření `false` není velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="b3e96-126">The string handling of `false` is not case sensitive.</span></span>  
  
 <span data-ttu-id="b3e96-127">V grafickém subsystému WPF `x:Shared` je platný pouze za následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="b3e96-127">In WPF, `x:Shared` is only valid under the following conditions:</span></span>  
  
-   <span data-ttu-id="b3e96-128"><xref:System.Windows.ResourceDictionary> Obsahující položky s `x:Shared` musí být zkompilovány.</span><span class="sxs-lookup"><span data-stu-id="b3e96-128">The <xref:System.Windows.ResourceDictionary> that contains the items with `x:Shared` must be compiled.</span></span> <span data-ttu-id="b3e96-129"><xref:System.Windows.ResourceDictionary> Nemůže být v rámci přijít XAML nebo použít pro motivy.</span><span class="sxs-lookup"><span data-stu-id="b3e96-129">The <xref:System.Windows.ResourceDictionary> cannot be within loose XAML or used for themes.</span></span>  
  
-   <span data-ttu-id="b3e96-130"><xref:System.Windows.ResourceDictionary> Obsahuje položky nesmí být vnořený v rámci jiného <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="b3e96-130">The <xref:System.Windows.ResourceDictionary> that contains the items must not be nested within another <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="b3e96-131">Například nemůžete použít `x:Shared` pro položky v <xref:System.Windows.ResourceDictionary> se v rámci <xref:System.Windows.Style> který je už <xref:System.Windows.ResourceDictionary> položky.</span><span class="sxs-lookup"><span data-stu-id="b3e96-131">For example, you cannot use `x:Shared` for items in a <xref:System.Windows.ResourceDictionary> that is within a <xref:System.Windows.Style> that is already a <xref:System.Windows.ResourceDictionary> item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e96-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3e96-132">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="b3e96-133">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="b3e96-133">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="b3e96-134">Základní prvky</span><span class="sxs-lookup"><span data-stu-id="b3e96-134">Base Elements</span></span>](../../../docs/framework/wpf/advanced/base-elements.md)
