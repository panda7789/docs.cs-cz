---
title: Zabezpečené vzory konstruktoru pro DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 6d6ff444b99ca893e687731c56a48ea3ac072dd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187235"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="ad909-102">Zabezpečené vzory konstruktoru pro DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="ad909-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="ad909-103">Obecně platí, že konstruktory třídy by neměly volat zpětná volání, jako jsou virtuální metody nebo delegáti, protože konstruktory mohou být volány jako základní inicializace konstruktorů pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="ad909-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="ad909-104">Zadání virtuální může být provedeno v neúplném stavu inicializace daného objektu.</span><span class="sxs-lookup"><span data-stu-id="ad909-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="ad909-105">Samotný systém vlastností však volá a zpřístupňuje zpětná volání interně jako součást systému vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="ad909-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="ad909-106">Tak jednoduché operace jako nastavení hodnoty <xref:System.Windows.DependencyObject.SetValue%2A> vlastnosti závislosti s voláním potenciálně zahrnuje zpětné volání někde v určení.</span><span class="sxs-lookup"><span data-stu-id="ad909-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="ad909-107">Z tohoto důvodu byste měli být opatrní při nastavování hodnot vlastností závislostí v těle konstruktoru, což může být problematické, pokud je váš typ použit jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="ad909-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="ad909-108">Existuje zvláštní vzor pro <xref:System.Windows.DependencyObject> implementaci konstruktory, které se vyhýbá konkrétní problémy se stavy vlastností závislostí a vlastní zpětná volání, která je dokumentována zde.</span><span class="sxs-lookup"><span data-stu-id="ad909-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a><span data-ttu-id="ad909-109">Virtuální metody systému vlastností</span><span class="sxs-lookup"><span data-stu-id="ad909-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="ad909-110">Následující virtuální metody nebo zpětná volání jsou potenciálně volány <xref:System.Windows.DependencyObject.SetValue%2A> během výpočtů volání, <xref:System.Windows.ValidateValueCallback>které <xref:System.Windows.PropertyChangedCallback> <xref:System.Windows.CoerceValueCallback>nastavuje hodnotu vlastnosti závislosti: , , , <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad909-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="ad909-111">Každá z těchto virtuálních metod nebo zpětná volání slouží k určitému účelu při rozšiřování všestrannosti vlastností systému [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="ad909-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="ad909-112">Další informace o použití těchto virtuals přizpůsobit určení hodnoty [vlastností,](dependency-property-callbacks-and-validation.md)naleznete v tématu závislost vlastnost i ověření .</span><span class="sxs-lookup"><span data-stu-id="ad909-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="ad909-113">FXCop rulesti vs vlastnictví systému Virtuals</span><span class="sxs-lookup"><span data-stu-id="ad909-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="ad909-114">Pokud používáte nástroj Microsoft FXCop jako součást procesu sestavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a buď odvodit z určité třídy architektury volání základní konstruktoru nebo implementovat vlastní vlastnosti závislostí na odvozené třídy, může dojít k porušení určité hosto.</span><span class="sxs-lookup"><span data-stu-id="ad909-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="ad909-115">Řetězec názvu pro toto porušení je:</span><span class="sxs-lookup"><span data-stu-id="ad909-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="ad909-116">Toto je pravidlo, které je součástí výchozí veřejné pravidlo sady pro FXCop.</span><span class="sxs-lookup"><span data-stu-id="ad909-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="ad909-117">Toto pravidlo může být vykazování je trasování prostřednictvím systému vlastností závislostí, který nakonec volá virtuální metodu systému vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="ad909-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="ad909-118">Toto porušení pravidel může nadále zobrazovat i po následující doporučené vzory konstruktoru zdokumentované v tomto tématu, takže budete muset zakázat nebo potlačit toto pravidlo v konfiguraci sady pravidel FXCop.</span><span class="sxs-lookup"><span data-stu-id="ad909-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="ad909-119">Většina problémů pochází z odvození tříd, nepoužívání existujících tříd</span><span class="sxs-lookup"><span data-stu-id="ad909-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="ad909-120">Problémy hlášené tímto pravidlem dojít, když třída, kterou implementujete s virtuální metody v jeho pořadí konstrukce je pak odvozen od.</span><span class="sxs-lookup"><span data-stu-id="ad909-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="ad909-121">Pokud zapečetíte svou třídu nebo jinak víte nebo vynucujete, že vaše třída nebude odvozena z, úvahy zde vysvětlené a problémy, které motivovaly pravidlo FXCop, se na vás nevztahují.</span><span class="sxs-lookup"><span data-stu-id="ad909-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="ad909-122">Pokud však vytváříte třídy takovým způsobem, že jsou určeny k použití jako základní třídy, například pokud vytváříte šablony nebo rozšiřitelnou sadu knihovny ovládacích prvků, měli byste postupovat podle vzorů doporučených zde pro konstruktory.</span><span class="sxs-lookup"><span data-stu-id="ad909-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="ad909-123">Výchozí konstruktory musí inicializovat všechny hodnoty požadované zpětná volání</span><span class="sxs-lookup"><span data-stu-id="ad909-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="ad909-124">Všechny členy instance, které jsou používány přepsání třídy nebo zpětná volání (zpětná volání ze seznamu v části Property System Virtuals) musí být inicializovány ve vaší třídy konstruktoru bez parametrů, i když některé z těchto hodnot jsou vyplněny "skutečné" hodnoty prostřednictvím parametry konstruktérů bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="ad909-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="ad909-125">Následující ukázkový kód (a následné příklady) je pseudo-C# příklad, který porušuje toto pravidlo a vysvětluje problém:</span><span class="sxs-lookup"><span data-stu-id="ad909-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="ad909-126">Při volání `new MyClass(objectvalue)`kódu aplikace volá konstruktor bez parametrů a konstruktory základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ad909-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="ad909-127">Pak se `Property1 = object1`nastaví , `OnPropertyChanged` který volá `MyClass` <xref:System.Windows.DependencyObject>virtuální metodu na vlastnící .</span><span class="sxs-lookup"><span data-stu-id="ad909-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="ad909-128">Přepsání odkazuje `_myList`na , který ještě nebyl inicializován.</span><span class="sxs-lookup"><span data-stu-id="ad909-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="ad909-129">Jedním ze způsobů, jak se těmto problémům vyhnout, je zajistit, aby zpětná volání používala pouze jiné vlastnosti závislostí a aby každá taková vlastnost závislosti má nastavenou výchozí hodnotu jako součást registrovaných metadat.</span><span class="sxs-lookup"><span data-stu-id="ad909-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a><span data-ttu-id="ad909-130">Bezpečné vzory konstruktoru</span><span class="sxs-lookup"><span data-stu-id="ad909-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="ad909-131">Chcete-li se vyhnout rizikům neúplné inicializace, pokud je vaše třída použita jako základní třída, postupujte podle těchto vzorů:</span><span class="sxs-lookup"><span data-stu-id="ad909-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="ad909-132">Konstruktory bez parametrů volající základní inicializaci</span><span class="sxs-lookup"><span data-stu-id="ad909-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="ad909-133">Implementujte tyto konstruktory, které volají výchozí výchozí hodnotu:</span><span class="sxs-lookup"><span data-stu-id="ad909-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="ad909-134">Konstruktory, které nejsou výchozí (pohodlné), neodpovídají žádným základním podpisům</span><span class="sxs-lookup"><span data-stu-id="ad909-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="ad909-135">Pokud tyto konstruktory použít parametry nastavit vlastnosti závislostí v inicializaci, nejprve volat vlastní třídy bezparametrický konstruktor pro inicializaci a potom použijte parametry pro nastavení vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="ad909-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="ad909-136">Mohou to být buď vlastnosti závislostí definované vaší třídou, nebo vlastnosti závislosti zděděné ze základních tříd, ale v obou případech použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="ad909-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="ad909-137">Konstruktory, které nejsou výchozí (pohodlné), které odpovídají základním podpisům</span><span class="sxs-lookup"><span data-stu-id="ad909-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="ad909-138">Namísto volání základní konstruktor se stejnou parametrizací, znovu volat vlastní třídy konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="ad909-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="ad909-139">Nevolejte základní inicializátor; místo toho `this()`byste měli zavolat .</span><span class="sxs-lookup"><span data-stu-id="ad909-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="ad909-140">Potom reprodukovat původní chování konstruktoru pomocí předané parametry jako hodnoty pro nastavení příslušné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ad909-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="ad909-141">Použijte původní základní konstruktor dokumentace pro navádění při určování vlastností, které jsou určeny pro konkrétní parametry nastavit:</span><span class="sxs-lookup"><span data-stu-id="ad909-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="ad909-142">Musí odpovídat všem podpisům.</span><span class="sxs-lookup"><span data-stu-id="ad909-142">Must match all signatures</span></span>  
 <span data-ttu-id="ad909-143">V případech, kdy základní typ má více podpisů, je nutné záměrně sladit všechny možné podpisy s vlastní implementací konstruktoru, který používá doporučený vzor volání konstruktoru třídy bez parametrů před dalším nastavením Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ad909-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="ad909-144">Nastavení vlastností závislosti pomocí funkce SetValue</span><span class="sxs-lookup"><span data-stu-id="ad909-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="ad909-145">Tyto stejné vzory platí, pokud nastavujete vlastnost, která nemá obálku pro <xref:System.Windows.DependencyObject.SetValue%2A>pohodlí nastavení vlastnosti a nastavte hodnoty s .</span><span class="sxs-lookup"><span data-stu-id="ad909-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="ad909-146">Vaše volání, <xref:System.Windows.DependencyObject.SetValue%2A> které procházejí parametry konstruktoru by také volání třídy konstruktor bez parametrů pro inicializaci.</span><span class="sxs-lookup"><span data-stu-id="ad909-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad909-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad909-147">See also</span></span>

- [<span data-ttu-id="ad909-148">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="ad909-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="ad909-149">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="ad909-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="ad909-150">Zabezpečení vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="ad909-150">Dependency Property Security</span></span>](dependency-property-security.md)
