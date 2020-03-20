---
title: Priorita hodnot závislých vlastností
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 1d7c644c7f7581a96ffff1a0fe1fcf2adfe071e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186150"
---
# <a name="dependency-property-value-precedence"></a>Priorita hodnot závislých vlastností
<a name="introduction"></a>Toto téma vysvětluje, jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fungování systému vlastností může ovlivnit hodnotu vlastnosti závislosti a popisuje prioritu, podle které aspekty systému vlastností platí pro efektivní hodnotu vlastnosti.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnostem závislostí z pohledu příjemce existujících vlastností závislostí na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídách a že jste si přečetli přehled [vlastností závislostí](dependency-properties-overview.md). Chcete-li postupovat podle příkladů v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tomto tématu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] měli byste také pochopit a vědět, jak psát aplikace.  
  
<a name="intro"></a>
## <a name="the-wpf-property-system"></a>Systém vlastností WPF  
 Systém [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností nabízí účinný způsob, jak mít hodnotu vlastností závislostí být určeny různými faktory, povolení funkce, jako je například ověření vlastností v reálném čase, pozdní vazba a upozorňování související vlastnosti změny hodnot pro jiné vlastnosti. Přesné pořadí a logika, která se používá k určení hodnoty vlastností závislostí je přiměřeně složitý. Znalost tohoto pořadí vám pomůže vyhnout se zbytečnénastavení vlastnosti a může také uklidit nejasnosti nad přesně, proč některé pokusy ovlivnit nebo předvídat hodnotu vlastnosti závislost neskončila výsledkem očekávané hodnoty.  
  
<a name="multiple_sets"></a>
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Vlastnosti závislostí mohou být "Nastaveny" na více místech  
 Následuje příklad, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kde má<xref:System.Windows.Controls.Control.Background%2A>stejná vlastnost ( ) tři různé operace "set", které mohou ovlivnit hodnotu.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Zde, jakou barvu očekáváte, že se použije – červená, zelená nebo modrá?  
  
 S výjimkou animovaných hodnot a nátlaku jsou místní sady vlastností nastaveny na nejvyšší prioritu. Pokud nastavíte hodnotu místně, můžete očekávat, že hodnota bude dodržena, a to i nad všechny styly nebo šablony ovládacích prvků. Zde v příkladu <xref:System.Windows.Controls.Control.Background%2A> je nastavena na red místně. Proto styl definovaný v tomto oboru, i když se jedná o implicitní styl, který by se jinak vztahoval <xref:System.Windows.Controls.Control.Background%2A> na všechny prvky tohoto typu v tomto oboru, není nejvyšší prioritou pro udělení vlastnosti její hodnotu.  Pokud jste odebrali místní hodnotu červená z této instance Button, pak styl by přednost a tlačítko by získat hodnotu pozadí ze stylu.  V rámci stylu mají přednost aktivační události, takže tlačítko bude modré, pokud je nad ním myš, a jinak zelené.  
  
<a name="listing"></a>
## <a name="dependency-property-setting-precedence-list"></a>Seznam priorit nastavení vlastností závislostí  
 Následuje konečné pořadí, které systém vlastností používá při přiřazování hodnot závislosti za běhu. Nejvyšší priorita je uvedena jako první. Tento seznam rozšiřuje některé zobecnění provedené v [přehledvlastnosti závislostí](dependency-properties-overview.md).  
  
1. **Nátlak na systém nemovitostí.** Podrobnosti o nátlaku naleznete v [tématu Nátlak, animace a Základní hodnota](#animations) dále v tomto tématu.  
  
2. **Aktivní animace nebo animace s chováním podržení.** Chcete-li mít jakýkoli praktický účinek, animace vlastnosti musí mít přednost před základní (neanimovaná) hodnota, i v případě, že tato hodnota byla nastavena místně. Podrobnosti naleznete v tématu [Nátlak, animace a Základní hodnota](#animations) dále v tomto tématu.  
  
3. **Místní hodnota.** Místní hodnota může být nastavena prostřednictvím pohodlí "obálky" vlastnost, která se také [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]rovná nastavení jako atribut <xref:System.Windows.DependencyObject.SetValue%2A> nebo prvek vlastnosti v aplikaci nebo volání rozhraní API pomocí vlastnosti konkrétní instance. Pokud nastavíte místní hodnotu pomocí vazby nebo prostředku, tyto každý akt v prioritě, jako by byla nastavena přímá hodnota.  
  
4. **Vlastnosti šablony TemplatedParent.** Prvek má, <xref:System.Windows.FrameworkElement.TemplatedParent%2A> pokud byl vytvořen jako součást <xref:System.Windows.Controls.ControlTemplate> šablony <xref:System.Windows.DataTemplate>(a nebo ). Podrobnosti o tom, kdy to platí, naleznete v tématu [TemplatedParent](#templatedparent) dále v tomto tématu. V šabloně platí následující priorita:  
  
    1. Aktivační události <xref:System.Windows.FrameworkElement.TemplatedParent%2A> ze šablony.  
  
    2. Sady vlastností (obvykle prostřednictvím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.FrameworkElement.TemplatedParent%2A> atributů) v šabloně.  
  
5. **Implicitní styl.** Platí pouze pro `Style` nemovitost. Vlastnost `Style` je vyplněna libovolným zdrojem stylu s klíčem, který odpovídá typu tohoto prvku. Tento prostředek stylu musí existovat buď na stránce nebo v aplikaci; vyhledávání pro zdroj implicitní styl nepokračuje do motivů.  
  
6. **Spouští styl.** Aktivační události v rámci stylů ze stránky nebo aplikace (tyto styly mohou být explicitní nebo implicitní styly, ale ne z výchozích stylů, které mají nižší prioritu).  
  
7. **Šablona se aktivuje.** Libovolný aktivační událost ze šablony ve stylu nebo přímo aplikované šablony.  
  
8. **Nastavení stylu.** Hodnoty z <xref:System.Windows.Setter> uvnitř stylů ze stránky nebo aplikace.  
  
9. **Výchozí (motiv) styl.** Podrobnosti o tom, kdy to platí a jak styly motivů souvisejí se šablonami ve stylech motivů, najdete v tématu [Výchozí styly (Motiv)](#themestyles) dále v tomto tématu. Ve výchozím stylu platí následující pořadí priorit:  
  
    1. Aktivní aktivační události ve stylu motivu.  
  
    2. Setters ve stylu motivu.  
  
10. **Dědičnosti.** Několik vlastností závislostí dědí jejich hodnoty z nadřazeného prvku na podřízené prvky, tak, aby nemusí být nastaveny konkrétně na každý prvek v celé aplikaci. Podrobnosti naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).  
  
11. **Výchozí hodnota z metadat vlastnosti závislosti.** Jakákoli daná vlastnost závislosti může mít výchozí hodnotu stanovenou registrací systému vlastností této konkrétní vlastnosti. Také odvozené třídy, které dědí vlastnost závislosti mají možnost přepsat tato metadata (včetně výchozí hodnoty) na základě typu. Další informace naleznete [v tématu Metadata vlastností závislostí.](dependency-property-metadata.md) Vzhledem k tomu, že dědičnost je kontrolována před výchozí hodnotou, má výchozí hodnota nadřazeného prvku přednost před podřízeným prvkem.  V důsledku toho pokud dědičná vlastnost není nikde nastavena, použije se místo výchozí hodnoty podřízeného prvku výchozí hodnota výchozí hodnota výchozí hodnota podřízeného prvku.  
  
<a name="templatedparent"></a>
## <a name="templatedparent"></a>ŠablonaRodič  
 TemplatedParent jako položka priority se nevztahuje na žádnou vlastnost prvku, který deklarujete přímo ve standardních značkách aplikace. Koncept TemplatedParent existuje pouze pro podřízené položky ve vizuálním stromu, které vzniknou prostřednictvím aplikace šablony. Když systém vlastností <xref:System.Windows.FrameworkElement.TemplatedParent%2A> hledá hodnotu v šabloně, prohledává šablonu, která tento prvek vytvořila. Hodnoty vlastností <xref:System.Windows.FrameworkElement.TemplatedParent%2A> ze šablony obecně fungují, jako by byly nastaveny jako místní hodnota na podřízený prvek, ale tato menší priorita versus místní hodnota existuje, protože šablony jsou potenciálně sdíleny. Podrobnosti najdete v tématu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>
## <a name="the-style-property"></a>Vlastnost Style  
 Pořadí vyhledávání popsané výše platí pro všechny možné vlastnosti závislostí s výjimkou jedné: <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> je jedinečná v tom, že nemůže být sama stylizována, takže položky priority 5 až 8 se nevztahují. Také animaci nebo vynucení <xref:System.Windows.FrameworkElement.Style%2A> se nedoporučuje (a animaci <xref:System.Windows.FrameworkElement.Style%2A> by vyžadovalo vlastní animaci třídy). To ponechává tři <xref:System.Windows.FrameworkElement.Style%2A> způsoby, které vlastnost může být nastavena:  
  
- **Explicitní styl.** Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> je nastavena přímo. Ve většině scénářů styl není definován a obsahuje, ale místo toho je odkazován jako prostředek explicitním klíčem. V tomto případě Style vlastnost sama o sobě funguje, jako by to byla místní hodnota, priorita položka 3.  
  
- **Implicitní styl.** Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> není nastavena přímo. Existuje však na určité úrovni v pořadí vyhledávání prostředků (stránka, aplikace) a je zadán pomocí klíče prostředku, <xref:System.Windows.FrameworkElement.Style%2A> který odpovídá typu, na který má být styl použit. V tomto případě <xref:System.Windows.FrameworkElement.Style%2A> vlastnost sama o sobě pracuje s prioritou označenou v pořadí jako položka 5. Tato podmínka může být <xref:System.Windows.DependencyPropertyHelper> zjištěna pomocí proti <xref:System.Windows.FrameworkElement.Style%2A> vlastnost a hledá <xref:System.Windows.BaseValueSource.ImplicitStyleReference> ve výsledcích.  
  
- **Výchozí styl**, označované také jako **styl motivu.** Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> není nastavena přímo a ve `null` skutečnosti bude číst jako až do běhu. V tomto případě styl pochází z hodnocení motivu run-time, který je součástí prezentačního [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modulu.  
  
 Pro implicitní styly, které nejsou v `MyButton` `Button`tématech, musí typ přesně odpovídat - odvozená třída nebude implicitně používat styl pro `Button`.  
  
<a name="themestyles"></a>
## <a name="default-theme-styles"></a>Výchozí (motiv) styly  
 Každý ovládací prvek, se kterým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je dodáván, má výchozí styl. Tento výchozí styl se potenciálně liší podle motivu, a proto se tento výchozí styl někdy označuje jako styl motivu.  
  
 Nejdůležitější informace, které se nacházejí ve výchozím stylu pro ovládací prvek je jeho šablona ovládacího <xref:System.Windows.Controls.Control.Template%2A> prvku, který existuje ve stylu motivu jako setter pro jeho vlastnost. Pokud by neexistovala žádná šablona z výchozích stylů, ovládací prvek bez vlastní šablony jako součást vlastního stylu by neměl žádný vizuální vzhled. Šablona z výchozího stylu poskytuje vizuální vzhled každého ovládacího prvku základní strukturu a také definuje připojení mezi vlastnostmi definovanými ve vizuálním stromu šablony a odpovídající třídy ovládacího prvku. Každý ovládací prvek zpřístupňuje sadu vlastností, které mohou ovlivnit vizuální vzhled ovládacího prvku bez úplného nahrazení šablony. Zvažte například výchozí vizuální <xref:System.Windows.Controls.Primitives.Thumb> vzhled ovládacího prvku, <xref:System.Windows.Controls.Primitives.ScrollBar>který je součástí ovládacího prvku .  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> má určité přizpůsobitelné vlastnosti. Výchozí šablona <xref:System.Windows.Controls.Primitives.Thumb> vytvoří základní strukturu / vizuální strom <xref:System.Windows.Controls.Border> s několika vnořenými součástmi pro vytvoření zúženého vzhledu. Pokud vlastnost, která je součástí šablony je určena k <xref:System.Windows.Controls.Primitives.Thumb> vystavení pro vlastní nastavení třídy, pak tato vlastnost musí být vystaveny [TemplateBinding](templatebinding-markup-extension.md), v rámci šablony. V případě <xref:System.Windows.Controls.Primitives.Thumb>, různé vlastnosti těchto ohraničení sdílet <xref:System.Windows.Controls.Border.Background%2A> vazbu šablony na vlastnosti, jako je například nebo <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ale některé další vlastnosti nebo vizuální uspořádání jsou pevně zakódovány do šablony ovládacího prvku nebo jsou vázány na hodnoty, které pocházejí přímo z motivu a nelze je změnit, pokud nenahradíte celou šablonu. Obecně platí, že pokud vlastnost pochází z šablony nadřazené a není vystavena vazbou šablony, nelze ji upravit styly, protože neexistuje žádný snadný způsob, jak na ni cílit. Ale tato vlastnost může být stále ovlivněna dědičností hodnoty vlastnosti v použité šabloně nebo ve výchozím hodnotě.  
  
 Styly motivů používají jako klíč ve svých definicích text. Pokud jsou však motivy použity na danou instanci prvku, <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> vyhledávání motivů pro tento typ se provádí kontrolou vlastnosti ovládacího prvku. To je na rozdíl od použití literálu Type, jako implicitní styly. Hodnota <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> by dědí odvozené třídy i v případě, že implementátor nezměnil (zamýšlený způsob změny vlastnosti není přepsat na úrovni vlastnosti, ale místo toho změnit jeho výchozí hodnotu v metadatech vlastnosti). Toto přesměrování umožňuje základní třídy definovat styly motivu pro odvozené prvky, které jinak nemají styl (nebo co je důležitější, nemají šablonu v rámci tohoto stylu a proto by mít žádný výchozí vizuální vzhled vůbec). Proto můžete odvodit `MyButton` z <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Button> a bude stále získat výchozí šablonu. Pokud jste byli autorem `MyButton` ovládacího prvku a chtěli jste jiné chování, můžete <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> `MyButton` přepsat metadata vlastnosti závislostí, aby se vrátil `MyButton` jiný klíč, `MyButton` a pak definovat příslušné styly motivu včetně šablony, pro kterou je nutné zabalit s ovládacím prvkem. Další podrobnosti o tématech, stylech a vytváření ovládacích prvků naleznete v [tématu Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>
## <a name="dynamic-resource-references-and-binding"></a>Dynamické odkazy na prostředky a vazba  
 Dynamické odkazy na prostředky a operace vazby respektují prioritu umístění, ve kterém jsou nastaveny. Například dynamický prostředek použitý na místní hodnotu funguje na prioritu položku 3, vazba pro nastavení vlastností v rámci stylu motivu platí pro položku priority 9 a tak dále. Vzhledem k tomu, že dynamické odkazy na prostředky a vazba musí být schopny získat hodnoty ze stavu běhu aplikace, znamená to, že skutečný proces určování priority hodnoty vlastnosti pro danou vlastnost se rozšíří také do doby běhu.  
  
 Dynamické odkazy na prostředky nejsou přísně řečeno součástí systému vlastností, ale mají vlastní pořadí vyhledávání, které interaguje s výše uvedenou sekvencí. Tato priorita je podrobněji zdokumentována v [xaml prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md). Základní shrnutí této priority je: element to page root, aplikace, téma, systém.  
  
 Dynamické prostředky a vazby mají přednost, kde byly nastaveny, ale hodnota je odložena. Jedním z důsledků je, že pokud nastavíte dynamický prostředek nebo vazbu na místní hodnotu, jakákoli změna místní hodnoty nahradí dynamický prostředek nebo vazbu zcela. I v případě, že voláte metodu <xref:System.Windows.DependencyObject.ClearValue%2A> vymazat místně nastavenou hodnotu, dynamický prostředek nebo vazba nebude obnovena. Ve skutečnosti pokud <xref:System.Windows.DependencyObject.ClearValue%2A> zavoláte na vlastnost, která má dynamický prostředek nebo vazbu na místě (bez literálu místní hodnoty), jsou vymazány <xref:System.Windows.DependencyObject.ClearValue%2A> volání příliš.  
  
<a name="setcurrentvalue"></a>
## <a name="setcurrentvalue"></a>Hodnota SetCurrentValue  
 Metoda <xref:System.Windows.DependencyObject.SetCurrentValue%2A> je jiný způsob, jak nastavit vlastnost, ale není v pořadí priority. Místo <xref:System.Windows.DependencyObject.SetCurrentValue%2A> toho umožňuje změnit hodnotu vlastnosti bez přepsání zdroje předchozí hodnoty. Můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> kdykoli chcete nastavit hodnotu bez udělení této hodnoty přednost místní hodnoty. Například pokud vlastnost je nastavena aktivační událost a <xref:System.Windows.DependencyObject.SetCurrentValue%2A>pak přiřazena jinou hodnotu přes , systém vlastností stále respektuje aktivační událost a vlastnost se změní, pokud dojde k akci aktivační události. <xref:System.Windows.DependencyObject.SetCurrentValue%2A>umožňuje změnit hodnotu vlastnosti bez udělení zdroje s vyšší prioritou. Podobně můžete změnit <xref:System.Windows.DependencyObject.SetCurrentValue%2A> hodnotu vlastnosti bez přepsání vazby.  
  
<a name="animations"></a>
## <a name="coercion-animations-and-base-value"></a>Nátlak, animace a základní hodnota  
 Nátlak a animace fungují na hodnotu, která je označována jako "základní hodnota" v celé této sdk. Základní hodnota je tedy jakákoli hodnota, která je určena vyhodnocením směrem nahoru v položkách, dokud není dosaženo bodu 2.  
  
 Pro animaci může mít základní hodnota vliv na animovanou hodnotu, pokud tato animace neurčuje pro určité chování "Od" a "To", nebo pokud se animace po dokončení záměrně vrátí k základní hodnotě. Chcete-li to zobrazit v praxi, spusťte [ukázku cílových hodnot From, To a By Animation](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues). Zkuste nastavit místní hodnoty výšky obdélníku v příkladu tak, aby počáteční místní hodnota se liší od všech "Od" v animaci. Všimněte si, že animace začít hned pomocí "Od" hodnoty a nahradit základní hodnotu po spuštění. Animace může určit, aby se vrátil k hodnotě nalezené před <xref:System.Windows.Media.Animation.FillBehavior>animace po dokončení zadáním Stop . Poté se pro stanovení základní hodnoty použije normální priorita.  
  
 Více animací může být použita na jednu vlastnost, přičemž každá z těchto animací může být definována z různých bodů v prioritě hodnoty. Tyto animace však bude potenciálně složené jejich hodnoty, nikoli pouze použití animace z vyšší priority. To závisí na přesně jak jsou definovány animace a typ hodnoty, která je animována. Další informace o animaci vlastností naleznete v [tématu Přehled animací](../graphics-multimedia/animation-overview.md).  
  
 Nátlak platí na nejvyšší úrovni ze všech. Dokonce i již spuštěná animace podléhá nátlaku hodnoty. Některé existující vlastnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] závislostí v aplikaci mají předdefinovaný nátlak. Pro vlastní závislost vlastnost, definujete chování nátlaku pro vlastní závislost vlastnost <xref:System.Windows.CoerceValueCallback> zápisem a předáním zpětnévolání jako součást metadat při vytváření vlastnosti. Můžete také přepsat chování nátlaku existujících vlastností přepsáním metadat na této vlastnosti v odvozené třídě. Nátlak interaguje se základní hodnotou tak, aby byla použita omezení nátlaku, protože tato omezení existují v době, ale základní hodnota je stále zachována. Proto pokud omezení v nátlaku jsou později zrušena, příkaz vrátí nejbližší možnou hodnotu této základní hodnotě a potenciálně vliv nátlaku na vlastnost přestane, jakmile jsou zrušena všechna omezení. Další informace o chování nátlaku naleznete v [tématu Zpětná volání vlastností závislostí a ověření](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>
## <a name="trigger-behaviors"></a>Chování aktivační ch spouště  
 Ovládací prvky často definují chování aktivačních událostí jako součást jejich výchozího stylu v motivech. Nastavení místních vlastností ovládacích prvků může zabránit aktivační události z moci reagovat na události řízené uživatelem buď vizuálně nebo behaviorálně. Nejběžnější použití aktivační události vlastnosti je pro řízení <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>nebo vlastnosti stavu, jako je například . Například ve výchozím <xref:System.Windows.Controls.Button> nastavení, když <xref:System.Windows.UIElement.IsEnabled%2A> je `false`zakázána <xref:System.Windows.Controls.Control.Foreground%2A> (aktivační událost pro je), pak hodnota ve stylu motivu je to, co způsobí, že ovládací prvek se zobrazí "šedě". Ale pokud jste nastavili místní <xref:System.Windows.Controls.Control.Foreground%2A> hodnotu, že normální šedá barva bude přepsána předností místní sady vlastností, a to i v tomto scénáři aktivované vlastnosti. Buďte opatrní při nastavování hodnot pro vlastnosti, které mají chování aktivační události na úrovni motivu a ujistěte se, že nejste nepřiměřeně zasahovat do zamýšlenéuživatelské prostředí pro tento ovládací prvek.  
  
<a name="clearvalue"></a>
## <a name="clearvalue-and-value-precedence"></a>Vymazat hodnotu a prioritu hodnoty  
 Metoda <xref:System.Windows.DependencyObject.ClearValue%2A> poskytuje účelné prostředky k vymazání jakékoli místně použité hodnoty z vlastnosti závislosti, která je nastavena na prvek. Volání <xref:System.Windows.DependencyObject.ClearValue%2A> však není zárukou, že výchozí nastavení v metadatech během registrace vlastnosti je nová efektivní hodnota. Všichni ostatní účastníci v prioritě hodnoty jsou stále aktivní. Z pořadí priorit byla odebrána pouze místně nastavená hodnota. Například pokud zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> na vlastnost, kde je tato vlastnost také nastavena stylem motivu, pak se hodnota motivu použije jako nová hodnota, nikoli výchozí hodnota založená na metadatech. Pokud chcete, aby všechny účastníky hodnoty vlastnosti z procesu a nastavit hodnotu na výchozí registrované metadata, můžete získat tuto výchozí hodnotu definitivně dotazem na metadata <xref:System.Windows.DependencyObject.SetValue%2A>vlastnosti závislosta a pak můžete použít výchozí hodnotu místně nastavit vlastnost s voláním .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Zpětné volání a ověření vlastností závislostí](dependency-property-callbacks-and-validation.md)
