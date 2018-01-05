---
title: "x:Subclass – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d620b59208b9dc852abee3dd2e4d6c58b223d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xsubclass-directive"></a><span data-ttu-id="4f56a-102">x:Subclass – direktiva</span><span class="sxs-lookup"><span data-stu-id="4f56a-102">x:Subclass Directive</span></span>
<span data-ttu-id="4f56a-103">Mění chování kompilace kódu XAML při `x:Class` k dispozici je také.</span><span class="sxs-lookup"><span data-stu-id="4f56a-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="4f56a-104">Místo vytváření částečné třídu, která je založena na `x:Class`, poskytnutého `x:Class` je vytvořen jako zprostředkující třída, a pak se očekává založeny na vaše zadané odvozené třídy `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="4f56a-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="4f56a-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4f56a-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="4f56a-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="4f56a-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4f56a-107">Optional.</span></span> <span data-ttu-id="4f56a-108">Určuje CLR obor názvů, který obsahuje `classname`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="4f56a-109">Pokud `namespace` není zadaný, tečku (.) odděluje `namespace` a `classname`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="4f56a-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4f56a-110">Required.</span></span> <span data-ttu-id="4f56a-111">Určuje název CLR částečné třídy, který se připojuje načíst XAML a vaše kódu pro tento jazyk XAML.</span><span class="sxs-lookup"><span data-stu-id="4f56a-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="4f56a-112">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="4f56a-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="4f56a-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4f56a-113">Optional.</span></span> <span data-ttu-id="4f56a-114">Může lišit od `namespace` pokud každý obor názvů můžete vyřešit dalších.</span><span class="sxs-lookup"><span data-stu-id="4f56a-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="4f56a-115">Určuje CLR obor názvů, který obsahuje `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="4f56a-116">Pokud `subclassName` není zadaný, tečku (.) odděluje `subclassNamespace` a `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="4f56a-117">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4f56a-117">Required.</span></span> <span data-ttu-id="4f56a-118">Určuje název CLR podtřídy.</span><span class="sxs-lookup"><span data-stu-id="4f56a-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="4f56a-119">Závislosti</span><span class="sxs-lookup"><span data-stu-id="4f56a-119">Dependencies</span></span>  
 <span data-ttu-id="4f56a-120">[x: Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md) musí být poskytovány na stejný objekt, a tento objekt musí být kořenový element provozních XAML.</span><span class="sxs-lookup"><span data-stu-id="4f56a-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f56a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f56a-121">Remarks</span></span>  
 <span data-ttu-id="4f56a-122">`x:Subclass`využití je primárně určený pro jazyky, které nepodporují deklarace třídu.</span><span class="sxs-lookup"><span data-stu-id="4f56a-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="4f56a-123">Třída, která slouží jako `x:Subclass` nemůže být vnořené třídy a `x:Subclass` musí odkazovat na kořenový objekt, jak je popsáno v části "Závislosti".</span><span class="sxs-lookup"><span data-stu-id="4f56a-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="4f56a-124">V opačném koncepční význam `x:Subclass` není definována implementací rozhraní .NET Framework XAML Services.</span><span class="sxs-lookup"><span data-stu-id="4f56a-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="4f56a-125">Je to proto, že rozhraní .NET Framework XAML Services chování neurčuje celkové programovací model, ve které XAML značek a kódu zálohování připojeni.</span><span class="sxs-lookup"><span data-stu-id="4f56a-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="4f56a-126">Implementace další koncepty související s `x:Class` a `x:Subclass` provádí konkrétní architektury, kterých programovací modely nebo modely aplikace a definovat, jak připojit kód XAML, zkompilovaný kód a na základě CLR kódu.</span><span class="sxs-lookup"><span data-stu-id="4f56a-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="4f56a-127">Každý framework může mít svůj vlastní akce sestavení, které povolit některé chování nebo konkrétní součásti, které musí být součástí prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="4f56a-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="4f56a-128">V rámci rozhraní akce sestavení může také lišit v závislosti na konkrétní jazyk CLR, který se používá pro modelu code-behind.</span><span class="sxs-lookup"><span data-stu-id="4f56a-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="4f56a-129">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="4f56a-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="4f56a-130">`x:Subclass`může být v kořenovém adresáři stránku nebo na <xref:System.Windows.Application> kořenové v definici aplikace, která už má `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="4f56a-131">Deklarování `x:Subclass` u libovolného elementu jiného než kořenové stránky nebo aplikace, nebo ho zadáte, kde ne `x:Class` existuje, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="4f56a-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="4f56a-132">Vytváření odvozené třídy, které pracují správně pro `x:Subclass` scénář je poměrně složitá.</span><span class="sxs-lookup"><span data-stu-id="4f56a-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="4f56a-133">Možná bude muset prozkoumat zprostředkující soubory (soubory .g vyprodukované kompilace kódu, s názvy, které zahrnují názvy souborů XAML ve složce obj. projektu).</span><span class="sxs-lookup"><span data-stu-id="4f56a-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="4f56a-134">Tyto soubory zprostředkující vám pomohou určit původ určité programovací konstrukce v připojené k částečné třídy kompilované aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f56a-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="4f56a-135">Obslužné rutiny událostí v odvozené třídě musí být `internal override` (`Friend Overrides` v [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) Chcete-li přepsat zástupných procedur u obslužných rutin, jako vytvoří ve třídě zprostředkující během kompilace.</span><span class="sxs-lookup"><span data-stu-id="4f56a-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)]) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="4f56a-136">Jinak hodnota implementace odvozené třídy skrýt (stínové) implementaci zprostředkující třídy a nejsou volání zprostředkující třídu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="4f56a-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="4f56a-137">Když definujete obě `x:Class` a `x:Subclass`, není nutné k zajištění všech implementace pro třídu, která je odkazován objektem `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="4f56a-138">Potřebujete pojmenujte ho pomocí `x:Class` atributů tak, aby kompilátor má některé pokyny pro třídu, která vytváří v zprostředkující soubory (kompilátor není vyberte výchozí název v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="4f56a-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="4f56a-139">Můžete udělit `x:Class` třídy implementace; je to ale není Typický scénář použití obě `x:Class` a `x:Subclass`.</span><span class="sxs-lookup"><span data-stu-id="4f56a-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f56a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f56a-140">See Also</span></span>  
 [<span data-ttu-id="4f56a-141">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="4f56a-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="4f56a-142">XAML a vlastní třídy pro WPF</span><span class="sxs-lookup"><span data-stu-id="4f56a-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
