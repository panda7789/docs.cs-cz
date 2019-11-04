---
title: Priorita hodnot závislých vlastností
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], classes as owners
- dependency properties [WPF], metadata
- classes [WPF], owners of dependency properties
- metadata [WPF], dependency properties
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
ms.openlocfilehash: 2abe89abf1ab246464c8f7a7ca7c87295b0b3946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458974"
---
# <a name="dependency-property-value-precedence"></a>Priorita hodnot závislých vlastností
<a name="introduction"></a>Toto téma vysvětluje, jak může pracovní postup [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému vlastností ovlivnit hodnotu vlastnosti závislosti a popisuje prioritu, podle které se aspekty systému vlastností vztahují na platnou hodnotu vlastnosti.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti na třídách [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a máte [Přehled vlastností závislostí](dependency-properties-overview.md)pro čtení. Chcete-li postupovat podle příkladů v tomto tématu, měli byste také pochopit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="intro"></a>   
## <a name="the-wpf-property-system"></a>Systém vlastností WPF  
 Systém vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabízí účinný způsob, jak mít hodnoty vlastností závislosti určené různými faktory, a to díky tomu, že funkce, jako je ověřování vlastností v reálném čase, pozdní vazba a oznamování souvisejících vlastností změn hodnot pro Další vlastnosti. Přesné pořadí a logika, které se používají k určení hodnot vlastností závislosti, jsou poměrně složité. Znalost tohoto pořadí vám pomůže vyhnout se zbytečnému nastavení vlastností a může také vymazat záměnu přesně, proč nějaký pokus o ovlivnění nebo předvídání hodnoty vlastnosti závislosti nekončí hodnotou, kterou jste očekávali.  
  
<a name="multiple_sets"></a>   
## <a name="dependency-properties-might-be-set-in-multiple-places"></a>Vlastnosti závislosti můžou být nastavené na více místech.  
 Následující příklad je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kde stejná vlastnost (<xref:System.Windows.Controls.Control.Background%2A>) má tři různé operace "Set", které by mohly ovlivnit hodnotu.  
  
 [!code-xaml[PropertiesOvwSupport#DPPrecedence](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 V tomto příkladu se použije barva, kterou očekáváte – červená, zelená nebo modrá?  
  
 S výjimkou animovaných hodnot a vynucení jsou místní sady vlastností nastaveny s nejvyšší prioritou. Pokud nastavíte hodnotu lokálně, můžete očekávat, že hodnota bude dodržena, dokonce i nad všemi styly nebo šablonami ovládacího prvku. V tomto příkladu je <xref:System.Windows.Controls.Control.Background%2A> nastavené na červenou místně. Proto styl definovaný v tomto oboru, i když je implicitní styl, který by jinak aplikován na všechny prvky daného typu v daném oboru, není nejvyšší prioritou pro poskytnutí <xref:System.Windows.Controls.Control.Background%2A> vlastnosti jeho hodnoty.  Pokud jste odstranili místní hodnotu Red z této instance tlačítka, měl by mít styl přednost a tlačítko získá hodnotu pozadí z stylu.  V rámci stylu mají aktivační události přednost, takže tlačítko bude modré, pokud je ukazatel myši nad ním a zelený jinak.  
  
<a name="listing"></a>   
## <a name="dependency-property-setting-precedence-list"></a>Seznam priorit nastavení vlastností závislosti  
 Následuje konečné pořadí, které systém vlastností používá při přiřazování hodnot běhového běhu pro vlastnosti závislosti. Nejvyšší priorita je uvedena jako první. Tento seznam se rozšíří na některé z generalizací provedených v [přehledu vlastností závislosti](dependency-properties-overview.md).  
  
1. **Vynucení systému vlastností.** Podrobnosti o vynucení najdete v části [konverze, animace a základní hodnota](#animations) dále v tomto tématu.  
  
2. **Aktivní animace nebo animace s chováním blokování.** Aby bylo možné mít nějaký praktický účinek, musí mít animace vlastnosti mít přednost před základní (neanimovanou) hodnotou, a to i v případě, že se tato hodnota nastavila lokálně. Podrobnosti najdete v části [konverze, animace a základní hodnota](#animations) dále v tomto tématu.  
  
3. **Lokální hodnota.** Místní hodnotu lze nastavit prostřednictvím pohodlí vlastnosti "Obálka", která je také rovna nastavení atributu nebo prvku vlastnosti v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nebo volání rozhraní API <xref:System.Windows.DependencyObject.SetValue%2A> pomocí vlastnosti určité instance. Pokud nastavíte místní hodnotu pomocí vazby nebo prostředku, tyto všechny tyto akce budou mít přednost, jako kdyby byla nastavena přímá hodnota.  
  
4. **Vlastnosti šablony TemplatedParent** Element má <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, pokud byl vytvořen jako součást šablony (<xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.DataTemplate>). Podrobnosti o tom, kdy se to týká, najdete v části [TemplatedParent](#templatedparent) dále v tomto tématu. V šabloně platí následující priorita:  
  
    1. Triggery ze šablony <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
    2. Sady vlastností (obvykle prostřednictvím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributů) v šabloně <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
5. **Implicitní styl** Vztahuje se pouze na vlastnost `Style`. Vlastnost `Style` je vyplněna jakýmkoli prostředkem stylu s klíčem, který se shoduje s typem daného prvku. Tento prostředek stylu musí existovat buď na stránce, nebo v aplikaci. vyhledávání pro implicitní prostředek stylu nepokračuje v motivech.  
  
6. **Triggery stylu** Aktivační události ve stylech ze stránky nebo aplikace (tyto styly mohou být buď explicitní, nebo implicitní styly, ale nikoli z výchozích stylů, které mají nižší prioritu).  
  
7. **Spouštěče šablon.** Libovolný Trigger ze šablony v rámci stylu nebo přímo použitou šablonu.  
  
8. **Settery stylu.** Hodnoty z <xref:System.Windows.Setter> v rámci stylů ze stránky nebo aplikace.  
  
9. **Výchozí styl (motiv).** Podrobnosti o tom, kdy se to týká, a jak se styly motivů vztahují k šablonám v rámci stylů motivů, naleznete v části [výchozí (motiv) styly](#themestyles) dále v tomto tématu. V rámci výchozího stylu platí následující pořadí priorit:  
  
    1. Aktivní triggery ve stylu motivu.  
  
    2. Metody setter ve stylu motivu.  
  
10. **Dědičnost.** Několik vlastností závislosti dědí jejich hodnoty z nadřazeného prvku na podřízené prvky, jako by nemusely být nastaveny konkrétně pro každý prvek v rámci aplikace. Podrobnosti najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).  
  
11. **Výchozí hodnota z metadat vlastnosti závislosti** Kterákoli z daných vlastností závislosti může mít výchozí hodnotu stanovenou registrací systému vlastností dané konkrétní vlastnosti. Také odvozené třídy, které dědí vlastnost závislosti, mají možnost přepsat tato metadata (včetně výchozí hodnoty) na základě typu. Další informace najdete v tématu [metadata vlastnosti závislosti](dependency-property-metadata.md) . Vzhledem k tomu, že dědičnost je u zděděné vlastnosti zkontrolována před výchozí hodnotou, má výchozí hodnota nadřazeného elementu přednost před podřízeným prvkem.  V důsledku toho, pokud vlastnost dědičná není nastavena kdekoli, použije se místo výchozí hodnoty podřízeného prvku výchozí hodnota zadaná v kořenu nebo nadřazeném objektu.  
  
<a name="templatedparent"></a>   
## <a name="templatedparent"></a>TemplatedParent  
 TemplatedParent jako položka priority se nevztahuje na žádnou vlastnost elementu, který deklarujete přímo v kódu standardní aplikace. Koncept TemplatedParent existuje pouze pro podřízené položky ve vizuálním stromu, který je součástí aplikace šablony. Když systém vlastností vyhledá v šabloně <xref:System.Windows.FrameworkElement.TemplatedParent%2A> hodnotu, hledá šablonu, která tento prvek vytvořila. Hodnoty vlastností z šablony <xref:System.Windows.FrameworkElement.TemplatedParent%2A> obvykle fungují jako v případě, že byly nastaveny jako místní hodnota u podřízeného prvku, ale tato nižší priorita a lokální hodnota existuje, protože šablony jsou potenciálně sdíleny. Podrobnosti najdete v tématu <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## <a name="the-style-property"></a>Vlastnost Style  
 Pořadí vyhledávání popsané dříve se vztahuje na všechny možné vlastnosti závislosti kromě jedné: vlastnost <xref:System.Windows.FrameworkElement.Style%2A>. Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> je jedinečná v tom, že sama nemůže být Style, takže se nepoužijí položky priority 5 až 8. Animace ani vynucený <xref:System.Windows.FrameworkElement.Style%2A> se nedoporučuje (a animace <xref:System.Windows.FrameworkElement.Style%2A> by vyžadovala vlastní třídu animace). To nechává tři způsoby, jak může být nastavena vlastnost <xref:System.Windows.FrameworkElement.Style%2A>:  
  
- **Explicitní styl.** Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> je nastavena přímo. Ve většině scénářů není styl definovaný jako inline, ale místo toho je odkazován jako prostředek pomocí explicitního klíče. V takovém případě vlastnost Style sám funguje, jako by to byla lokální hodnota, priorita – položka 3.  
  
- **Implicitní styl** Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> není nastavena přímo. <xref:System.Windows.FrameworkElement.Style%2A> však existuje na určité úrovni v sekvenci vyhledávání prostředků (stránka, aplikace) a používá se klíč prostředku, který odpovídá typu, na který se má styl použít. V tomto případě vlastnost <xref:System.Windows.FrameworkElement.Style%2A> sama funguje podle priority identifikovaného v sekvenci jako položka 5. Tuto podmínku lze zjistit pomocí <xref:System.Windows.DependencyPropertyHelper> proti vlastnosti <xref:System.Windows.FrameworkElement.Style%2A> a hledání <xref:System.Windows.BaseValueSource.ImplicitStyleReference> ve výsledcích.  
  
- **Výchozí styl**, označovaný také jako **styl motivu.** Vlastnost <xref:System.Windows.FrameworkElement.Style%2A> není nastavena přímo a ve skutečnosti bude načtena jako `null` až do doby běhu. V takovém případě styl pochází z vyhodnocení motivu za běhu, který je součástí modulu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentationer.  
  
 Pro implicitní styly, které nejsou v motivech, musí typ odpovídat přesně – `MyButton` `Button`odvozená třída implicitně nepoužívá Style pro `Button`.  
  
<a name="themestyles"></a>   
## <a name="default-theme-styles"></a>Výchozí (motiv) – styly  
 Každý ovládací prvek, který je dodáván s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], má výchozí styl. Tento výchozí styl se může lišit podle motivu, což je důvod, proč se tento výchozí styl někdy označuje jako styl motivu.  
  
 Nejdůležitější informace, které jsou nalezeny ve výchozím stylu ovládacího prvku, je jeho šablona ovládacího prvku, která existuje ve stylu motivu jako setter pro jeho vlastnost <xref:System.Windows.Controls.Control.Template%2A>. Pokud neexistovala žádná šablona z výchozích stylů, nebude mít ovládací prvek bez vlastní šablony jako součást vlastního stylu žádný vizuální vzhled. Šablona z výchozího stylu dává vizuální vzhled každého ovládacího prvku základní strukturu a také definuje připojení mezi vlastnostmi definovanými ve vizuálním stromu šablony a odpovídající třídou ovládacího prvku. Každý ovládací prvek zveřejňuje sadu vlastností, které mohou ovlivnit vzhled ovládacího prvku bez úplného nahrazení šablony. Zvažte například výchozí vizuální vzhled ovládacího prvku <xref:System.Windows.Controls.Primitives.Thumb>, který je součástí <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 <xref:System.Windows.Controls.Primitives.Thumb> má určité přizpůsobitelné vlastnosti. Výchozí šablona <xref:System.Windows.Controls.Primitives.Thumb> vytvoří základní strukturu/vizuální strom s několika vnořenými <xref:System.Windows.Controls.Border> komponentami, aby bylo možné vytvořit vzhled zkosení. Pokud je vlastnost, která je součástí šablony, určena k zpřístupnění pro přizpůsobení třídou <xref:System.Windows.Controls.Primitives.Thumb>, pak musí být tato vlastnost vystavena v rámci šablony [TemplateBinding](templatebinding-markup-extension.md). V případě <xref:System.Windows.Controls.Primitives.Thumb>různé vlastnosti těchto ohraničení sdílejí vazbu šablony k vlastnostem, jako je například <xref:System.Windows.Controls.Border.Background%2A> nebo <xref:System.Windows.Controls.Border.BorderThickness%2A>. Některé další vlastnosti nebo vizuální mechanismy jsou pevně zakódovány do šablony ovládacího prvku nebo jsou vázány na hodnoty, které přicházejí přímo z motivu, a nelze je změnit krátkým nahrazením celé šablony. Obecně platí, že pokud vlastnost pochází ze šablony nadřazeného objektu a není vystavena vazbou šablony, nemůže být upravena podle stylů, protože neexistuje snadný způsob, jak na ni cílit. Tato vlastnost však může být i nadále ovlivněna děděním hodnoty vlastnosti v použité šabloně nebo výchozí hodnotou.  
  
 Styly motivu používají jako klíč ve svých definicích typ. Nicméně pokud jsou motivy použity u dané instance elementu, vyhledávání motivů tohoto typu je provedeno kontrolou vlastnosti <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> ovládacího prvku. To je na rozdíl od použití literálového typu, jako implicitní styly. Hodnota <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> by dědila na odvozené třídy i v případě, že ji implementátor nezměnil (zamýšleným způsobem změny vlastnosti není přepsat na úrovni vlastnosti, ale místo toho změnit její výchozí hodnotu v metadatech vlastností). Tento nepřímý odkaz umožňuje třídám definovat styly motivů pro odvozené prvky, které jinak nemají styl (nebo jsou důležitější, nemají šablonu v rámci tohoto stylu a proto by neměl mít žádný výchozí vizuální vzhled). Proto můžete odvodit `MyButton` z <xref:System.Windows.Controls.Button> a bude stále mít <xref:System.Windows.Controls.Button> výchozí šablonu. Pokud jste autorem ovládacího prvku `MyButton` a chtěli jste jiné chování, mohli byste přepsat metadata vlastnosti závislosti pro <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> na `MyButton`, abyste vrátili jiný klíč, a pak definovat relevantní styly motivů, včetně šablony pro `MyButton` je nutné zabalit pomocí ovládacího prvku `MyButton`. Další informace o motivech, stylech a vytváření ovládacích prvků naleznete v tématu [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## <a name="dynamic-resource-references-and-binding"></a>Dynamické odkazy na prostředky a vazby  
 Dynamické odkazy na prostředky a operace vazby se týkají priority umístění, ve kterém jsou nastavené. Například dynamický prostředek použitý pro místní hodnotu funguje na základě priority položky 3, vazba pro metodu setter vlastnosti v rámci stylu motivu se vztahuje na prioritu položky 9 atd. Vzhledem k tomu, že dynamické odkazy na prostředky a vazby musí být schopny získat hodnoty z běhového stavu aplikace, to znamená, že skutečný proces určení priority hodnoty vlastnosti pro danou vlastnost se rozšíří i na dobu běhu.  
  
 Dynamické odkazy na prostředky nejsou bezpodmínečně součástí systému vlastností, ale mají vlastní pořadí vyhledávání, které komunikuje s pořadím uvedeným výše. Tato priorita je podrobněji popsána v [prostředcích XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md). Základní suma této priority je: element na kořen stránky, aplikace, motiv, systém.  
  
 Dynamické prostředky a vazby mají přednost, kde byly nastaveny, ale hodnota je odložena. Jedna z těchto hodnot je, že pokud nastavíte dynamický prostředek nebo vazbu na místní hodnotu, jakákoli změna místní hodnoty nahradí dynamický prostředek nebo vazbu zcela. I v případě, že zavoláte metodu <xref:System.Windows.DependencyObject.ClearValue%2A> pro vymazání místně nastavené hodnoty, dynamický prostředek nebo vazba nebudou obnoveny. Ve skutečnosti platí, že pokud voláte <xref:System.Windows.DependencyObject.ClearValue%2A> u vlastnosti, která má dynamický prostředek nebo vazbu na místě (bez lokální hodnoty literálu), jsou vymazány pomocí <xref:System.Windows.DependencyObject.ClearValue%2A> volání.  
  
<a name="setcurrentvalue"></a>   
## <a name="setcurrentvalue"></a>SetCurrentValue  
 Metoda <xref:System.Windows.DependencyObject.SetCurrentValue%2A> je další způsob, jak nastavit vlastnost, ale není v pořadí podle priority. Místo toho <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umožňuje změnit hodnotu vlastnosti bez přepsání zdroje předchozí hodnoty. Můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> kdykoli, kdy chcete nastavit hodnotu bez toho, aby tato hodnota měla přednost místní hodnotě. Pokud je například vlastnost nastavena triggerem a poté byla přiřazena další hodnota prostřednictvím <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, systém vlastností bude aktivační událost nadále respektovat a vlastnost se změní, pokud dojde k akci triggeru. <xref:System.Windows.DependencyObject.SetCurrentValue%2A> umožňuje změnit hodnotu vlastnosti bez toho, aby byla zdrojem s vyšší prioritou. Podobně můžete použít <xref:System.Windows.DependencyObject.SetCurrentValue%2A> ke změně hodnoty vlastnosti bez přepsání vazby.  
  
<a name="animations"></a>   
## <a name="coercion-animations-and-base-value"></a>Konverze, animace a základní hodnota  
 Na základě hodnoty, která je v rámci této [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]termínem "základní hodnota", je vynucená a animace. Základní hodnota je, takže jakákoli hodnota je určena pomocí hodnocení nahoru v položkách až do dosažení položky 2.  
  
 V případě animace může mít základní hodnota efekt na animovanou hodnotu, pokud tato animace neurčuje pro určité chování obě "od" i "do", nebo pokud se animace záměrně po dokončení vrátí k základní hodnotě. Chcete-li se podívat v praxi, spusťte [ukázku hodnot cíle animace z, do a podle animace](https://go.microsoft.com/fwlink/?LinkID=159988). Zkuste nastavit místní hodnoty výšky obdélníku v příkladu tak, aby se počáteční místní hodnota v animaci lišila od libovolné "od". Všimněte si, že animace začínají hned za použití hodnot "od" a po spuštění nahradí základní hodnotu. Animace může určit, že se má vrátit k hodnotě nalezené před animací po jejím dokončení zadáním stop <xref:System.Windows.Media.Animation.FillBehavior>. Následně se pro stanovení základní hodnoty použije normální priorita.  
  
 Pro jednu vlastnost lze použít více animací, přičemž každý z těchto animací je pravděpodobně definován z různých bodů v prioritě hodnoty. Nicméně tyto animace budou potenciálně složené jejich hodnoty, nikoli jenom použití animace z vyšší priority. To závisí přesně na tom, jak jsou animace definovány, a typu hodnoty, která je animovaná. Další informace o animování vlastností najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).  
  
 Vynucení platí na nejvyšší úrovni. I již spuštěná animace podléhá vynucení hodnot. Některé existující vlastnosti závislosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] měly vestavěnou vynucenou. U vlastní vlastnosti závislosti definujete chování při vynucení pro vlastní vlastnost závislosti zápisem <xref:System.Windows.CoerceValueCallback> a předáním zpětného volání jako součásti metadat při vytváření vlastnosti. Můžete také přepsat chování při vynucení stávajících vlastností přepsáním metadat u této vlastnosti v odvozené třídě. Konverze komunikuje se základní hodnotou takovým způsobem, že omezení pro vynucení jsou použita, protože tato omezení existují v čase, ale základní hodnota je stále zachovaná. Proto pokud jsou omezení v vynucení později převedená, vrátí vynucení nejbližší hodnotu k této základní hodnotě a potenciálně ovlivněný vliv na vlastnost přestane, jakmile budou všechna omezení vyvolána. Další informace o chování při vynucení naleznete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## <a name="trigger-behaviors"></a>Chování triggeru  
 Ovládací prvky často definují chování triggeru jako součást jejich výchozího stylu v motivech. Nastavení místních vlastností ovládacího prvku může zabránit aktivačním událostem v reakci na události řízené uživateli, a to buď vizuálně, nebo behaviorální. Nejběžnějším použitím triggeru vlastnosti jsou vlastnosti ovládacího prvku nebo stavu, jako je například <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>. Například ve výchozím nastavení, když je zakázaný <xref:System.Windows.Controls.Button> (Trigger pro <xref:System.Windows.UIElement.IsEnabled%2A> je `false`), pak hodnota <xref:System.Windows.Controls.Control.Foreground%2A> ve stylu motivu způsobí, že se ovládací prvek zobrazí šedě. Pokud jste ale nastavili místní hodnotu <xref:System.Windows.Controls.Control.Foreground%2A>ou, bude mít normální barva šedé na více instancí přednost před nastavením místní vlastnosti, a to i v tomto scénáři aktivovaném vlastností. Buďte opatrní při nastavení hodnot pro vlastnosti, které mají chování triggeru na úrovni motivu, a ujistěte se, že nebudete mít řádný vliv na zamýšlené uživatelské prostředí pro daný ovládací prvek.  
  
<a name="clearvalue"></a>   
## <a name="clearvalue-and-value-precedence"></a>ClearValue a Priorita hodnoty  
 Metoda <xref:System.Windows.DependencyObject.ClearValue%2A> poskytuje účel pro vymazání všech místně použitých hodnot z vlastnosti závislosti, která je nastavena u prvku. Volání <xref:System.Windows.DependencyObject.ClearValue%2A> však není zárukou, že výchozí hodnota stanovená v metadatech během registrace vlastnosti je nová efektivní hodnota. Všichni ostatní účastníci v prioritě hodnot jsou stále aktivní. Z pořadí priorit byla odebrána pouze místně nastavená hodnota. Například pokud zavoláte <xref:System.Windows.DependencyObject.ClearValue%2A> u vlastnosti, kde je tato vlastnost nastavena také stylem motivu, bude hodnota motivu použita jako nová hodnota, nikoli jako výchozí nastavení založené na metadatech. Pokud chcete převzít všechny hodnoty vlastností z procesu a nastavit hodnotu na výchozí registrovanou metadata, můžete tuto výchozí hodnotu získat definitivně pomocí dotazu na metadata vlastnosti závislosti a potom můžete použít výchozí hodnotu místně. Nastavte vlastnost se voláním <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyObject>
- <xref:System.Windows.DependencyProperty>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Zpětné volání a ověření vlastností závislostí](dependency-property-callbacks-and-validation.md)
