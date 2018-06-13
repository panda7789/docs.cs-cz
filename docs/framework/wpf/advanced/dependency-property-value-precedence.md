---
title: Priorita hodnot závislých vlastností
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 7719c39c82b69421477cadf9ae5caf9f9f55b457
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541934"
---
# <a name="dependency-property-value-precedence"></a>Priorita hodnot závislých vlastností
<a name="introduction"></a> Toto téma vysvětluje, jak do chodu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost systému může mít vliv na hodnotu vlastnosti závislosti a popisuje priorit, podle které aspekty vlastnosti systému, na které se týkají platnou hodnotu vlastnosti.  
    
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastností závislostí z perspektivy příjemce existující vlastností závislostí na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy a přečetli [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Následují příklady v tomto tématu, měli byste taky seznámit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak napsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>Vlastnost systému WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vlastnost systému nabízí efektivní způsob, jak mají hodnotu vlastností závislostí určí na základě různých faktorech, povolení funkce, jako je ověření vlastností v reálném čase, pozdní vazby a upozornění souvisejících vlastností změny hodnot pro ostatní vlastnosti. Přesné pořadí a logiku, která se používá k určení hodnoty vlastností závislostí je to bude přiměřeně složitý. Znalost, toto pořadí bude umožňuje vyhnout se zbytečné vlastnost nastavení a může také vymazány nedorozuměním přes přesně proč některé pokusit o ovlivnit nebo předvídat hodnotu vlastnosti závislosti neukončil až výsledkem je hodnota, kterou jste očekávali.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Vlastnosti závislosti mohou být "nastavení" na více místech  
 Tady je příklad [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kde stejnou vlastnost (<xref:System.Windows.Controls.Control.Background%2A>) má tři různé "nastavení" operace, které by mohly ovlivnit hodnotu.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Zde, jakou barvu se očekává, že budou platit – červená, zelená nebo modrá?  
  
 S výjimkou animovaný hodnoty a převod místní nastavuje nastaveny na nejvyšší prioritu. Pokud nastavíte hodnotu místně můžete očekávat, že hodnota bude použito, i výše všechny styly nebo šablon ovládacích prvků. Tady příklad <xref:System.Windows.Controls.Control.Background%2A> je nastaven na červený místně. Proto styl definované v tomto rozsahu, i když je implicitní styl, že by jinak, platí pro všechny elementy daného typu v tomto oboru není nejvyšší prioritu pro poskytnutí <xref:System.Windows.Controls.Control.Background%2A> vlastnost jeho hodnotu.  Pokud jste odebrali místní hodnota Red z této instance tlačítko, styl by pak mají přednost před a tlačítko by získat hodnotu pozadí z styl.  V rámci styl aktivační události přednost, a tak tlačítko blue, pokud je ukazatel myši nad ním a zelená jinak.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Seznam priorit nastavení vlastností závislostí  
 Toto je spolehlivý pořadí, které používá systém vlastnost při přiřazování běhu hodnoty vlastností závislostí. Nejvyšší priorita je uvedená jako první. Tento seznam rozšíří na některém z generalizace provedené v [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
1.  **Vlastnost systému převod.** Podrobnosti na převod najdete v tématu [převod, animace a základní hodnoty](#animations) dál v tomto tématu.  
  
2.  **Aktivní animace nebo animací s chováním uchování.** Chcete-li mít praktické vliv, musí být animace vlastnosti moct mají přednost před (unanimated) hodnotu, i v případě, že tato hodnota byla nastavena místně. Podrobnosti najdete v tématu [převod, animace a základní hodnoty](#animations) dál v tomto tématu.  
  
3.  **Místní hodnota.** Místní hodnota může být nastaveno prostřednictvím pohodlím, které představuje vlastnost "obálky", která také rovná nastavení jako elementu nebo atributu vlastnost v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nebo volání <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] pomocí vlastnosti konkrétní instance. Pokud nastavíte hodnotu místní pomocí vazby nebo prostředek, tyto každý fungují v prioritu jako kdyby byla nastavena přímé hodnotu.  
  
4.  **Vlastnosti šablony TemplatedParent.** Element má <xref:System.Windows.FrameworkElement.TemplatedParent%2A> Pokud byla vytvořena v rámci šablony ( <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.DataTemplate>). Podrobnosti o když platí, najdete v části [TemplatedParent](#templatedparent) dál v tomto tématu. V rámci šablony platí následující prioritu:  
  
    1.  Aktivuje z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony.  
  
    2.  Sady vlastností (obvykle přes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy) v <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony.  
  
5.  **Implicitní styl.** Se týkají pouze `Style` vlastnost. `Style` Vlastnost vyplní jakémukoli prostředku, styl s klíčem, který odpovídá typu používaného daný element. Styl prostředku, musí existovat buď na stránce nebo v aplikaci; vyhledávání pro prostředek implicitní styl do motivy nebude pokračovat.  
  
6.  **Styl aktivační události.** Aktivační události v rámci styly ze stránky nebo aplikace (tyto styly může být explicitní nebo implicitní stylů, ale nikoli z výchozích stylů, které mají nižší prioritu).  
  
7.  **Šablona aktivační události.** Všechny aktivační události z šablony v rámci styl, nebo přímo použité šablony.  
  
8.  **Styl setter.** Hodnoty z <xref:System.Windows.Setter> během styly ze stránky nebo aplikace.  
  
9. **Styl výchozí (motiv).** Podrobnosti o když platí či vztah styly motivů a šablon v rámci styly motivů najdete v tématu [výchozí (motiv) styly](#themestyles) dál v tomto tématu. V rámci výchozí styl platí následující pořadí priority:  
  
    1.  Aktivní aktivační události ve stylu motivu.  
  
    2.  Mechanismy nastavení ve stylu motivu.  
  
10. **Dědičnost.** Několik vlastností závislostí jejich hodnoty dědí z nadřazeného prvku pro podřízené elementy, tak, aby nemusí být nastavení konkrétně na každý prvek v celé aplikaci. Podrobnosti najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
11. **Výchozí hodnota z metadat vlastností závislostí.** Všechny danou vlastnost závislosti může mít výchozí hodnotu podle registrace systému vlastnost této konkrétní vlastnosti. Odvozené třídy, které dědí vlastnost závislosti také mít možnost přepsání, aby metadata (včetně výchozí hodnota) na základě-type. V tématu [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) Další informace. Protože dědičnosti se kontroluje před výchozí hodnota pro o zděděnou vlastnost, výchozí hodnotu nadřazený element má přednost před podřízený element.  V důsledku toho pokud zděditelné vlastnost není nastavena kdekoli, je použita výchozí hodnota uvedeného na kořenový server WSUS nebo nadřazené místo podřízený element výchozí hodnota.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako položka přednost se nevztahuje na žádnou vlastnost element, který je deklarovat přímo v kódu standardní aplikace. Koncept TemplatedParent existuje pouze pro podřízené položky v rámci vizuálním stromu, které začalo existence prostřednictvím aplikace šablony. Pokud vlastnost systém vyhledá soubor <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablonu pro hodnotu ho je vyhledávání šablony, která vytvořila daný element. Vlastnost hodnoty z <xref:System.Windows.FrameworkElement.TemplatedParent%2A> šablony obecně fungovat, jako kdyby byly nastavené jako místní hodnotu na podřízený element, ale tato menší prioritu a místní hodnota existuje, protože šablony potenciálně sdílejí. Podrobnosti najdete v tématu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Vlastnost stylu  
 Pořadí vyhledávání popsané výše se vztahují na všechny vlastnosti možných závislostí kromě jednoho: <xref:System.Windows.FrameworkElement.Style%2A> vlastnost. <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost je jedinečný, v tom, že se nemůže sám sebe být navržen tak, aby položky přednost 5 až 8 se nevztahují. Navíc buď animaci nebo vynucený <xref:System.Windows.FrameworkElement.Style%2A> se nedoporučuje (a animace <xref:System.Windows.FrameworkElement.Style%2A> by vyžadovaly třídu vlastní animace). Zůstane tři způsoby, <xref:System.Windows.FrameworkElement.Style%2A> vlastnost může být nastaveno:  
  
-   **Explicitní styl.** <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost je nastavena přímo. Ve většině scénářů styl není definována vložením, ale místo toho se odkazuje jako prostředek, explicitní klíč. V takovém případě samotné vlastnosti stylu funguje, jako by šlo hodnotu místní přednost položky 3.  
  
-   **Implicitní styl.** <xref:System.Windows.FrameworkElement.Style%2A> Přímo není nastavena vlastnost. Ale <xref:System.Windows.FrameworkElement.Style%2A> existuje na určité úrovni v pořadí vyhledávání prostředků (stránka, aplikace) a je s klíčem využívajícím klíč prostředku, který odpovídá typu styl se použije. V takovém případě <xref:System.Windows.FrameworkElement.Style%2A> samotné vlastnosti funguje podle priorit, v pořadí jako položka 5 identifikovat. Tento stav můžete zjistit pomocí <xref:System.Windows.DependencyPropertyHelper> proti <xref:System.Windows.FrameworkElement.Style%2A> vlastnost a hledá <xref:System.Windows.BaseValueSource.ImplicitStyleReference> ve výsledcích.  
  
-   **Výchozí styl**, také známé jako **styl motivu.** <xref:System.Windows.FrameworkElement.Style%2A> Vlastnost není nastavená přímo a bude ve skutečnosti přečíst jako `null` až po dobu spuštění. V takovém případě styl pochází z vyhodnocení motivu spuštění, který je součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentace modul.  
  
 Pro implicitní styly není v motivy, musí přesně shodovat typ – `MyButton``Button`-odvozené třídy nebude používat implicitně styl `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Výchozí (motiv) styly  
 Každý ovládací prvek, který se dodává s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má výchozí styl. Aby výchozí styl potenciálně se liší podle motiv, který je důvod, proč tuto výchozí styl je někdy označovány jako styl motivu.  
  
 Nejdůležitější informace, která se nachází v rámci výchozí styl pro ovládací prvek, je jeho řízení šablony, která existuje v motivu styl jako setter pro jeho <xref:System.Windows.Controls.Control.Template%2A> vlastnost. Kdyby žádnou šablonu z výchozí styly ovládacího prvku bez vlastní šablonu v rámci vlastní styl by měla mít žádné vzhled vůbec. Šablona z výchozí styl dává vzhled všech ovládacích prvků základní strukturu a také definuje připojení mezi vlastnosti definované ve vizuálním stromu šablona a odpovídající třída ovládacích prvků. Každý ovládací prvek poskytuje sadu vlastností, které mohou mít vliv vzhled ovládacího prvku bez úplného nahrazení šablony. Představte si třeba výchozí vzhled <xref:System.Windows.Controls.Primitives.Thumb> řízení, které je součástí služby <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 A <xref:System.Windows.Controls.Primitives.Thumb> některé přizpůsobitelné vlastnosti. Výchozí šablony služby <xref:System.Windows.Controls.Primitives.Thumb> vytvoří základní strukturu / vnořené vizuálním stromu s několika <xref:System.Windows.Controls.Border> součásti pro vytvoření vzhledu zkosení. Je-li určen vlastnosti, která je součástí šablony mají být exponovány pro přizpůsobení pomocí <xref:System.Windows.Controls.Primitives.Thumb> třídy, pak musí být vystavené tuto vlastnost [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), v rámci šablony. U <xref:System.Windows.Controls.Primitives.Thumb>, různé vlastnosti těchto ohraničení sdílet šablony vazbu na vlastnosti, jako <xref:System.Windows.Controls.Border.Background%2A> nebo <xref:System.Windows.Controls.Border.BorderThickness%2A>. Ale některé vlastnosti nebo visual uspořádání jsou pevně zakódovaná do šablony ovládací prvek nebo je vázána na hodnoty, které pochází přímo z motiv a nedá se změnit souborem nahraďte celou šablony. Obecně platí Pokud vlastnost dodává s nadřazenou položkou použitím šablon a není vystavené vazbu šablony, nelze ho upravit podle styly protože neexistuje žádný snadný způsob, jak na ni cílit. Ale tato vlastnost může mít vliv stále dědičnost vlastnosti hodnotu v šabloně použité, nebo výchozí hodnotu.  
  
 Styly motivů typu slouží jako klíč v jejich definice. Ale pokud motivy jsou použity k instanci daného elementu, motivy vyhledávání pro tento typ provádí kontrolu <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> ovládacího prvku. Jde na rozdíl od použití literálu typu, stejně jako implicitní stylů. Hodnota <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> by dědit do odvozených tříd i v případě, že implementátor nezměnila ho (určený způsob změny vlastnost je nechcete přepsat na úrovni vlastnost, ale chcete místo toho změnit jeho výchozí hodnotu metadata vlastnosti). Tato indirection umožňuje základní třídy k definování motivu styly pro odvozené prvky, které jinak nemají styl (nebo více je nejdůležitější, nemají šablonu v rámci této styl a by proto mít vůbec žádné výchozí vzhled). Proto můžete odvodit `MyButton` z <xref:System.Windows.Controls.Button> a stále dostávat <xref:System.Windows.Controls.Button> výchozí šablony. Pokud byste byli ovládacího prvku Autor `MyButton` a chtěli byste různé chování, může přepsat metadata vlastnosti závislosti pro <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> na `MyButton` vrátit jiný klíč, a pak definovat styly relevantní motivů, včetně šablony pro `MyButton` , musíte sestavit balíček s vaší `MyButton` ovládacího prvku. Další informace o motivy, styly a vytváření ovládacího prvku v [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dynamické prostředků odkazů a vazby  
 Operace vazby a odkazy na dynamické prostředků respektují prioritu umístění, ve kterém jsou nastavené. Například dynamického prostředku projeví na hodnotě místní funguje na každou položku přednost před 3, vazby pro vlastnost setter v rámci styl motiv se vztahuje na položku přednost před 9 a tak dále. Protože dynamické prostředků odkazy i vazby musí být schopný získat hodnoty z stav běhu aplikace, to má za následek, že samotný proces určování priorit hodnotu vlastností pro danou vlastnost zasahuje do také čas spuštění.  
  
 Dynamické odkazy prostředků nejsou přesněji řečeno součást vlastností systému, ale mají své vlastní, který komunikuje s pořadím uvedené výše pořadí vyhledávání. Tuto prioritu je více důkladně dokumentovány v článku [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md). Je základní sumarizační tohoto pořadí: element kořenové stránky, aplikace, motiv, systému.  
  
 Dynamické prostředky a vazby mít prioritu, které byly nastavené, ale hodnota je odložen. Důsledkem tohoto objektu je, že pokud nastavíte dynamického prostředku nebo vytvoření vazby na hodnotu místní, všechny změny do místní hodnota nahradí dynamické prostředku nebo zcela vazby. I v případě, že zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> metoda zrušte místně nastavte hodnotu, dynamické prostředku nebo vazba nebude obnoven. V faktu, když zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> na vlastnost, která má dynamické prostředek nebo vazbu na místě (s literálovou hodnotou žádné místní), jsou vymazány podle <xref:System.Windows.DependencyObject.ClearValue%2A> příliš volání.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Metoda je jiný způsob, jak nastavit vlastnost, ale není v pořadí podle priority. Místo toho <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umožňuje změnit hodnotu vlastnosti bez přepsal zdroj předchozí hodnotu. Můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> vždy, když chcete nastavit hodnotu bez nutnosti poskytnutí tuto hodnotu přednost před místním hodnoty. Například, pokud vlastnost nastavení triggerem a pak přiřadit jinou hodnotu prostřednictvím <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, vlastnost systému stále respektuje aktivační události a vlastnost se změní, pokud dojde k akci aktivační události. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> Umožňuje změnit hodnotu vlastnosti bez nutnosti poskytnutí zdroj s vyšší prioritou. Podobně můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> ke změně hodnoty vlastnosti bez přepsal vazbu.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Převod, animace a základní hodnoty  
 Převod a animace obě fungovat na hodnotu, která je označovaných jako "základní hodnota" v celém to [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Základní hodnota je proto ať hodnota je určena prostřednictvím vyhodnocení směrem nahoru v položkách, dokud nebude dosaženo položka 2.  
  
 Pro animace základní value může mít vliv na animovaný hodnotu, pokud tento animace neurčuje "Od" a "Na" pro určité chování, nebo pokud animace úmyslně vrátí základní hodnotu po dokončení. Chcete-li zobrazit to v praxi, spusťte [z, k a ukázkové hodnoty Target animace](http://go.microsoft.com/fwlink/?LinkID=159988). Zkuste nastavit místní hodnoty výšky obdélníku v příkladu, tak, že počáteční místní hodnota se liší od všech "Od" v animace. Všimněte si, že animací začít hned používat hodnoty "Od" a nahraďte hodnotu jednou spustit. Animace může zadat vrátit hodnotu před animace nalezeny po dokončení se zadáním zastavení <xref:System.Windows.Media.Animation.FillBehavior>. Později normální priorita slouží k určení základní hodnota.  
  
 Více animací může použít jedinou vlastností, s každou z těchto animací pravděpodobně s byla definována z různých okamžicích v prioritu hodnotu. Ale tyto animace bude potenciálně složené jejich hodnoty, nikoli jen použití animace z vyšší prioritu. To závisí na přesně jak jsou definovány animace a typ hodnoty, který je právě animovaný. Další informace o animaci vlastnosti najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Převod se vztahuje na nejvyšší úrovni všechny. I již běžící animace podléhá převod hodnotu. Některé vlastnosti existující závislostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít integrovanou převod. Pro vlastnost vlastní závislosti, kterou definujte chování převod pro vlastnost vlastní závislosti zápis <xref:System.Windows.CoerceValueCallback> a předání zpětné volání v rámci metadat, když vytvoříte vlastnost. Můžete také přepsat chování převod stávajících vlastností přepsáním metadata pro tuto vlastnost v odvozené třídě. Převod komunikuje s hodnotu tak, že použijí omezení na převod jako těchto omezení existují v době, ale stále se uchovávají základní hodnota. Proto pokud omezení v převod jsou novější ukončeno nebo převod vrátí na nejbližší hodnotu možné tato základní hodnota a potenciálně převod vliv na vlastnost přestanou také všechna omezení jsou odvolány. Další informace o převod chování najdete v tématu [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Aktivační událost chování  
 Ovládací prvky často definují chování aktivační události v rámci jejich výchozí styl v motivů. Nastavení místního vlastnosti v ovládacích prvcích na může zabránit schopnost reagovat na základě uživatele události vizuálně nebo behaviorally aktivačních událostí. Pro řízení stavu nebo stavu vlastnosti, jako se nejčastěji používá aktivační události vlastnost <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Například ve výchozím nastavení při <xref:System.Windows.Controls.Button> vypnutá (Spustit <xref:System.Windows.UIElement.IsEnabled%2A> je `false`) potom <xref:System.Windows.Controls.Control.Foreground%2A> styl motiv hodnotu co způsobí, že se objeví "šedě" ovládacího prvku. Ale pokud nastavíte místní <xref:System.Windows.Controls.Control.Foreground%2A> hodnotu, že normální na více systémů šedá barva bude mít přednost v přednost vaše místní vlastností nastavenou i v tomto scénáři aktivovaného vlastnost. Buďte opatrní nastavení hodnoty vlastností, které aktivační událost motiv úrovni chování a ujistěte se, že nejsou neoprávněně zasahování určený uživatelské prostředí pro ovládací prvek.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue a hodnota prioritu  
 <xref:System.Windows.DependencyObject.ClearValue%2A> Metoda poskytuje účelné znamená zrušte všechny místně použité hodnoty z vlastnosti závislosti, které jsou nastavené v elementu. Avšak volání <xref:System.Windows.DependencyObject.ClearValue%2A> není zárukou, výchozí hodnota, která vznikla v metadatech vlastnost registrace je novou platnou hodnotu. Všechny ostatní účastníci přednost hodnota jsou stále aktivní. Pouze nastavte místně hodnota byla odebrána z pořadí priorit. Například, pokud zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> u vlastnosti, kde tuto vlastnost je také nastavte ve stylu motiv a potom jako novou hodnotu než výchozí na základě metadat, je použita hodnota motivu. Pokud chcete provést všechny účastníky hodnotu vlastnosti mimo proces a nastavte hodnotu na výchozí registrované metadata, můžete získat, výchozí hodnota platností pomocí dotazu na metadata vlastnosti závislosti a pak můžete použít výchozí hodnotu pro místně Nastavte vlastnost pomocí volání <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Zpětné volání a ověření vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)
