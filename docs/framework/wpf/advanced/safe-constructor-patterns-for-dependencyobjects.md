---
title: Zabezpečené vzory konstruktoru pro DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: 03615c1c49f2acf2a7c7f0910860f36de0a4f2d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547339"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Zabezpečené vzory konstruktoru pro DependencyObjects
Konstruktory – třída obecně platí, by neměl volání zpětná volání, jako je například virtuální metody nebo delegáti, protože konstruktory lze volat jako základní inicializace konstruktory odvozené třídy. Zadání virtuální může být provedena do stavu neúplná inicializace libovolného objektu. Ale samotného systému vlastnost volá a zveřejňuje zpětná volání interně v rámci systému vlastnost závislosti. Jednoduché operace jako nastavení hodnoty vlastnosti závislosti s <xref:System.Windows.DependencyObject.SetValue%2A> volání potenciálně zahrnuje zpětné volání někde pro zjišťování. Z tohoto důvodu byste měli být opatrní při nastavení hodnoty vlastností v textu konstruktor, který se může stát problematické, pokud váš typ se používá jako základní třída závislostí. Je určitý vzor pro implementaci <xref:System.Windows.DependencyObject> konstruktory, které zabraňuje konkrétních problémů s stavy vlastnost závislosti a vyplývajících zpětná volání, které jsou zde uvedeny.  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Vlastnost systému virtuální metody  
 Následující virtuální metody nebo zpětná volání jsou potenciálně volá se během výpočty z <xref:System.Windows.DependencyObject.SetValue%2A> volání, které nastavuje hodnotu vlastnosti závislosti: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Každý z těchto virtuální metody nebo zpětná volání slouží určitý účel v rozšíření všestrannost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systém a závislosti vlastnosti. Další informace o tom, jak použít tyto virtuals k přizpůsobení rozhodnutí hodnotu vlastnosti, najdete v části [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Vynucení pravidla FXCop vs. Vlastnost systému Virtuals  
 Pokud použijete nástroj Microsoft FXCop jako součást procesu sestavení a buď odvozujete od určité [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání konstruktoru základní třídy rozhraní framework nebo implementovat vlastní vlastností závislostí v odvozených třídách, může dojít k konkrétní Porušení pravidel FXCop. Název řetězce pro tento porušení je:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Toto je pravidlo, které je součástí výchozí sada pro FXCop veřejné pravidel. Co toto pravidlo může být vytváření sestav je trasování prostřednictvím systému vlastnost závislostí, který nakonec volá metodu virtuálního systému vlastnost závislosti. Toto pravidlo porušení může nadále zobrazovat i po následující doporučené konstruktor vzory popsané v tomto tématu se proto může být třeba zakázat nebo potlačit v konfiguraci sady pravidel FXCop daného pravidla.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Většiny problémů pocházet z odvozující třídy, ne pomocí existujících tříd  
 Problémy hlášené tímto pravidlem nastane, když je třída, která můžete implementovat s virtuální metody v jeho pořadí vytváření pak odvozený od. Pokud zapečetit vaší třídy, nebo jinak vědět nebo vynutit, aby třídě nebude být odvozen od, jaké jsou požadavky popsané tady a problémy, které opodstatněny pravidlo FXCop se nevztahují na vás. Ale pokud autorizujete třídy tak, že jsou určeny k použití jako základní třídy pro instanci Pokud vytváříte šablony, nebo rozšíření řízení knihovny, postupujte podle zde doporučené pro konstruktory vzory.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Výchozí konstruktory musí inicializovat všechny hodnoty požadoval zpětných volání  
 U členů instancí, které jsou používány třída přepsání nebo zpětných volání (zpětná volání v seznamu v části Vlastnosti systému Virtuals) se musí inicializovat ve vaší třídy výchozí konstruktor, i v případě, že některé z těchto hodnot jsou vyplněny "Skutečná" hodnoty prostřednictvím Parametry jiný než výchozí konstruktory.  
  
 Následující příklad kódu (a další příklady) se svého – příklad jazyka C#, která porušuje toto pravidlo a vysvětluje problému:  
  
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
  
 Pokud kód aplikace volá `new MyClass(objectvalue)`, volá výchozí konstruktor a základní třídy konstruktory. Potom nastaví `Property1 = object1`, která volá metodu virtuální `OnPropertyChanged` na vlastnící `MyClass` <xref:System.Windows.DependencyObject>.  Přepsání odkazuje na `_myList`, která ještě nebyla inicializována.  
  
 Jedním ze způsobů, abyste se těmto problémům je zajistit, že zpětná volání používat pouze ostatní vlastnosti závislosti, a že každý tato vlastnost závislosti zavedených výchozí hodnota v rámci jeho registrované metadata.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Vzory bezpečné konstruktor  
 Chcete-li zamezit rizikům neúplná inicializace, pokud vaše třída se používá jako základní třída, postupujte podle tyto vzory:  
  
#### <a name="default-constructors-calling-base-initialization"></a>Výchozí konstruktory volání základní inicializace  
 Implementujte tyto konstruktory volání základní výchozí nastavení:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory (pohodlí) jiné než výchozí, neodpovídá žádné základní podpisy  
 Pokud tyto konstruktory používat parametry pro nastavení vlastností závislostí při inicializaci, první volání vlastní třída výchozí konstruktor pro inicializaci a pak pomocí parametrů pro nastavení vlastností závislostí. To může buď být definované třídu vlastností závislostí nebo vlastností závislostí dědí z třídy base, ale v obou případech používají následující vzorec:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Konstruktory, jiné než výchozí (pohodlí), které neodpovídají základní podpisy  
 Namísto volání základní konstruktor s stejné Parametrizace, opakujte volání vlastní třídu výchozí konstruktor. Nevolejte základní inicializátoru; Místo toho by měly volat `this()`. Pak opakovat původní chování konstruktor pomocí předaných parametrů jako hodnoty pro nastavení relevantní vlastnosti. Použití v původní dokumentaci konstruktor základní pokyny k určení vlastností, které konkrétní parametry jsou určená k nastavení:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Musí odpovídat všechny podpisy  
 V případech, kde je základní typ má více podpisů musí odpovídat úmyslně všechny možné podpisy s implementací konstruktor vlastní, která používá doporučená vzor volání konstruktoru třídy výchozí před nastavením další vlastnosti.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Nastavení vlastností závislostí s SetValue  
 Tyto stejné vzory použít, pokud nastavíte vlastnost, která nepodporuje mít obálka pro vlastnost nastavení pohodlí a nastavit hodnoty s <xref:System.Windows.DependencyObject.SetValue%2A>. Vaše volání <xref:System.Windows.DependencyObject.SetValue%2A> této předávání konstruktor parametry měli také zavolat třídu výchozí konstruktor pro inicializaci.  
  
## <a name="see-also"></a>Viz také  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Zabezpečení vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
