---
title: Priorita hodnot závislých vlastností
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 25dfe63a65c3044837beb26ec6c4eaa772c1df1b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180726"
---
# <a name="dependency-property-value-precedence"></a>Priorita hodnot závislých vlastností
<a name="introduction"></a> Toto téma vysvětluje, jak fungování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systému může mít vliv na hodnotu vlastnosti závislosti a popisuje prioritu, ve které aspekty vlastnost systému použít na platnou hodnotu vlastnosti.  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnosti závislosti z pohledu příjemce vlastnosti existujícího závislosti na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy a přečetl [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Následují příklady v tomto tématu, měli byste taky seznámit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>V systému vlastností WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vlastnost systému nabízí efektivní způsob, jak mají hodnotu vlastnosti závislosti měli určit podle různých faktorech, povolení funkce, jako je ověření vlastností v reálném čase, pozdní vazby a upozornění souvisejících vlastností změny hodnot pro další vlastnosti. Přesné pořadí a logiku, která se používá k určení hodnot vlastností závislosti je poměrně složitý. Znalost, toto pořadí se snáze vyhnete zbytečným vlastnost nastavení a může také vymazat záměně přes přesně proč některé pokusí ovlivnit nebo předvídat hodnotu vlastnosti závislostí neukončil nahoru výsledkem je hodnota, kterou jste očekávali.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Vlastnosti závislostí může být "Set" na více místech  
 Tady je příklad [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kde stejnou vlastnost (<xref:System.Windows.Controls.Control.Background%2A>) má tři různé "set" operace, které by mohly ovlivnit hodnota.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Tady, kterou barvu se očekává, že budou platit – červená, zelená nebo blue?  
  
 S výjimkou animovaný hodnoty a vynucení nastaví místní vlastnost nastavíte na nejvyšší prioritu. Pokud nastavíte hodnotu místně můžete očekávat, že hodnota bude použito, dokonce i nad všechny styly a šablony ovládacích prvků. Tady v příkladu <xref:System.Windows.Controls.Control.Background%2A> je nastavena na hodnotu Red místně. Proto styl definované v tomto oboru, i když je implicitní styl, který by jinak platí pro všechny elementy tohoto typu v tomto oboru není nejvyšší prioritu pro poskytování <xref:System.Windows.Controls.Control.Background%2A> vlastnost jeho hodnotu.  Pokud jste odebrali místní hodnota červené z této instance typu Button, styl by pak mají přednost před a na tlačítko získat hodnoty na pozadí z stylu.  Ve stylu aktivační události přednost, takže toto tlačítko bude modrá, pokud ukazatel myši je nad ním a zelená jinak.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Seznam přednost nastavení vlastností závislosti  
 Níže je úplným a rozhodujícím pořadí, ve kterém systém vlastnost používá při přidělování za běhu hodnot vlastností závislosti. Nejvyšší priorita je uvedená jako první. Tento seznam rozšíří na některém z generalizace provedených [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
1.  **Vlastnost systému vynucení.** Podrobnosti o vynucení, najdete v části [vynucení, animace a základní hodnotu](#animations) dále v tomto tématu.  
  
2.  **Aktivní animace, nebo animací pomocí chování blokování.** Pokud chcete mít žádný efekt praktické, musí být animace vlastnosti moct mají přednost před základní hodnoty (unanimated) i v případě, že tato hodnota byla nastavena místně. Podrobnosti najdete v tématu [vynucení, animace a základní hodnotu](#animations) dále v tomto tématu.  
  
3.  **Místní hodnota.** Místní hodnota může být nastaveno prostřednictvím pohodlí vlastnost "zabezpečenou obálku", což také odpovídá nastavení jako atribut nebo vlastnost element v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nebo voláním <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] pomocí vlastnosti konkrétní instance. Pokud nastavíte hodnotu místní pomocí vazby nebo prostředek, tyto každý působit v prioritu jako kdyby byla nastavena hodnotu s přímým přístupem.  
  
4.  **Vlastnosti šablony TemplatedParent.** Element má <xref:System.Windows.FrameworkElement.TemplatedParent%2A> Pokud byl vytvořen jako součást šablony ( <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.DataTemplate>). Podrobnosti o tom, kdy se to používá, najdete v části [TemplatedParent](#templatedparent) dále v tomto tématu. V rámci šablony platí následující priority:  
  
    1.  Aktivační události od <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony.  
  
    2.  Sady vlastností (obvykle až [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy) v <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony.  
  
5.  **Implicitní styl.** Platí jenom pro `Style` vlastnost. `Style` Vlastnost sestavil prostředek stylu s klíčem, který odpovídá typu daného prvku. Tento prostředek stylu musí existovat ve stránce nebo aplikaci. vyhledávání pro prostředek implicitní styl nebude pokračovat do motivy.  
  
6.  **Styl aktivační události.** Aktivační události ve stylech ze stránky nebo aplikace (tyto styly může být explicitní nebo implicitní styly, ale ne z výchozích stylů, které mají nižší prioritou).  
  
7.  **Aktivuje se šablony.** Žádné aktivační události ze šablony ve stylu nebo šablony použité přímo.  
  
8.  **Style setter.** Z hodnoty <xref:System.Windows.Setter> ve stylech ze stránky nebo aplikace.  
  
9. **Styl výchozí (motiv).** Podrobnosti o při takovém se vztah styly motivů a šablon v rámci stylů motivů, naleznete v tématu [výchozí (motiv) styly](#themestyles) dále v tomto tématu. Ve výchozím stylu platí následující pořadí priorit:  
  
    1.  Aktivní triggery ve stylu motivu.  
  
    2.  Metody setter ve stylu motivu.  
  
10. **Dědičnost.** Několik vlastností závislostí jejich hodnoty dědí z nadřazeného elementu pro podřízené prvky tak, že není nutné nastavovat zvlášť na každý prvek v celé aplikaci. Podrobnosti najdete v tématu [dědičnost hodnoty vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
11. **Výchozí hodnota z metadata vlastností závislosti** Žádné danou vlastnost závislosti může mít výchozí hodnotu, podle registrace systému vlastnosti této konkrétní vlastnosti. Odvozené třídy, které dědí vlastnosti závislosti také mít možnost přepsat tato metadata (včetně výchozí hodnota) na základě-type. Zobrazit [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) Další informace. Vzhledem k tomu, že dědičnost je zaškrtnuté políčko než výchozí hodnotu pro zděděnou vlastnost, výchozí hodnotu nadřazený prvek má přednost před podřízený element.  V důsledku toho pokud dědičnou vlastnost není nastavená kdekoli, je použita výchozí hodnota je definován na kořenový server WSUS nebo nadřazené místo výchozí hodnota podřízeného elementu.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako položka Priorita se nevztahují žádné vlastnosti elementu, který deklarujete přímo ve značce standardní aplikace. Koncept TemplatedParent existuje pouze pro podřízené položky ve vizuálním stromu přicházející do existence prostřednictvím aplikace šablony. Pokud vlastnost systém vyhledá soubor <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony pro hodnoty, to je hledání šablonu, kterou vytvořili tento prvek. Vlastnost hodnoty z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony obecně fungovat jako, pokud byly nastaveny jako místní hodnota na podřízený element, ale tento nižší prioritu oproti hodnotě místní existuje, protože tyto šablony jsou potenciálně sdílené. Podrobnosti najdete v tématu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Vlastnost stylu  
 Pořadí vyhledávání bylo popsáno dříve se vztahuje na všechny vlastnosti možné závislosti, s výjimkou jednoho: <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost je jedinečný, v tom, že se nemůže sám být ve stylu, takže prioritu položek 5 až 8 se nedá použít. Navíc animace nebo podřízenému <xref:System.Windows.FrameworkElement.Style%2A> se nedoporučuje (a animaci <xref:System.Windows.FrameworkElement.Style%2A> by vyžadovaly vlastní animace třídy). Kvůli tomu tři způsoby, které <xref:System.Windows.FrameworkElement.Style%2A> může být nastavena vlastnost:  
  
-   **Explicitní styl.** <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost nastavena přímo. Ve většině scénářů si styl není definována vložením, ale místo toho se odkazuje jako prostředek, explicitní klíčem. V tomto případě samotné vlastnosti stylu se chová jako kdyby byly místní hodnota priority položky 3.  
  
-   **Implicitní styl.** <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost není nastavena přímo. Ale <xref:System.Windows.FrameworkElement.Style%2A> existuje na určité úrovni v pořadí vyhledávání prostředků (stránka, aplikace) a je nastaven pomocí klíče prostředku, který odpovídá typu styl se použije k. V takovém případě <xref:System.Windows.FrameworkElement.Style%2A> samotné vlastnosti funguje podle priority podle pořadí jako položka 5. Tento stav můžete zjistit pomocí <xref:System.Windows.DependencyPropertyHelper> proti <xref:System.Windows.FrameworkElement.Style%2A> vlastnost a hledáte <xref:System.Windows.BaseValueSource.ImplicitStyleReference> ve výsledcích.  
  
-   **Výchozí styl**, označované také jako **stylu motivu.** <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost není nastavena přímo a bude ve skutečnosti číst jako `null` až běhu. V tomto případě styl pochází z hodnocení motiv, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentace modul.  
  
 Pro implicitní styly není v motivy, typ musí odpovídat přesně – `MyButton` `Button`-odvozené třídy implicitně nepoužije styl `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Styly výchozí (motiv)  
 Každý ovládací prvek, který se dodává s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má výchozí styl. Výchozí styl potenciálně se bude lišit podle motiv, což je důvod, proč tento výchozí styl se někdy označuje jako stylu motivu.  
  
 Nejdůležitější informace, které se nachází ve výchozím stylu pro ovládací prvek je ovládací prvek šablony, který existuje ve stylu motivu jako setter pro jeho <xref:System.Windows.Controls.Control.Template%2A> vlastnost. Pokud nebyly žádné šablony z výchozí styly, má bez vlastní šablony jako součást vlastní styl ovládacího prvku bez vizuálního vzhledu vůbec. Šablony z výchozího stylu dává vzhled každý ovládací prvek základní strukturu a také definuje připojení mezi vlastnosti definované ve vizuálním stromu šablony a odpovídající třídy ovládacího prvku. Každý ovládací prvek zveřejňuje sadu vlastností, které mohou mít vliv vzhled ovládacího prvku bez úplného nahrazení šablony. Představte si třeba výchozí vzhled <xref:System.Windows.Controls.Primitives.Thumb> ovládací prvek, který je součástí sady <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> některé přizpůsobitelné vlastnosti. Výchozí šablony <xref:System.Windows.Controls.Primitives.Thumb> vytvoří základní struktura / vizuální strom a s několika vnořené <xref:System.Windows.Controls.Border> součásti pro vytvoření vzhledu zkosení. Pokud je vlastnost, která je součástí šablony má být vystaveny pro přizpůsobení pomocí <xref:System.Windows.Controls.Primitives.Thumb> třídy, pak musí být vystavené tuto vlastnost [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), v rámci šablony. V případě třídy <xref:System.Windows.Controls.Primitives.Thumb>, různé vlastnosti těchto ohraničení sdílet šablony vazbu k vlastnosti, jako <xref:System.Windows.Controls.Border.Background%2A> nebo <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ale určité vlastnosti nebo visual režimu pevně zakódovaných v šabloně ovládacího prvku nebo jsou vázány na hodnoty, které pocházejí přímo z motivu a nemá nahrazování celého šablony se nedá změnit. Obecně platí Pokud vlastnost pochází z nadřazené položky bez vizuálního vzhledu a není dostupná šablona vazbou, nelze ho upravit podle styly protože neexistuje žádný snadný způsob, jak ji zaměřit. Ale tato vlastnost může být ovlivněny stále dědičnost hodnoty vlastnosti použité šablony, nebo výchozí hodnotu.  
  
 Styly motivů typu slouží jako klíč v jejich definice. Ale při použití motivů do instance daného elementu, motivy vyhledávání pro tento typ se provádí tak, že zkontrolujete <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> vlastnosti u ovládacího prvku. To se liší od použití literálu typu, stejně jako implicitní styly. Hodnota <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> by k odvozeným třídám dědit i v případě, implementátora nezměnil ho (požadovaný způsob, jak při změně hodnoty vlastnosti je nechcete přepsat na úrovni vlastnost, ale chcete místo toho změnit jeho výchozí hodnotu v metadatech vlastnost). Tuto indirekci umožňuje základních tříd k definování motivu styly odvozené elementy, které nemají jinak styl (nebo více důležité je, není nutné šablonu v rámci tohoto stylu a by tedy mít vůbec žádné výchozí vzhled). Proto lze odvodit `MyButton` z <xref:System.Windows.Controls.Button> a dostanete <xref:System.Windows.Controls.Button> výchozí šablonu. Pokud byste byli ovládacího prvku Autor `MyButton` a chtěli byste různé chování, může přepsat metadata vlastností závislosti pro <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> na `MyButton` vrátí jiný kód, a pak definovat včetně šablony stylů relevantní motiv pro `MyButton` , musíte sestavit balíček s vaší `MyButton` ovládacího prvku. Další podrobnosti o motivy, styly a vytváření ovládacího prvku, naleznete v tématu [Přehled vytváření ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dynamický prostředek odkazy a vazby  
 Dynamický prostředek odkazy a operace vazby dodržovat prioritu umístění, ve kterém jsou nastavené. Například dynamického prostředku použít na lokální hodnotu funguje na položku prioritou 3, vazby pro vlastnost setter uvnitř stylu motivu se vztahuje na prioritu položky 9 a tak dále. Protože odkazy na dynamické prostředky a vazby musí být schopen získat hodnoty z běhu stav aplikace, to znamená, že v době běhu také rozšiřuje skutečné procesu, který určuje priorita hodnot vlastností pro jakékoli dané vlastnosti.  
  
 Dynamické reference na prostředky přesněji řečeno nejsou součástí systému vlastností, ale mají svoje vlastní, který komunikuje s pořadí uvedené výše pořadí vyhledávání. Tuto prioritu se důkladněji dokumentovány v článku [prostředky XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md). Je základní souhrn tuto prioritu: element kořenového stránka, aplikace, motiv, systému.  
  
 Dynamické prostředky a vazby mají přednost před kde byly sady, ale hodnota je odloženo. Důsledkem tohoto je, že pokud nastavíte dynamický prostředek nebo vazbu na lokální hodnotu, všechny změny na lokální hodnotu nahradí dynamický prostředek nebo zcela vazby. I v případě, že zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> metoda zrušte místně nastavené hodnoty, dynamický prostředek nebo vazby nebude obnoven. Ve skutečnosti, pokud zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> na vlastnost, která má dynamický prostředek nebo vazbu na místě (s žádné místní hodnota literálu), jsou vymazány, tak <xref:System.Windows.DependencyObject.ClearValue%2A> příliš volání.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Metoda je jiný způsob, jak nastavit vlastnosti, ale není v pořadí podle priority. Místo toho <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umožňuje změnit hodnotu vlastnosti, aniž byste museli přepsat zdroj předchozí hodnotu. Můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> pokaždé, když chcete nastavit hodnotu bez ztráty tuto hodnotu priority místní hodnoty. Například, pokud je vlastnost nastavením aktivační události a pak přiřadí jiná hodnota prostřednictvím <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, systém vlastností stále respektuje aktivační událost a vlastnost se změní, pokud dojde k akci triggeru. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Umožňuje změnit hodnotu vlastnosti bez zadání zdroji s vyšší prioritou. Podobně můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> ke změně hodnoty vlastnosti bez vazby přepsání.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Vynucení, animace a základní hodnotu  
 Vynucení a animace, jak reagovat na hodnotu, která je označován jako "základní hodnoty" v rámci tohoto [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Základní hodnota je tedy libovolné hodnota určena pomocí vyhodnocování nahoru v položkách, dokud nebude dosaženo položka 2.  
  
 Pro animaci základní hodnota může mít vliv na hodnotu animovaný Pokud animace neurčuje "Od" a "Do" pro určité chování, nebo pokud animace se záměrně vrátí základní hodnotu po dokončení. Pokud chcete zobrazit toto v praxi, spusťte [od, Komu a kdo ukázkové hodnoty cílové animace](https://go.microsoft.com/fwlink/?LinkID=159988). Nastavte místní hodnoty výšky obdélníku v tomto příkladu tak, aby počáteční místní hodnota se liší od kdokoli "Z" animace. Všimněte si, že animací začít okamžitě používat hodnoty "Od" a nahraďte základní hodnotu po spuštění. Animace může určit se vraťte na hodnotu nalezenou před animace po dokončení se tak, že zadáte zastavení <xref:System.Windows.Media.Animation.FillBehavior>. Později normální priorita se používá k určení základní hodnoty.  
  
 Animací několik může být použit pro jednu vlastnost s jednotlivými tyto animace budete pravděpodobně s definována v různých okamžicích v Priorita hodnot. Však bude potenciálně tyto animace budete složené jejich hodnoty, nikoli pouze implementovány animace z vyšší prioritu. To závisí na přesně jak jsou definované animací a typ hodnoty, který je právě animovaný. Další informace o animace vlastností najdete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Konverze se vztahuje na nejvyšší úrovni všechny. Již běžícímu animace se hodnota vynucení. Určité vlastnosti existujícího závislosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají integrovanou vynucení. Pro vlastnost závislosti vlastní, můžete definovat chování vynucení pro vlastnost vlastní závislosti zápisem <xref:System.Windows.CoerceValueCallback> a při vytváření vlastnost předávání zpětného volání jako součást metadat. Můžete také přepsat chování převod existujících vlastností přepsání metadat pro tuto vlastnost v odvozené třídě. Vynucení komunikuje s základní hodnoty tak, že použijí omezení pro vynucení těchto omezení existují v okamžiku, ale stále se uchovávají základní hodnoty. Proto pokud vynucení omezení jsou vyšší zrušeno, vynucení vrátí nejbližší hodnotu možné tato základní hodnota a potenciálně vynucení vliv na vlastnosti přestane ihned poté, co jsou všechna omezení zrušeno. Další informace o chování vynucení, najdete v části [vlastnost závislosti zpětné volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Chování aktivační událost  
 Ovládací prvky často definují chování aktivační událost jako součást svého výchozího stylu v motivů. Nastavení místní vlastnosti v ovládacích prvcích může zabránit schopnost reagovat na události řízené uživateli vizuálně nebo behaviorally aktivačních událostí. Pro ovládací prvek nebo stav vlastnosti, jako se nejčastěji používá aktivační události vlastnost <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Například ve výchozím nastavení při <xref:System.Windows.Controls.Button> je zakázaný (aktivovat pro <xref:System.Windows.UIElement.IsEnabled%2A> je `false`) pak bude <xref:System.Windows.Controls.Control.Foreground%2A> hodnota stylu motivu je co způsobí, že ovládací prvek se zobrazí "šedě". Ale pokud nastavíte místní <xref:System.Windows.Controls.Control.Foreground%2A> hodnotu, že normální navýšením kapacity šedá barva bude mít přednost prioritu sady vlastnost místně i v tomto scénáři aktivuje vlastnost. Dávejte pozor. nastavení hodnoty vlastností, které mají aktivační procedura motiv chování a ujistěte se, že nebudou neoprávněně zasahovala určené uživatelské prostředí pro tento ovládací prvek.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue a Priorita hodnot  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Metoda poskytuje účelné znamená, že chcete vymazat všechny místně použité hodnoty z vlastnosti závislosti, který je nastaven pro element. Však voláním <xref:System.Windows.DependencyObject.ClearValue%2A> nezaručuje, že je výchozí, jak je stanoveno v metadatech během registrace vlastnost novou platnou hodnotu. Všechny ostatní účastníci Priorita hodnot jsou stále aktivní. Pouze místně nastavené hodnota byla odebrána z pořadí priority. Například, pokud zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> u vlastnosti, kde tato vlastnost nastavena také ve stylu motivu, pak hodnota motiv se použije jako novou hodnotu než výchozí na základě metadat. Pokud chcete využít všichni účastníci hodnotu vlastnosti mimo proces a nastavte hodnotu na výchozí registrované metadata, můžete získat, výchozí hodnota platností pomocí dotazu na metadata vlastností závislosti a pak můžete použít výchozí hodnotu místně Nastavte vlastnost voláním <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Zpětné volání a ověření vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
