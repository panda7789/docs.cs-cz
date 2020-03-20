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
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Zabezpečené vzory konstruktoru pro DependencyObjects
Obecně platí, že konstruktory třídy by neměly volat zpětná volání, jako jsou virtuální metody nebo delegáti, protože konstruktory mohou být volány jako základní inicializace konstruktorů pro odvozenou třídu. Zadání virtuální může být provedeno v neúplném stavu inicializace daného objektu. Samotný systém vlastností však volá a zpřístupňuje zpětná volání interně jako součást systému vlastností závislostí. Tak jednoduché operace jako nastavení hodnoty <xref:System.Windows.DependencyObject.SetValue%2A> vlastnosti závislosti s voláním potenciálně zahrnuje zpětné volání někde v určení. Z tohoto důvodu byste měli být opatrní při nastavování hodnot vlastností závislostí v těle konstruktoru, což může být problematické, pokud je váš typ použit jako základní třída. Existuje zvláštní vzor pro <xref:System.Windows.DependencyObject> implementaci konstruktory, které se vyhýbá konkrétní problémy se stavy vlastností závislostí a vlastní zpětná volání, která je dokumentována zde.  

<a name="Property_System_Virtual_Methods"></a>
## <a name="property-system-virtual-methods"></a>Virtuální metody systému vlastností  
 Následující virtuální metody nebo zpětná volání jsou potenciálně volány <xref:System.Windows.DependencyObject.SetValue%2A> během výpočtů volání, <xref:System.Windows.ValidateValueCallback>které <xref:System.Windows.PropertyChangedCallback> <xref:System.Windows.CoerceValueCallback>nastavuje hodnotu vlastnosti závislosti: , , , <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Každá z těchto virtuálních metod nebo zpětná volání slouží k určitému účelu při rozšiřování všestrannosti vlastností systému [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a vlastností závislostí. Další informace o použití těchto virtuals přizpůsobit určení hodnoty [vlastností,](dependency-property-callbacks-and-validation.md)naleznete v tématu závislost vlastnost i ověření .  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>FXCop rulesti vs vlastnictví systému Virtuals  
 Pokud používáte nástroj Microsoft FXCop jako součást procesu sestavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a buď odvodit z určité třídy architektury volání základní konstruktoru nebo implementovat vlastní vlastnosti závislostí na odvozené třídy, může dojít k porušení určité hosto. Řetězec názvu pro toto porušení je:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Toto je pravidlo, které je součástí výchozí veřejné pravidlo sady pro FXCop. Toto pravidlo může být vykazování je trasování prostřednictvím systému vlastností závislostí, který nakonec volá virtuální metodu systému vlastností závislostí. Toto porušení pravidel může nadále zobrazovat i po následující doporučené vzory konstruktoru zdokumentované v tomto tématu, takže budete muset zakázat nebo potlačit toto pravidlo v konfiguraci sady pravidel FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Většina problémů pochází z odvození tříd, nepoužívání existujících tříd  
 Problémy hlášené tímto pravidlem dojít, když třída, kterou implementujete s virtuální metody v jeho pořadí konstrukce je pak odvozen od. Pokud zapečetíte svou třídu nebo jinak víte nebo vynucujete, že vaše třída nebude odvozena z, úvahy zde vysvětlené a problémy, které motivovaly pravidlo FXCop, se na vás nevztahují. Pokud však vytváříte třídy takovým způsobem, že jsou určeny k použití jako základní třídy, například pokud vytváříte šablony nebo rozšiřitelnou sadu knihovny ovládacích prvků, měli byste postupovat podle vzorů doporučených zde pro konstruktory.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Výchozí konstruktory musí inicializovat všechny hodnoty požadované zpětná volání  
 Všechny členy instance, které jsou používány přepsání třídy nebo zpětná volání (zpětná volání ze seznamu v části Property System Virtuals) musí být inicializovány ve vaší třídy konstruktoru bez parametrů, i když některé z těchto hodnot jsou vyplněny "skutečné" hodnoty prostřednictvím parametry konstruktérů bez parametrů.  
  
 Následující ukázkový kód (a následné příklady) je pseudo-C# příklad, který porušuje toto pravidlo a vysvětluje problém:  
  
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
  
 Při volání `new MyClass(objectvalue)`kódu aplikace volá konstruktor bez parametrů a konstruktory základní třídy. Pak se `Property1 = object1`nastaví , `OnPropertyChanged` který volá `MyClass` <xref:System.Windows.DependencyObject>virtuální metodu na vlastnící .  Přepsání odkazuje `_myList`na , který ještě nebyl inicializován.  
  
 Jedním ze způsobů, jak se těmto problémům vyhnout, je zajistit, aby zpětná volání používala pouze jiné vlastnosti závislostí a aby každá taková vlastnost závislosti má nastavenou výchozí hodnotu jako součást registrovaných metadat.  
  
<a name="Safe_Constructor_Patterns"></a>
## <a name="safe-constructor-patterns"></a>Bezpečné vzory konstruktoru  
 Chcete-li se vyhnout rizikům neúplné inicializace, pokud je vaše třída použita jako základní třída, postupujte podle těchto vzorů:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Konstruktory bez parametrů volající základní inicializaci  
 Implementujte tyto konstruktory, které volají výchozí výchozí hodnotu:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory, které nejsou výchozí (pohodlné), neodpovídají žádným základním podpisům  
 Pokud tyto konstruktory použít parametry nastavit vlastnosti závislostí v inicializaci, nejprve volat vlastní třídy bezparametrický konstruktor pro inicializaci a potom použijte parametry pro nastavení vlastností závislostí. Mohou to být buď vlastnosti závislostí definované vaší třídou, nebo vlastnosti závislosti zděděné ze základních tříd, ale v obou případech použijte následující vzor:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Konstruktory, které nejsou výchozí (pohodlné), které odpovídají základním podpisům  
 Namísto volání základní konstruktor se stejnou parametrizací, znovu volat vlastní třídy konstruktor bez parametrů. Nevolejte základní inicializátor; místo toho `this()`byste měli zavolat . Potom reprodukovat původní chování konstruktoru pomocí předané parametry jako hodnoty pro nastavení příslušné vlastnosti. Použijte původní základní konstruktor dokumentace pro navádění při určování vlastností, které jsou určeny pro konkrétní parametry nastavit:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Musí odpovídat všem podpisům.  
 V případech, kdy základní typ má více podpisů, je nutné záměrně sladit všechny možné podpisy s vlastní implementací konstruktoru, který používá doporučený vzor volání konstruktoru třídy bez parametrů před dalším nastavením Vlastnosti.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Nastavení vlastností závislosti pomocí funkce SetValue  
 Tyto stejné vzory platí, pokud nastavujete vlastnost, která nemá obálku pro <xref:System.Windows.DependencyObject.SetValue%2A>pohodlí nastavení vlastnosti a nastavte hodnoty s . Vaše volání, <xref:System.Windows.DependencyObject.SetValue%2A> které procházejí parametry konstruktoru by také volání třídy konstruktor bez parametrů pro inicializaci.  
  
## <a name="see-also"></a>Viz také

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
