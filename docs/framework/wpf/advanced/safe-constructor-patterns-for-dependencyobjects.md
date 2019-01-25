---
title: Zabezpečené vzory konstruktoru pro DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 8e9e2f83e15e4e1703ed42dfb479efb8feed3bb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661279"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="75da6-102">Zabezpečené vzory konstruktoru pro DependencyObjects</span><span class="sxs-lookup"><span data-stu-id="75da6-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="75da6-103">Obecně platí konstruktor třídy neměli volat zpětná volání, jako je například virtuální metody nebo delegátů, protože konstruktory lze volat jako základní inicializace konstruktory odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="75da6-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="75da6-104">Zadání virtuálního může být provedeno stavu neúplná inicializace libovolný daný objekt.</span><span class="sxs-lookup"><span data-stu-id="75da6-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="75da6-105">Však samotný systém vlastnost volá a zpřístupňuje zpětná volání interně jako součást v systému vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="75da6-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="75da6-106">Jednoduché operace jako nastavení hodnoty vlastnosti závislostí s <xref:System.Windows.DependencyObject.SetValue%2A> volání může potenciálně zahrnout zpětné volání někde v určení.</span><span class="sxs-lookup"><span data-stu-id="75da6-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="75da6-107">Z tohoto důvodu byste měli být opatrní při nastavení hodnoty vlastností v těle konstruktoru, který může být problematické, pokud se typ používá jako základní třída závislostí.</span><span class="sxs-lookup"><span data-stu-id="75da6-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="75da6-108">Neexistuje konkrétní vzor pro implementování <xref:System.Windows.DependencyObject> konstruktory, které předchází konkrétní problémy se stavy vlastnost závislostí a přináší zpětná volání, které jsou zde uvedeny.</span><span class="sxs-lookup"><span data-stu-id="75da6-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="75da6-109">Virtuální metody vlastností systému</span><span class="sxs-lookup"><span data-stu-id="75da6-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="75da6-110">Následující virtuální metody nebo zpětná volání jsou potenciálně volány během výpočty z <xref:System.Windows.DependencyObject.SetValue%2A> volání, která nastaví hodnotu vlastnosti závislosti: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="75da6-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="75da6-111">Každá z těchto virtuální metody nebo zpětná volání slouží konkrétní účel rozšíření všestrannost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systém a závislosti vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75da6-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="75da6-112">Další informace o tom, jak pomocí těchto virtuálních funkcí: můžete přizpůsobit stanovení hodnotu vlastnosti, naleznete v tématu [vlastnost závislosti zpětné volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span><span class="sxs-lookup"><span data-stu-id="75da6-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="75da6-113">Vynucení pravidel FXCop vs. Vlastnost systému virtuálních funkcí:</span><span class="sxs-lookup"><span data-stu-id="75da6-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="75da6-114">Pokud používáte nástroj Microsoft FXCop jako součást procesu sestavení a buď odvozovat z některých [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání konstruktoru základní třídy rozhraní framework nebo implementovat vlastní vlastnosti závislosti v odvozených třídách, může dojít konkrétní Porušení pravidla FXCop.</span><span class="sxs-lookup"><span data-stu-id="75da6-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="75da6-115">Název řetězce pro toto porušení je:</span><span class="sxs-lookup"><span data-stu-id="75da6-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="75da6-116">Toto je pravidlo, které je součástí výchozí sady pro FXCop veřejné pravidel.</span><span class="sxs-lookup"><span data-stu-id="75da6-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="75da6-117">Co toto pravidlo může být vytváření sestav je trasování prostřednictvím systému vlastnost závislosti, které nakonec volání virtuální metody systému vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="75da6-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="75da6-118">Porušení tohoto pravidla může nadále zobrazovat i po provedení vzory doporučené konstruktoru popsané v tomto tématu, můžete potřebovat k zakázání nebo potlačení tímto pravidlem ve vaší konfiguraci sady pravidel FXCop.</span><span class="sxs-lookup"><span data-stu-id="75da6-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="75da6-119">Většinu problémů pocházejí z odvozená třídy bez použití existujících tříd</span><span class="sxs-lookup"><span data-stu-id="75da6-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="75da6-120">Problémy hlášené tímto pravidlem dojít, když je třída, která můžete implementovat virtuální metody v jeho pořadí konstrukce pak odvozen z.</span><span class="sxs-lookup"><span data-stu-id="75da6-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="75da6-121">Pokud zapečeťte třídu, nebo jinak vědět nebo vynutit, nebude vaše třída odvozena od, na základě aspektů je zde vysvětleno a na vás nemusí vztahovat problémy, které opodstatněny pravidlo FXCop.</span><span class="sxs-lookup"><span data-stu-id="75da6-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="75da6-122">Nicméně pokud autorizujete třídy tak, že jsou určeny pro použití jako základní třídy pro instanci Pokud při vytváření šablony, nebo knihovna rozšíření ovládacích prvků, postupujte podle vzorů zde doporučeného pro konstruktory.</span><span class="sxs-lookup"><span data-stu-id="75da6-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="75da6-123">Výchozí konstruktory musí inicializovat všechny hodnoty požadoval zpětná volání</span><span class="sxs-lookup"><span data-stu-id="75da6-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="75da6-124">U členů instancí, které používají třídy přepsání nebo zpětná volání (zpětná volání ze seznamu v části Vlastnosti systému virtuálních funkcí:) musí být inicializován ve výchozí konstruktor třídy, i když některé z těchto hodnot se sestavil "real" hodnoty prostřednictvím Parametry jiný než výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="75da6-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="75da6-125">Následující příklad kódu (a další příklady) je pseudo -C# příklad poruší toto pravidlo a vysvětluje problému:</span><span class="sxs-lookup"><span data-stu-id="75da6-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="75da6-126">Když kód aplikace volá `new MyClass(objectvalue)`, volá výchozí konstruktor a základní třídy konstruktory.</span><span class="sxs-lookup"><span data-stu-id="75da6-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="75da6-127">Potom nastaví `Property1 = object1`, která volá metodu virtuální `OnPropertyChanged` na vlastnící `MyClass` <xref:System.Windows.DependencyObject>.</span><span class="sxs-lookup"><span data-stu-id="75da6-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="75da6-128">Přepsání odkazuje na `_myList`, která dosud nebyla inicializována.</span><span class="sxs-lookup"><span data-stu-id="75da6-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="75da6-129">Abyste měli jistotu, že zpětná volání používat jenom jiné vlastnosti závislosti, a že každé takové vlastnost závislosti zavedené výchozí hodnotu jako součást jeho registrované metadata je jedním ze způsobů, abyste se těmto problémům.</span><span class="sxs-lookup"><span data-stu-id="75da6-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="75da6-130">Zabezpečené vzory konstruktoru</span><span class="sxs-lookup"><span data-stu-id="75da6-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="75da6-131">Zamezit neúplná inicializace Pokud vaše třída se používá jako základní třída, postupujte podle těchto vzorců:</span><span class="sxs-lookup"><span data-stu-id="75da6-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="75da6-132">Výchozí konstruktory základního inicializace volání</span><span class="sxs-lookup"><span data-stu-id="75da6-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="75da6-133">Tyto konstruktory volání základní výchozí implementace:</span><span class="sxs-lookup"><span data-stu-id="75da6-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="75da6-134">Konstruktory jiné než výchozí (pohodlí), neodpovídá žádné základní podpisy</span><span class="sxs-lookup"><span data-stu-id="75da6-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="75da6-135">Pokud tyto konstruktory pomocí parametrů můžete nastavit vlastnosti závislostí při inicializaci, nejprve zavolat vlastní výchozí konstruktor třídy pro inicializaci a pak pomocí parametrů můžete nastavit vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="75da6-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="75da6-136">Toto může buď být definované třídě vlastnosti závislosti nebo závislosti vlastnosti zděděné ze základní třídy, ale v obou případech používají následující vzor:</span><span class="sxs-lookup"><span data-stu-id="75da6-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="75da6-137">Jiné než výchozí (pohodlí) konstruktory, které odpovídají základní podpisy</span><span class="sxs-lookup"><span data-stu-id="75da6-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="75da6-138">Místo volat konstruktor základní třídy pomocí stejné Parametrizace, znovu zavolejte vlastní třídu výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="75da6-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="75da6-139">Nevolejte základní inicializátor; Místo toho byste měli volat `this()`.</span><span class="sxs-lookup"><span data-stu-id="75da6-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="75da6-140">Pak pomocí předaných parametrů jako hodnoty pro nastavení vlastnosti důležité opakovat původní chování konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="75da6-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="75da6-141">Použití původní základní konstruktor dokumentaci pokyny k určení vlastností, které konkrétní parametry jsou určené pro nastavení:</span><span class="sxs-lookup"><span data-stu-id="75da6-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="75da6-142">Musí odpovídat všechny podpisy</span><span class="sxs-lookup"><span data-stu-id="75da6-142">Must match all signatures</span></span>  
 <span data-ttu-id="75da6-143">V případech, kdy základní typ má více podpisů musí odpovídat záměrně všechny možné podpisy s implementací konstruktoru vlastní, která používá doporučená vzor volání výchozího konstruktoru třídy před nastavením další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="75da6-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="75da6-144">Nastavení vlastností závislostí s SetValue</span><span class="sxs-lookup"><span data-stu-id="75da6-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="75da6-145">Tyto stejné vzory se dají použít, pokud nastavíte vlastnost, která bez obálku pro vlastnost nastavení pohodlí a nastavte hodnoty s <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="75da6-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="75da6-146">Vaše volání <xref:System.Windows.DependencyObject.SetValue%2A> této předávat parametry konstruktoru byste také zavolat třídy výchozí konstruktor pro inicializaci.</span><span class="sxs-lookup"><span data-stu-id="75da6-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75da6-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75da6-147">See also</span></span>
- [<span data-ttu-id="75da6-148">Vlastní vlastnosti závislosti</span><span class="sxs-lookup"><span data-stu-id="75da6-148">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
- [<span data-ttu-id="75da6-149">Přehled vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="75da6-149">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
- [<span data-ttu-id="75da6-150">Zabezpečení vlastností závislosti</span><span class="sxs-lookup"><span data-stu-id="75da6-150">Dependency Property Security</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
