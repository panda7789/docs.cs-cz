---
title: Zabezpečené vzory konstruktoru pro DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 66e380a9428395c772d0dcfe45a995374774aec6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283829"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="19e94-102">Zabezpečené vzory konstruktoru pro DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="19e94-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="19e94-103">Obecně konstruktory třídy by neměly volat zpětná volání, jako jsou virtuální metody nebo delegáti, protože konstruktory lze volat jako základní inicializaci konstruktorů pro odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="19e94-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="19e94-104">Vstup do virtuální sítě může být proveden v neúplném stavu inicializace libovolného daného objektu.</span><span class="sxs-lookup"><span data-stu-id="19e94-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="19e94-105">Systém vlastností však volá a zpřístupňuje zpětná volání interně jako součást systému vlastností závislosti.</span><span class="sxs-lookup"><span data-stu-id="19e94-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="19e94-106">Jednoduchá operace jako nastavení hodnoty vlastnosti závislosti s <xref:System.Windows.DependencyObject.SetValue%2A> volání potenciálně zahrnuje zpětné volání někde v rámci určení.</span><span class="sxs-lookup"><span data-stu-id="19e94-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="19e94-107">Z tohoto důvodu byste měli být opatrní při nastavování hodnot vlastností závislosti v těle konstruktoru, což může být problematické, pokud je typ použit jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="19e94-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="19e94-108">Existuje konkrétní vzor pro implementaci <xref:System.Windows.DependencyObject> konstruktorů, které zabraňují konkrétním problémům se stavy vlastností závislosti a podpostupům zpětného volání, která jsou popsána zde.</span><span class="sxs-lookup"><span data-stu-id="19e94-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="19e94-109">Virtuální metody systému vlastností</span><span class="sxs-lookup"><span data-stu-id="19e94-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="19e94-110">Následující virtuální metody nebo zpětná volání jsou potenciálně volány během výpočtů <xref:System.Windows.DependencyObject.SetValue%2A> volání, které nastaví hodnotu vlastnosti závislosti: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="19e94-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="19e94-111">Každá z těchto virtuálních metod nebo zpětných volání slouží k určitému účelu při rozšiřování univerzálnosti vlastností systému vlastností [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a závislostí.</span><span class="sxs-lookup"><span data-stu-id="19e94-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="19e94-112">Další informace o tom, jak tyto virtuální funkce použít k přizpůsobení hodnoty vlastnosti, najdete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="19e94-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="19e94-113">Vynucení pravidel FXCop vs. systémové virtuální systémy vlastností</span><span class="sxs-lookup"><span data-stu-id="19e94-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="19e94-114">Použijete-li nástroj Microsoft FXCop jako součást procesu sestavení a buď Odvozujete z určitých tříd [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Framework, které volají základní konstruktor, nebo implementujte své vlastní vlastnosti závislosti na odvozených třídách, může dojít ke konkrétnímu porušení pravidla FXCop.</span><span class="sxs-lookup"><span data-stu-id="19e94-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="19e94-115">Řetězec názvu pro toto porušení je:</span><span class="sxs-lookup"><span data-stu-id="19e94-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="19e94-116">Toto je pravidlo, které je součástí výchozí veřejné sady pravidel pro FXCop.</span><span class="sxs-lookup"><span data-stu-id="19e94-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="19e94-117">To, co toto pravidlo může vytvářet, je trasování prostřednictvím systému vlastností závislosti, který nakonec volá virtuální metodu systémové vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="19e94-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="19e94-118">Toto porušení pravidla se může dál zobrazovat, i když následují Doporučené vzory konstruktoru popsané v tomto tématu, takže možná budete muset toto pravidlo v konfiguraci sady pravidel FXCop zakázat nebo potlačit.</span><span class="sxs-lookup"><span data-stu-id="19e94-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="19e94-119">Většina problémů pochází z odvození tříd, nepoužívá se stávající třídy.</span><span class="sxs-lookup"><span data-stu-id="19e94-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="19e94-120">Problémy nahlášené tímto pravidlem nastávají, když třída, kterou implementujete s virtuálními metodami v její sekvenci konstrukce, je pak odvozena z.</span><span class="sxs-lookup"><span data-stu-id="19e94-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="19e94-121">Pokud svou třídu zapečetete nebo jinak znáte nebo vynutili, že vaše třída nebude odvozena z, zde popsané aspekty a problémy, které pravidlo FXCop, neplatí pro vás.</span><span class="sxs-lookup"><span data-stu-id="19e94-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="19e94-122">Pokud však vytváříte třídy takovým způsobem, že jsou určeny pro použití jako základní třídy, například pokud vytváříte šablony nebo sadu rozbalitelné knihovny ovládacích prvků, měli byste postupovat podle vzorů, které jsou zde doporučeny pro konstruktory.</span><span class="sxs-lookup"><span data-stu-id="19e94-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="19e94-123">Výchozí konstruktory musí inicializovat všechny hodnoty požadované pomocí zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="19e94-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="19e94-124">Všechny členy instance, které jsou používány přepisy nebo zpětnými voláními třídy (zpětná volání ze seznamu v sekci virtuals System), musí být inicializovány v konstruktoru bez parametrů třídy, i když některé z těchto hodnot jsou vyplněny hodnotami "reálného" prostřednictvím parametry konstruktorů bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="19e94-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class parameterless constructor, even if some of those values are filled by "real" values through parameters of the nonparameterless constructors.</span></span>  
  
 <span data-ttu-id="19e94-125">Následující příklad kódu (a další příklady) je pseudoC# příklad, který porušuje toto pravidlo a vysvětluje problém:</span><span class="sxs-lookup"><span data-stu-id="19e94-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="19e94-126">Když kód aplikace volá `new MyClass(objectvalue)`, volá konstruktor bez parametrů a konstruktory základní třídy.</span><span class="sxs-lookup"><span data-stu-id="19e94-126">When application code calls `new MyClass(objectvalue)`, this calls the parameterless constructor and base class constructors.</span></span> <span data-ttu-id="19e94-127">Pak nastaví `Property1 = object1`, která volá virtuální metodu `OnPropertyChanged` na vlastnící `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="19e94-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="19e94-128">Přepsání odkazuje na `_myList`, které ještě nebyly inicializovány.</span><span class="sxs-lookup"><span data-stu-id="19e94-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="19e94-129">Jedním ze způsobů, jak se těmto problémům vyhnout, je zajistit, že zpětná volání používají pouze jiné vlastnosti závislosti a že každá taková vlastnost závislosti má jako součást svých registrovaných metadat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="19e94-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="19e94-130">Vzor bezpečných konstruktorů</span><span class="sxs-lookup"><span data-stu-id="19e94-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="19e94-131">Chcete-li se vyhnout rizikům neúplné inicializace, pokud je třída použita jako základní třída, postupujte podle těchto vzorů:</span><span class="sxs-lookup"><span data-stu-id="19e94-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a><span data-ttu-id="19e94-132">Konstruktory bez parametrů volají základní inicializaci</span><span class="sxs-lookup"><span data-stu-id="19e94-132">Parameterless constructors calling base initialization</span></span>  
 <span data-ttu-id="19e94-133">Implementujte tyto konstruktory, které volají základní výchozí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="19e94-133">Implement these constructors calling the base default:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="19e94-134">Nevýchozí (pohodlí) konstruktory, které neodpovídají žádným základním podpisům</span><span class="sxs-lookup"><span data-stu-id="19e94-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="19e94-135">Pokud tyto konstruktory používají parametry pro nastavení vlastností závislosti při inicializaci, nejprve zavolejte vlastní konstruktor bez parametrů třídy pro inicializaci a poté pomocí parametrů nastavte vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="19e94-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class parameterless constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="19e94-136">Můžou to být buď vlastnosti závislosti definované vaší třídou, nebo vlastnosti závislosti zděděné ze základních tříd, ale v obou případech použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="19e94-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="19e94-137">Nevýchozí (pohodlí) konstruktory, které odpovídají základním podpisům</span><span class="sxs-lookup"><span data-stu-id="19e94-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="19e94-138">Namísto volání základního konstruktoru se stejným Parametrizace znovu zavolejte vlastní konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="19e94-138">Instead of calling the base constructor with the same parameterization, again call your own class' parameterless constructor.</span></span> <span data-ttu-id="19e94-139">Nevolejte základní inicializátor; místo toho byste měli volat `this()`.</span><span class="sxs-lookup"><span data-stu-id="19e94-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="19e94-140">Pak znovu vytvořte původní chování konstruktoru pomocí předaných parametrů jako hodnot pro nastavení příslušných vlastností.</span><span class="sxs-lookup"><span data-stu-id="19e94-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="19e94-141">V dokumentaci k základnímu konstruktoru použijte pokyny k určení vlastností, které jsou určeny k nastavení pro konkrétní parametry:</span><span class="sxs-lookup"><span data-stu-id="19e94-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="19e94-142">Musí odpovídat všem podpisům</span><span class="sxs-lookup"><span data-stu-id="19e94-142">Must match all signatures</span></span>  
 <span data-ttu-id="19e94-143">V případech, kde má základní typ více signatur, je nutné záměrně porovnat všechny možné podpisy s implementací konstruktoru vlastní, která používá doporučený vzor volání konstruktoru bez parametrů třídy před dalším nastavením. vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="19e94-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class parameterless constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="19e94-144">Nastavení vlastností závislosti pomocí NastavitHodnotu</span><span class="sxs-lookup"><span data-stu-id="19e94-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="19e94-145">Tyto stejné vzory platí v případě, že nastavujete vlastnost, která nemá obálku pro usnadnění nastavení vlastností, a nastavíte hodnoty pomocí <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="19e94-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="19e94-146">Vaše volání <xref:System.Windows.DependencyObject.SetValue%2A>, která přecházejí do parametrů konstruktoru, by měla také volat konstruktor bez parametrů třídy pro inicializaci.</span><span class="sxs-lookup"><span data-stu-id="19e94-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' parameterless constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19e94-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19e94-147">See also</span></span>

- [<span data-ttu-id="19e94-148">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="19e94-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="19e94-149">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="19e94-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="19e94-150">Zabezpečení vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="19e94-150">Dependency Property Security</span></span>](dependency-property-security.md)
