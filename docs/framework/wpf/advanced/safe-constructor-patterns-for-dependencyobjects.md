---
title: Zabezpečené vzory konstruktoru pro DependencyObjects
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: ba8b0a48b2b75a9191553392d5ec0a1f66575807
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086725"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a>Zabezpečené vzory konstruktoru pro DependencyObjects
Obecně platí konstruktor třídy neměli volat zpětná volání, jako je například virtuální metody nebo delegátů, protože konstruktory lze volat jako základní inicializace konstruktory odvozené třídy. Zadání virtuálního může být provedeno stavu neúplná inicializace libovolný daný objekt. Však samotný systém vlastnost volá a zpřístupňuje zpětná volání interně jako součást v systému vlastností závislostí. Jednoduché operace jako nastavení hodnoty vlastnosti závislostí s <xref:System.Windows.DependencyObject.SetValue%2A> volání může potenciálně zahrnout zpětné volání někde v určení. Z tohoto důvodu byste měli být opatrní při nastavení hodnoty vlastností v těle konstruktoru, který může být problematické, pokud se typ používá jako základní třída závislostí. Neexistuje konkrétní vzor pro implementování <xref:System.Windows.DependencyObject> konstruktory, které předchází konkrétní problémy se stavy vlastnost závislostí a přináší zpětná volání, které jsou zde uvedeny.  

<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a>Virtuální metody vlastností systému  
 Následující virtuální metody nebo zpětná volání jsou potenciálně volány během výpočty z <xref:System.Windows.DependencyObject.SetValue%2A> volání, která nastaví hodnotu vlastnosti závislosti: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>. Každá z těchto virtuální metody nebo zpětná volání slouží konkrétní účel rozšíření všestrannost [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systém a závislosti vlastnosti. Další informace o tom, jak pomocí těchto virtuálních funkcí: můžete přizpůsobit stanovení hodnotu vlastnosti, naleznete v tématu [vlastnost závislosti zpětné volání a ověření](dependency-property-callbacks-and-validation.md).  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a>Vynucení pravidel FXCop vs. Vlastnost systému virtuálních funkcí:  
 Pokud používáte nástroj Microsoft FXCop jako součást procesu sestavení a buď odvozovat z některých [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání konstruktoru základní třídy rozhraní framework nebo implementovat vlastní vlastnosti závislosti v odvozených třídách, může dojít konkrétní Porušení pravidla FXCop. Název řetězce pro toto porušení je:  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Toto je pravidlo, které je součástí výchozí sady pro FXCop veřejné pravidel. Co toto pravidlo může být vytváření sestav je trasování prostřednictvím systému vlastnost závislosti, které nakonec volání virtuální metody systému vlastnost závislosti. Porušení tohoto pravidla může nadále zobrazovat i po provedení vzory doporučené konstruktoru popsané v tomto tématu, můžete potřebovat k zakázání nebo potlačení tímto pravidlem ve vaší konfiguraci sady pravidel FXCop.  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a>Většinu problémů pocházejí z odvozená třídy bez použití existujících tříd  
 Problémy hlášené tímto pravidlem dojít, když je třída, která můžete implementovat virtuální metody v jeho pořadí konstrukce pak odvozen z. Pokud zapečeťte třídu, nebo jinak vědět nebo vynutit, nebude vaše třída odvozena od, na základě aspektů je zde vysvětleno a na vás nemusí vztahovat problémy, které opodstatněny pravidlo FXCop. Nicméně pokud autorizujete třídy tak, že jsou určeny pro použití jako základní třídy pro instanci Pokud při vytváření šablony, nebo knihovna rozšíření ovládacích prvků, postupujte podle vzorů zde doporučeného pro konstruktory.  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a>Výchozí konstruktory musí inicializovat všechny hodnoty požadoval zpětná volání  
 U členů instancí, které používají třídy přepsání nebo zpětná volání (zpětná volání ze seznamu v části Vlastnosti systému virtuálních funkcí:) musí být inicializován ve výchozí konstruktor třídy, i když některé z těchto hodnot se sestavil "real" hodnoty prostřednictvím Parametry jiný než výchozí konstruktory.  
  
 Následující příklad kódu (a další příklady) je pseudo -C# příklad poruší toto pravidlo a vysvětluje problému:  
  
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
  
 Když kód aplikace volá `new MyClass(objectvalue)`, volá výchozí konstruktor a základní třídy konstruktory. Potom nastaví `Property1 = object1`, která volá metodu virtuální `OnPropertyChanged` na vlastnící `MyClass` <xref:System.Windows.DependencyObject>.  Přepsání odkazuje na `_myList`, která dosud nebyla inicializována.  
  
 Abyste měli jistotu, že zpětná volání používat jenom jiné vlastnosti závislosti, a že každé takové vlastnost závislosti zavedené výchozí hodnotu jako součást jeho registrované metadata je jedním ze způsobů, abyste se těmto problémům.  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a>Zabezpečené vzory konstruktoru  
 Zamezit neúplná inicializace Pokud vaše třída se používá jako základní třída, postupujte podle těchto vzorců:  
  
#### <a name="default-constructors-calling-base-initialization"></a>Výchozí konstruktory základního inicializace volání  
 Tyto konstruktory volání základní výchozí implementace:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a>Konstruktory jiné než výchozí (pohodlí), neodpovídá žádné základní podpisy  
 Pokud tyto konstruktory pomocí parametrů můžete nastavit vlastnosti závislostí při inicializaci, nejprve zavolat vlastní výchozí konstruktor třídy pro inicializaci a pak pomocí parametrů můžete nastavit vlastnosti závislosti. Toto může buď být definované třídě vlastnosti závislosti nebo závislosti vlastnosti zděděné ze základní třídy, ale v obou případech používají následující vzor:  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a>Jiné než výchozí (pohodlí) konstruktory, které odpovídají základní podpisy  
 Místo volat konstruktor základní třídy pomocí stejné Parametrizace, znovu zavolejte vlastní třídu výchozí konstruktor. Nevolejte základní inicializátor; Místo toho byste měli volat `this()`. Pak pomocí předaných parametrů jako hodnoty pro nastavení vlastnosti důležité opakovat původní chování konstruktoru. Použití původní základní konstruktor dokumentaci pokyny k určení vlastností, které konkrétní parametry jsou určené pro nastavení:  
  
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
 V případech, kdy základní typ má více podpisů musí odpovídat záměrně všechny možné podpisy s implementací konstruktoru vlastní, která používá doporučená vzor volání výchozího konstruktoru třídy před nastavením další vlastnosti.  
  
#### <a name="setting-dependency-properties-with-setvalue"></a>Nastavení vlastností závislostí s SetValue  
 Tyto stejné vzory se dají použít, pokud nastavíte vlastnost, která bez obálku pro vlastnost nastavení pohodlí a nastavte hodnoty s <xref:System.Windows.DependencyObject.SetValue%2A>. Vaše volání <xref:System.Windows.DependencyObject.SetValue%2A> této předávat parametry konstruktoru byste také zavolat třídy výchozí konstruktor pro inicializaci.  
  
## <a name="see-also"></a>Viz také:

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
