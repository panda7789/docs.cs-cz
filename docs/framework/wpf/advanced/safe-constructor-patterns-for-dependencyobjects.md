---
title: Zabezpečené vzory konstruktoru pro DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: fce17979fbd43df0496f972cac525fd79dcbfe32
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991818"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Zabezpečené vzory konstruktoru pro DependencyObjects
Obecně konstruktory třídy by neměly volat zpětná volání, jako jsou virtuální metody nebo delegáti, protože konstruktory lze volat jako základní inicializaci konstruktorů pro odvozenou třídu. Vstup do virtuální sítě může být proveden v neúplném stavu inicializace libovolného daného objektu. Systém vlastností však volá a zpřístupňuje zpětná volání interně jako součást systému vlastností závislosti. Jednoduchá operace jako nastavení hodnoty vlastnosti závislosti s <xref:System.Windows.DependencyObject.SetValue%2A> voláním potenciálně zahrnuje zpětné volání někde v rámci určení. Z tohoto důvodu byste měli být opatrní při nastavování hodnot vlastností závislosti v těle konstruktoru, což může být problematické, pokud je typ použit jako základní třída. Existuje konkrétní vzor pro implementaci <xref:System.Windows.DependencyObject> konstruktorů, které zabraňují konkrétním problémům se stavy vlastností závislosti a podpostupům zpětného volání, která jsou popsána zde.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Virtuální metody systému vlastností  
 Následující virtuální metody nebo zpětná volání jsou <xref:System.Windows.DependencyObject.SetValue%2A> potenciálně volány během výpočtů volání, které nastaví hodnotu vlastnosti závislosti: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Každá z těchto virtuálních metod nebo zpětných volání slouží k určitému účelu při rozšiřování univerzálnosti [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastností systému vlastností a závislostí. Další informace o tom, jak tyto virtuální funkce použít k přizpůsobení hodnoty vlastnosti, najdete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Vynucování pravidel FXCop vs. Virtuální systémy vlastností  
 Použijete-li nástroj Microsoft FXCop jako součást procesu sestavení a buď Odvozujete z určitých [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tříd rozhraní, které volají základní konstruktor, nebo implementujete vlastní vlastnosti závislosti na odvozených třídách, může dojít ke konkrétnímu Porušení pravidla FXCop. Řetězec názvu pro toto porušení je:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Toto je pravidlo, které je součástí výchozí veřejné sady pravidel pro FXCop. To, co toto pravidlo může vytvářet, je trasování prostřednictvím systému vlastností závislosti, který nakonec volá virtuální metodu systémové vlastnosti závislosti. Toto porušení pravidla se může dál zobrazovat, i když následují Doporučené vzory konstruktoru popsané v tomto tématu, takže možná budete muset toto pravidlo v konfiguraci sady pravidel FXCop zakázat nebo potlačit.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Většina problémů pochází z odvození tříd, nepoužívá se stávající třídy.  
 Problémy nahlášené tímto pravidlem nastávají, když třída, kterou implementujete s virtuálními metodami v její sekvenci konstrukce, je pak odvozena z. Pokud svou třídu zapečetete nebo jinak znáte nebo vynutili, že vaše třída nebude odvozena z, zde popsané aspekty a problémy, které pravidlo FXCop, neplatí pro vás. Pokud však vytváříte třídy takovým způsobem, že jsou určeny pro použití jako základní třídy, například pokud vytváříte šablony nebo sadu rozbalitelné knihovny ovládacích prvků, měli byste postupovat podle vzorů, které jsou zde doporučeny pro konstruktory.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Výchozí konstruktory musí inicializovat všechny hodnoty požadované pomocí zpětných volání.  
 Všechny členy instance, které jsou používány přepisy nebo zpětnými voláními třídy (zpětná volání ze seznamu v sekci virtuals System), musí být inicializovány v konstruktoru bez parametrů třídy, i když některé z těchto hodnot jsou vyplněny hodnotami "reálného" prostřednictvím parametry konstruktorů bez parametrů.  
  
 Následující příklad kódu (a další příklady) je pseudoC# příklad, který porušuje toto pravidlo a vysvětluje problém:  
  
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
  
 Když volá `new MyClass(objectvalue)`kód aplikace, volá konstruktor bez parametrů a konstruktory základní třídy. Pak nastaví `Property1 = object1`, který volá virtuální metodu `OnPropertyChanged` na vlastnící `MyClass`. <xref:System.Windows.DependencyObject>  Přepsání odkazuje na `_myList`, které ještě nebylo inicializováno.  
  
 Jedním ze způsobů, jak se těmto problémům vyhnout, je zajistit, že zpětná volání používají pouze jiné vlastnosti závislosti a že každá taková vlastnost závislosti má jako součást svých registrovaných metadat výchozí hodnotu.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Vzor bezpečných konstruktorů  
 Chcete-li se vyhnout rizikům neúplné inicializace, pokud je třída použita jako základní třída, postupujte podle těchto vzorů:  
  
#### <a name="parameterless-constructors-calling-base-initialization"></a>Konstruktory bez parametrů volají základní inicializaci  
 Implementujte tyto konstruktory, které volají základní výchozí hodnoty:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Nevýchozí (pohodlí) konstruktory, které neodpovídají žádným základním podpisům  
 Pokud tyto konstruktory používají parametry pro nastavení vlastností závislosti při inicializaci, nejprve zavolejte vlastní konstruktor bez parametrů třídy pro inicializaci a poté pomocí parametrů nastavte vlastnosti závislosti. Můžou to být buď vlastnosti závislosti definované vaší třídou, nebo vlastnosti závislosti zděděné ze základních tříd, ale v obou případech použijte následující vzor:  
  
```csharp  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Nevýchozí (pohodlí) konstruktory, které odpovídají základním podpisům  
 Namísto volání základního konstruktoru se stejným Parametrizace znovu zavolejte vlastní konstruktor bez parametrů. Nevolejte základní inicializátor; místo toho byste měli `this()`volat. Pak znovu vytvořte původní chování konstruktoru pomocí předaných parametrů jako hodnot pro nastavení příslušných vlastností. V dokumentaci k základnímu konstruktoru použijte pokyny k určení vlastností, které jsou určeny k nastavení pro konkrétní parametry:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a>Musí odpovídat všem podpisům  
 V případech, kde má základní typ více signatur, je nutné záměrně porovnat všechny možné podpisy s implementací konstruktoru vlastní, která používá doporučený vzor volání konstruktoru bez parametrů třídy před dalším nastavením. vlastnosti.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Nastavení vlastností závislosti pomocí NastavitHodnotu  
 Tyto stejné vzory platí v případě, že nastavujete vlastnost, která nemá obálku pro usnadnění nastavení vlastností, a nastavíte hodnoty <xref:System.Windows.DependencyObject.SetValue%2A>pomocí. Volání <xref:System.Windows.DependencyObject.SetValue%2A> tohoto konstruktoru Pass by měla také volat konstruktor bez parametrů třídy pro inicializaci.  
  
## <a name="see-also"></a>Viz také:

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
