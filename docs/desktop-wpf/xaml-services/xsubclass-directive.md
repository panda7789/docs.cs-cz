---
title: x:Subclass – direktiva
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071365"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="5964b-102">x:Subclass – direktiva</span><span class="sxs-lookup"><span data-stu-id="5964b-102">x:Subclass Directive</span></span>

<span data-ttu-id="5964b-103">Upravuje chování kompilace značek XAML, pokud `x:Class` je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5964b-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="5964b-104">Namísto vytváření částečné třídy, `x:Class`která je `x:Class` založena na , zadaný je vytvořen jako zprostředkující třídy a pak za předpokladu, odvozené třídy se očekává, že bude založena na `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="5964b-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="5964b-105">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="5964b-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="5964b-106">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="5964b-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="5964b-107">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5964b-107">Optional.</span></span> <span data-ttu-id="5964b-108">Určuje obor názvů CLR, `classname`který obsahuje .</span><span class="sxs-lookup"><span data-stu-id="5964b-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="5964b-109">Pokud `namespace` je zadán, tečka (.) odděluje `namespace` a `classname`.</span><span class="sxs-lookup"><span data-stu-id="5964b-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="5964b-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5964b-110">Required.</span></span> <span data-ttu-id="5964b-111">Určuje název CLR částečné třídy, která spojuje načtený XAML a váš kód na pozadí pro tento XAML.</span><span class="sxs-lookup"><span data-stu-id="5964b-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="5964b-112">Viz Poznámky.</span><span class="sxs-lookup"><span data-stu-id="5964b-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="5964b-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5964b-113">Optional.</span></span> <span data-ttu-id="5964b-114">Může se `namespace` lišit od toho, pokud každý obor názvů může přeložit druhý.</span><span class="sxs-lookup"><span data-stu-id="5964b-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="5964b-115">Určuje obor názvů CLR, `subclassName`který obsahuje .</span><span class="sxs-lookup"><span data-stu-id="5964b-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="5964b-116">Pokud `subclassName` je zadán, tečka (.) odděluje `subclassNamespace` a `subclassName`.</span><span class="sxs-lookup"><span data-stu-id="5964b-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="5964b-117">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5964b-117">Required.</span></span> <span data-ttu-id="5964b-118">Určuje název CLR podtřídy.</span><span class="sxs-lookup"><span data-stu-id="5964b-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="5964b-119">Závislosti</span><span class="sxs-lookup"><span data-stu-id="5964b-119">Dependencies</span></span>

<span data-ttu-id="5964b-120">[x:Class Directive](xclass-directive.md) musí být také k dispozici na stejném objektu a tento objekt musí být kořenovým prvkem výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="5964b-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="5964b-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5964b-121">Remarks</span></span>

<span data-ttu-id="5964b-122">`x:Subclass`použití je primárně určeno pro jazyky, které nepodporují deklarace dílčí třídy.</span><span class="sxs-lookup"><span data-stu-id="5964b-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="5964b-123">Třída použitá `x:Subclass` jako vnořená třída `x:Subclass` nemůže být vnořenou a musí odkazovat na kořenový objekt, jak je vysvětleno v části "Závislosti".</span><span class="sxs-lookup"><span data-stu-id="5964b-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="5964b-124">V opačném případě `x:Subclass` koncepční význam je nedefinována implementací služby .NET XAML Services.</span><span class="sxs-lookup"><span data-stu-id="5964b-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="5964b-125">Důvodem je, že chování služby .NET XAML Services neurčuje celkový programovací model, podle kterého jsou připojeny značky XAML a kód zálohování.</span><span class="sxs-lookup"><span data-stu-id="5964b-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="5964b-126">Implementace dalších konceptů `x:Class` souvisejících s a `x:Subclass` jsou prováděny konkrétní mise, které používají programovací modely nebo aplikační modely k definování, jak připojit značky XAML, zkompilované značky a kód založený na CLR.</span><span class="sxs-lookup"><span data-stu-id="5964b-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="5964b-127">Každý rámec může mít vlastní akce sestavení, které umožňují některé chování nebo konkrétní součásti, které musí být zahrnuty v prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="5964b-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="5964b-128">V rámci akce sestavení se také může lišit v závislosti na konkrétní jazyk CLR, který se používá pro kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="5964b-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="5964b-129">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="5964b-129">WPF Usage Notes</span></span>

<span data-ttu-id="5964b-130">`x:Subclass`může být na kořenové <xref:System.Windows.Application> stránce nebo na kořenovém `x:Class`adresáři v definici aplikace, která již má .</span><span class="sxs-lookup"><span data-stu-id="5964b-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="5964b-131">Deklarování `x:Subclass` na libovolný prvek než kořen stránky nebo `x:Class` aplikace nebo určení, kde neexistuje, způsobí chybu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="5964b-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="5964b-132">Vytvoření odvozené třídy, `x:Subclass` které pracují správně pro scénář je poměrně složité.</span><span class="sxs-lookup"><span data-stu-id="5964b-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="5964b-133">Možná budete muset prozkoumat zprostředkující soubory (soubory G vytvořené ve složce obj projektu podle kompilace značek s názvy, které obsahují názvy souborů XAML).</span><span class="sxs-lookup"><span data-stu-id="5964b-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="5964b-134">Tyto zprostředkující soubory vám mohou pomoci určit původ určitých programovacích konstrukcí ve spojených částečných třídách v kompilované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5964b-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="5964b-135">Obslužné rutiny událostí `internal override` `Friend Overrides` v odvozené třídě musí být (v jazyce Microsoft Visual Basic) k přepsání zástupných procedur pro obslužné rutiny, jak byly vytvořeny v zprostředkující třídě během kompilace.</span><span class="sxs-lookup"><span data-stu-id="5964b-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="5964b-136">V opačném případě odvozené implementace třídy skrýt (stín) implementace zprostředkující třídy a zprostředkující třídy obslužné rutiny nejsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="5964b-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="5964b-137">Při definování `x:Class` obou `x:Subclass`a , není nutné zadat žádnou implementaci pro `x:Class`třídu, na kterou odkazuje .</span><span class="sxs-lookup"><span data-stu-id="5964b-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="5964b-138">Stačí dát název prostřednictvím atributu `x:Class` tak, aby kompilátor má některé pokyny pro třídu, kterou vytvoří v zprostředkující soubory (kompilátor nevybere výchozí název v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="5964b-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="5964b-139">Můžete dát `x:Class` třídy implementace; však toto není typický scénář `x:Class` `x:Subclass`pro použití obou a .</span><span class="sxs-lookup"><span data-stu-id="5964b-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5964b-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="5964b-140">See also</span></span>

- [<span data-ttu-id="5964b-141">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="5964b-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="5964b-142">XAML a vlastní třídy pro WPF</span><span class="sxs-lookup"><span data-stu-id="5964b-142">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
