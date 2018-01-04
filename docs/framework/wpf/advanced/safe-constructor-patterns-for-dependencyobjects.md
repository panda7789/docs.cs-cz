---
title: "Zabezpečené vzory konstruktoru pro DependencyObjects"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: db1b7f47ef135b1a174eecef7e53b41e6996256d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="95dd3-102">Zabezpečené vzory konstruktoru pro DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="95dd3-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="95dd3-103">Konstruktory – třída obecně platí, by neměl volání zpětná volání, jako je například virtuální metody nebo delegáti, protože konstruktory lze volat jako základní inicializace konstruktory odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="95dd3-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="95dd3-104">Zadání virtuální může být provedena do stavu neúplná inicializace libovolného objektu.</span><span class="sxs-lookup"><span data-stu-id="95dd3-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="95dd3-105">Ale samotného systému vlastnost volá a zveřejňuje zpětná volání interně v rámci systému vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="95dd3-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="95dd3-106">Jednoduché operace jako nastavení hodnoty vlastnosti závislosti s <xref:System.Windows.DependencyObject.SetValue%2A> volání potenciálně zahrnuje zpětné volání někde pro zjišťování.</span><span class="sxs-lookup"><span data-stu-id="95dd3-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="95dd3-107">Z tohoto důvodu byste měli být opatrní při nastavení hodnoty vlastností v textu konstruktor, který se může stát problematické, pokud váš typ se používá jako základní třída závislostí.</span><span class="sxs-lookup"><span data-stu-id="95dd3-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="95dd3-108">Je určitý vzor pro implementaci <xref:System.Windows.DependencyObject> konstruktory, které zabraňuje konkrétních problémů s stavy vlastnost závislosti a vyplývajících zpětná volání, které jsou zde uvedeny.</span><span class="sxs-lookup"><span data-stu-id="95dd3-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="95dd3-109">Vlastnost systému virtuální metody</span><span class="sxs-lookup"><span data-stu-id="95dd3-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="95dd3-110">Následující virtuální metody nebo zpětná volání jsou potenciálně volá se během výpočty z <xref:System.Windows.DependencyObject.SetValue%2A> volání, které nastavuje hodnotu vlastnosti závislosti: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="95dd3-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="95dd3-111">Každý z těchto virtuální metody nebo zpětná volání slouží určitý účel v rozšíření všestrannost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systém a závislosti vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95dd3-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="95dd3-112">Další informace o tom, jak použít tyto virtuals k přizpůsobení rozhodnutí hodnotu vlastnosti, najdete v části [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="95dd3-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="95dd3-113">Vynucení pravidla FXCop vs. Vlastnost systému Virtuals</span><span class="sxs-lookup"><span data-stu-id="95dd3-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="95dd3-114">Pokud použijete nástroj Microsoft FXCop jako součást procesu sestavení a buď odvozujete od určité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání konstruktoru základní třídy rozhraní framework nebo implementovat vlastní vlastností závislostí v odvozených třídách, může dojít k konkrétní Porušení pravidel FXCop.</span><span class="sxs-lookup"><span data-stu-id="95dd3-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="95dd3-115">Název řetězce pro tento porušení je:</span><span class="sxs-lookup"><span data-stu-id="95dd3-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="95dd3-116">Toto je pravidlo, které je součástí výchozí sada pro FXCop veřejné pravidel.</span><span class="sxs-lookup"><span data-stu-id="95dd3-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="95dd3-117">Co toto pravidlo může být vytváření sestav je trasování prostřednictvím systému vlastnost závislostí, který nakonec volá metodu virtuálního systému vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="95dd3-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="95dd3-118">Toto pravidlo porušení může nadále zobrazovat i po následující doporučené konstruktor vzory popsané v tomto tématu se proto může být třeba zakázat nebo potlačit v konfiguraci sady pravidel FXCop daného pravidla.</span><span class="sxs-lookup"><span data-stu-id="95dd3-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="95dd3-119">Většiny problémů pocházet z odvozující třídy, ne pomocí existujících tříd</span><span class="sxs-lookup"><span data-stu-id="95dd3-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="95dd3-120">Problémy hlášené tímto pravidlem nastane, když je třída, která můžete implementovat s virtuální metody v jeho pořadí vytváření pak odvozený od.</span><span class="sxs-lookup"><span data-stu-id="95dd3-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="95dd3-121">Pokud zapečetit vaší třídy, nebo jinak vědět nebo vynutit, aby třídě nebude být odvozen od, jaké jsou požadavky popsané tady a problémy, které opodstatněny pravidlo FXCop se nevztahují na vás.</span><span class="sxs-lookup"><span data-stu-id="95dd3-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="95dd3-122">Ale pokud autorizujete třídy tak, že jsou určeny k použití jako základní třídy pro instanci Pokud vytváříte šablony, nebo rozšíření řízení knihovny, postupujte podle zde doporučené pro konstruktory vzory.</span><span class="sxs-lookup"><span data-stu-id="95dd3-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="95dd3-123">Výchozí konstruktory musí inicializovat všechny hodnoty požadoval zpětných volání</span><span class="sxs-lookup"><span data-stu-id="95dd3-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="95dd3-124">U členů instancí, které jsou používány třída přepsání nebo zpětných volání (zpětná volání v seznamu v části Vlastnosti systému Virtuals) se musí inicializovat ve vaší třídy výchozí konstruktor, i v případě, že některé z těchto hodnot jsou vyplněny "Skutečná" hodnoty prostřednictvím Parametry jiný než výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="95dd3-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="95dd3-125">Následující příklad kódu (a další příklady) se svého – příklad jazyka C#, která porušuje toto pravidlo a vysvětluje problému:</span><span class="sxs-lookup"><span data-stu-id="95dd3-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 <span data-ttu-id="95dd3-126">Pokud kód aplikace volá `new MyClass(objectvalue)`, volá výchozí konstruktor a základní třídy konstruktory.</span><span class="sxs-lookup"><span data-stu-id="95dd3-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="95dd3-127">Potom nastaví `Property1 = object1`, která volá metodu virtuální `OnPropertyChanged` na vlastnící `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="95dd3-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="95dd3-128">Přepsání odkazuje na `_myList`, která ještě nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="95dd3-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="95dd3-129">Jedním ze způsobů, abyste se těmto problémům je zajistit, že zpětná volání používat pouze ostatní vlastnosti závislosti, a že každý tato vlastnost závislosti zavedených výchozí hodnota v rámci jeho registrované metadata.</span><span class="sxs-lookup"><span data-stu-id="95dd3-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="95dd3-130">Vzory bezpečné konstruktor</span><span class="sxs-lookup"><span data-stu-id="95dd3-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="95dd3-131">Chcete-li zamezit rizikům neúplná inicializace, pokud vaše třída se používá jako základní třída, postupujte podle tyto vzory:</span><span class="sxs-lookup"><span data-stu-id="95dd3-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="95dd3-132">Výchozí konstruktory volání základní inicializace</span><span class="sxs-lookup"><span data-stu-id="95dd3-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="95dd3-133">Implementujte tyto konstruktory volání základní výchozí nastavení:</span><span class="sxs-lookup"><span data-stu-id="95dd3-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="95dd3-134">Konstruktory (pohodlí) jiné než výchozí, neodpovídá žádné základní podpisy</span><span class="sxs-lookup"><span data-stu-id="95dd3-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="95dd3-135">Pokud tyto konstruktory používat parametry pro nastavení vlastností závislostí při inicializaci, první volání vlastní třída výchozí konstruktor pro inicializaci a pak pomocí parametrů pro nastavení vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="95dd3-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="95dd3-136">To může buď být definované třídu vlastností závislostí nebo vlastností závislostí dědí z třídy base, ale v obou případech používají následující vzorec:</span><span class="sxs-lookup"><span data-stu-id="95dd3-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="95dd3-137">Konstruktory, jiné než výchozí (pohodlí), které neodpovídají základní podpisy</span><span class="sxs-lookup"><span data-stu-id="95dd3-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="95dd3-138">Namísto volání základní konstruktor s stejné Parametrizace, opakujte volání vlastní třídu výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="95dd3-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="95dd3-139">Nevolejte základní inicializátoru; Místo toho by měly volat `this()`.</span><span class="sxs-lookup"><span data-stu-id="95dd3-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="95dd3-140">Pak opakovat původní chování konstruktor pomocí předaných parametrů jako hodnoty pro nastavení relevantní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95dd3-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="95dd3-141">Použití v původní dokumentaci konstruktor základní pokyny k určení vlastností, které konkrétní parametry jsou určená k nastavení:</span><span class="sxs-lookup"><span data-stu-id="95dd3-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="95dd3-142">Musí odpovídat všechny podpisy</span><span class="sxs-lookup"><span data-stu-id="95dd3-142">Must match all signatures</span></span>  
 <span data-ttu-id="95dd3-143">V případech, kde je základní typ má více podpisů musí odpovídat úmyslně všechny možné podpisy s implementací konstruktor vlastní, která používá doporučená vzor volání konstruktoru třídy výchozí před nastavením další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95dd3-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="95dd3-144">Nastavení vlastností závislostí s SetValue</span><span class="sxs-lookup"><span data-stu-id="95dd3-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="95dd3-145">Tyto stejné vzory použít, pokud nastavíte vlastnost, která nepodporuje mít obálka pro vlastnost nastavení pohodlí a nastavit hodnoty s <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="95dd3-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="95dd3-146">Vaše volání <xref:System.Windows.DependencyObject.SetValue%2A> této předávání konstruktor parametry měli také zavolat třídu výchozí konstruktor pro inicializaci.</span><span class="sxs-lookup"><span data-stu-id="95dd3-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95dd3-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="95dd3-147">See Also</span></span>  
 [<span data-ttu-id="95dd3-148">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="95dd3-148">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="95dd3-149">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="95dd3-149">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="95dd3-150">Zabezpečení vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="95dd3-150">Dependency Property Security</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
