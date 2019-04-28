---
title: Zdroje XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 0176ebffe82e60671ea66481b7d659004dc31477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757076"
---
# <a name="xaml-resources"></a>Zdroje XAML
Prostředek je objekt, který je možné využít v různých míst ve své aplikaci. Příklady prostředků: štětce a styly. Tento přehled popisuje, jak použít zdroje v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Můžete také vytvořit a přístup k prostředkům pomocí kódu nebo Zaměnitelně mezi kódem a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Další informace najdete v tématu [zdroje a kód](resources-and-code.md).  
  
> [!NOTE]
>  Soubory prostředků, které jsou popsané v tomto tématu se liší podle soubory prostředků [prostředek aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md) a jiné než vložené nebo propojené prostředky podle [spravovat Prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Použití prostředků v XAML  
 Následující příklad definuje <xref:System.Windows.Media.SolidColorBrush> jako prostředek v kořenovém elementu na stránce. V příkladu se pak odkazuje na prostředek a používá k nastavení vlastností několik podřízených prvků, včetně <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Každý prvek úrovni architektury (<xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost, která je vlastnost, která obsahuje prostředky (jako <xref:System.Windows.ResourceDictionary>), který definuje prostředek. Prostředky můžete definovat na libovolný element. Ale zdroje jsou často definovány v kořenovém elementu, který je <xref:System.Windows.Controls.Page> v příkladu.  
  
 Každý prostředek ve slovníku prostředků musí mít jedinečný klíč. Při definování prostředků v kódu, můžete přiřadit jedinečný klíč prostřednictvím [x: Key – direktiva](../../xaml-services/x-key-directive.md). Klíč je obvykle řetězec; však můžete také nastavit ho na jiné typy objektů pomocí rozšíření odpovídající značky. Neřetězcové klíče pro prostředky používají určité oblasti funkcí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zejména pro styly, součástí zdroje a používání stylů pro data.  
  
 Potom co definujete prostředek, mohou odkazovat na prostředek použitého pro hodnotu vlastnosti s využitím prostředků rozšíření syntaxe značek, který určuje název klíče, například:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 V předchozím příkladu při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč zpracuje hodnotu `{StaticResource MyBrush}` pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Button>, logika vyhledávání prostředků nejprve zkontroluje, zda slovník prostředků pro <xref:System.Windows.Controls.Button> elementu. Pokud <xref:System.Windows.Controls.Button> nemá definici klíč prostředku `MyBrush` (tomu tak není, jeho prostředků kolekce je prázdná), vyhledávání příště připojí nadřazený element <xref:System.Windows.Controls.Button>, což je <xref:System.Windows.Controls.Page>. Proto když definujete prostředek na <xref:System.Windows.Controls.Page> kořenový element, všechny prvky v logického stromu <xref:System.Windows.Controls.Page> k němu přístup, a pro nastavení hodnota libovolné vlastnosti, které přijímá můžete znovu použít stejný prostředek <xref:System.Type> , který prostředek představuje. V předchozím příkladu, stejné `MyBrush` nastaví dva různé vlastnosti prostředku: <xref:System.Windows.Controls.Control.Background%2A> z <xref:System.Windows.Controls.Button>a <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statické a dynamické prostředky  
 Prostředek může být odkazováno jako prostředek statické nebo dynamické prostředek. To se provádí pomocí buď [StaticResource – rozšíření značek](staticresource-markup-extension.md) nebo [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md). Rozšíření značek je funkce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zajišťovaný zadáte odkaz na objekt tím, že rozšíření značek zpracovat atribut řetězců a vrátí objekt, který má [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděče. Další informace týkající se chování rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Při použití rozšíření značek, je obvykle zadat jeden nebo více parametrů v podobě řetězce, které se zpracovávají v tomto rozšíření konkrétní kód, nikoli právě vyhodnocuje v rámci nastavování vlastnosti. [– Rozšíření značek StaticResource](staticresource-markup-extension.md) zpracovává klíč vyhledáním hodnotu pro daný klíč ve všech dostupných zdrojové slovníky. K tomu dojde při načítání, který představuje bod v čase, když je potřeba přiřadit hodnotu, která přebírá odkaz na prostředek statické proces načítání. [– Rozšíření značek DynamicResource](dynamicresource-markup-extension.md) místo toho procesy klíč tak, že vytvoříte výraz a tento výraz zůstane nevyhodnoceném dokud skutečně při spuštění aplikace, po kterém výraz je vyhodnocen a poskytuje hodnotu.  
  
 Při odkazování na prostředek, mohou ovlivnit následující aspekty, ať už používáte statický prostředek nebo odkaz na dynamický prostředek:  
  
- Celkový návrh, jak vytvořit prostředky pro vaše aplikace (na stránce v aplikaci v volné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], v pouze sestavení prostředků).  
  
- Funkčnost aplikace: aktualizuje prostředky v reálném čase součástí požadavků aplikace?  
  
- Chování příslušných vyhledávání tohoto typu odkazu prostředku.  
  
- Konkrétní vlastnost nebo typ prostředku a nativní chování těchto typů.  
  
### <a name="static-resources"></a>Statické prostředky  
 Statický prostředek odkazuje pracovní nejlépe za těchto okolností:  
  
- Návrh aplikací se soustřeďuje nejvíce všech jeho prostředků do stránky nebo aplikace prostředků s úrovní slovníky. Odkazy na statické prostředky nejsou již znovu podle chování za běhu, jako je například opětovné načítání stránky, a proto může existovat několik výhod výkonu k zamezení velký počet odkazů na dynamický prostředek, pokud nejsou nutné na váš prostředek a návrh aplikace.  
  
- Nastavíte hodnotu vlastnosti, které nejsou na <xref:System.Windows.DependencyObject> nebo <xref:System.Windows.Freezable>.  
  
- Při vytváření slovník prostředků, který bude zkompilována do knihovny DLL a lze zabalit jako součást aplikace nebo sdílené mezi aplikacemi.  
  
- Vytváření motivu pro ovládací prvek vlastní a definování prostředky, které se používají v rámci motivy. V takovém případě obvykle nechcete, aby chování při vyhledávání odkaz dynamický prostředek, místo toho chcete odkaz na chování statických prostředků tak, aby vyhledávání zajišťuje předvídatelný a nezávislý na motiv. Dynamický prostředek neověřené odkaz, dokonce i odkaz v rámci motiv zůstane až do modulu runtime a může se stát, že po motiv použije, některé místní element bude znovu definovat klíč, který motiv se pokouší odkazovat a místní element bude spadat předchozí motiv samotné při vyhledávání. Pokud k tomu dojde, nebude chovat motivu očekávaným způsobem.  
  
- Používáte prostředky k nastavení velkého množství vlastností závislostí. Vlastnosti závislostí mít platnou hodnotu ukládání do mezipaměti jako povolené vlastnosti systému, takže pokud zadáte hodnotu pro vlastnost závislosti, které mohou být vyhodnoceny v okamžiku načtení, vlastnost závislosti není nutné vyhledávat reevaluated výraz a vrátit poslední platnou hodnotu. Tato technika může být zvýšení výkonu.  
  
- Chcete změnit základní prostředek pro všechny zákazníky, nebo chcete zachovat samostatných instancí pro každého příjemce pomocí [x: sdílený atribut](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Chování při vyhledávání statický prostředek  
  
1. Proces vyhledávání vyhledá požadovaný klíč ve slovníku prostředků, které jsou definovány pomocí elementu, který nastaví vlastnost.  
  
2. Logická stromová struktura směrem nahoru, proces vyhledávání následně prochází nadřazeného elementu a jeho slovníku prostředků. Tento postup se opakuje, dokud nebude dosaženo kořenový element.  
  
3. V dalším kroku se kontroluje prostředky aplikace. Prostředky aplikace jsou prostředky v rámci slovníku prostředků, který je definován <xref:System.Windows.Application> objekt pro vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
 Odkazy na statické prostředky z v rámci slovníku prostředků musí odkazovat na prostředek, který již byl definován lexikálně před odkaz na prostředek. Dopředné odkazy nemůže přeložit odkaz statických prostředků. Z tohoto důvodu Pokud používáte odkazy na statické prostředky, je třeba navrhnout strukturu slovníku prostředků tak, aby prostředky, které jsou určené pro použití podle prostředků jsou definovány v nebo na začátku každé slovník příslušných prostředků.  
  
 Statický prostředek vyhledávání můžete rozšířit do motivy, nebo do systémové prostředky, ale tato funkce je podporována pouze, protože [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč odloží požadavku. Odložení je nutné, aby modul runtime motiv v době, kdy se stránka načte správně platí pro aplikaci. Statický prostředek však odkazuje na klíče, které se ví, že existují pouze v motivy, nebo jako systém, které prostředky se nedoporučuje. Je to proto, že tyto odkazy se již znovu motiv při změně uživatelem v reálném čase. Dynamický prostředek odkaz je spolehlivější, pokud budete požadovat motiv nebo dostatek systémových prostředků. Výjimkou je, když motiv elementu samotného požádá o jiný prostředek. Tyto odkazy by měl být odkazy na statické prostředky z důvodů již bylo zmíněno dříve.  
  
 Se liší chování výjimky, pokud odkaz statický prostředek nebyl nalezen. Pokud byla odložena na prostředek, k výjimce dochází za běhu. Pokud prostředek nebyl odloženo, k výjimce dochází v okamžiku načtení.  
  
### <a name="dynamic-resources"></a>Dynamické prostředky  
 Dynamické prostředky nejvhodnější za těchto okolností:  
  
- Hodnota prostředku závisí na podmínkách, které nejsou známy až do modulu runtime. To zahrnuje systémových prostředků nebo prostředky, které jsou jinak uživatel nastavitelná při čekání. Například můžete vytvořit metodu setter hodnoty, které odkazují na vlastnosti systému jako vystavené <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, nebo <xref:System.Windows.SystemParameters>. Tyto hodnoty jsou skutečně dynamické, protože nakonec pocházejí z běhové prostředí uživatele a operačního systému. Také může mít motivů na úrovni aplikace, které se mohou měnit, ve kterém přístup k prostředkům na úrovni stránky musí zachytit změny.  
  
- Vytváříte nebo odkazující na styly motivů pro vlastní ovládací prvek.  
  
- Máte v úmyslu upravte obsah <xref:System.Windows.ResourceDictionary> během dobu životnosti aplikace.  
  
- Máte složité prostředků strukturu, která má vzájemné závislosti, kde mohou být požadovány dopředný odkaz. Odkazy na statické prostředky nepodporuje odkazy směrem vpřed, ale dynamický prostředek odkazy podporují je vzhledem k tomu, že prostředek není potřeba vyhodnotit až do modulu runtime a dopředné odkazy z tohoto důvodu nejsou relevantní koncept.  
  
- Odkazujete na prostředek, který je zejména velkých z hlediska kompilace nebo pracovní sady a zdroje nemusí být použity hned po načtení stránky. Odkazy na statické prostředky vždy načítat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] při načtení stránky; však není odkaz dynamický prostředek načítat, dokud se ve skutečnosti používá.  
  
- Vytváření stylu, kde může nastavení hodnoty pocházejí z jiné hodnoty, které jsou ovlivněny motivů nebo jiná nastavení uživatele.  
  
- Prostředky aplikujete na elementy, které může být v logickém stromu potomkům během životního cyklu aplikace. Změna nadřazeného také potenciálně změní rozsah vyhledávání prostředků, proto pokud chcete prostředek pro prvek reparented se znovu vyhodnotit podle nového oboru, vždy použijte odkaz dynamický prostředek.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Chování při vyhledávání dynamický prostředek  
 Chování při vyhledávání prostředků pro odkaz na dynamický prostředek parallels chování vyhledávání v kódu při volání <xref:System.Windows.FrameworkElement.FindResource%2A> nebo <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1. Proces vyhledávání vyhledá požadovaný klíč ve slovníku prostředků, které jsou definovány pomocí elementu, který nastaví vlastnost.  
  
    - Pokud element definuje <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, <xref:System.Windows.Style.Resources%2A> slovníku v rámci <xref:System.Windows.Style> je zaškrtnuté políčko.  
  
    - Pokud element definuje <xref:System.Windows.Controls.Control.Template%2A> vlastnost, <xref:System.Windows.FrameworkTemplate.Resources%2A> slovníku v rámci <xref:System.Windows.FrameworkTemplate> je zaškrtnuté políčko.  
  
2. Logická stromová struktura směrem nahoru, proces vyhledávání následně prochází nadřazeného elementu a jeho slovníku prostředků. Tento postup se opakuje, dokud nebude dosaženo kořenový element.  
  
3. V dalším kroku se kontroluje prostředky aplikace. Prostředky aplikace jsou prostředky v rámci slovníku prostředků, který je definován <xref:System.Windows.Application> objekt pro vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
4. Slovník prostředků motiv se kontroluje u aktuálně aktivní motiv. Pokud, motiv se změní za běhu, hodnota je již znovu.  
  
5. Systémové prostředky jsou kontrolovány.  
  
 Výjimka chování (pokud existuje) se liší:  
  
- Pokud byl prostředek požadoval <xref:System.Windows.FrameworkElement.FindResource%2A> volání a nebyla nalezena, je vyvolána výjimka.  
  
- Pokud byl prostředek požadoval <xref:System.Windows.FrameworkElement.TryFindResource%2A> volání a nebyla nalezena, je vyvolána žádná výjimka, ale vrácená hodnota je `null`. Pokud je vlastnost nastavena nepřijímá `null`, je stále možné, že hlubší výjimka bude vyvolána (záleží na jednotlivé vlastnosti nastavena).  
  
- Pokud prostředek byl požadován odkaz dynamický prostředek v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nebyla nalezena, pak chování závisí na obecné vlastnosti systému, ale obecné chování je, jako kdyby žádná operace nastavení vlastností došlo k chybě na úrovni, kde existuje prostředek. Například pokud se pokusíte nastavit na pozadí jednotlivá tlačítka elementu s použitím prostředek, který nemůže být vyhodnocena, pak nastavena žádná hodnota výsledky, ale efektivní hodnotou stále můžou pocházet z účastníci Priorita systému a hodnoty vlastností. Hodnoty na pozadí, stále může pocházet ze styl tlačítka pro místně definovaný, nebo stylu motivu. Pro vlastnosti, které nejsou definovány styly motivů platnou hodnotu po vyhodnocení problémovému prostředku může pocházet z výchozí hodnoty v metadatech vlastnost.  
  
#### <a name="restrictions"></a>Omezení  
 Dynamický prostředek odkazy mají některé důležité omezení. Nejméně jednu z následujících musí mít hodnotu true:  
  
- Vlastnost nastavena, musí být vlastnost na <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>. Vlastnost musí opírá <xref:System.Windows.DependencyProperty>.  
  
- Odkaz je pro hodnoty v rámci <xref:System.Windows.Style> <xref:System.Windows.Setter>.  
  
- Vlastnost nastavena, musí být vlastnost na <xref:System.Windows.Freezable> , který je zadaný jako hodnota buď <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> vlastnost, nebo <xref:System.Windows.Setter> hodnotu.  
  
 Protože musí být vlastnost nastavena <xref:System.Windows.DependencyProperty> nebo <xref:System.Windows.Freezable> vlastnost, většina změny vlastností se může rozšířit do uživatelského rozhraní vzhledem k tomu, že změna vlastnosti (hodnota změněné dynamický prostředek) je potvrzen v systému vlastností. Většina ovládací prvky zahrnují logiku, která vynutí jiné rozložení ovládacího prvku, pokud <xref:System.Windows.DependencyProperty> změny a že vlastnost může ovlivnit rozložení. Nicméně jsou všechny vlastnosti, které mají [– rozšíření značek DynamicResource](dynamicresource-markup-extension.md) jako jejich hodnota je zaručeno, zadejte hodnotu tak, že aktualizují v reálném čase v uživatelském rozhraní. Které tuto funkci stále se může lišit v závislosti na vlastnosti, stejně jako v závislosti na typu, který vlastní vlastnost, nebo dokonce logické struktury vaší aplikace.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Styly, DataTemplates a implicitní klíče  
 Dříve bylo uvedeno, že všechny položky v <xref:System.Windows.ResourceDictionary> musí mít klíč. Nicméně to neznamená, že všechny zdroje musí mít explicitní `x:Key`. Několik typů objektů podporují implicitní klíč, když je definována jako prostředek, kde hodnota klíče, která se váže na hodnotě jiné vlastnosti. To se označuje jako implicitní klíč, vzhledem `x:Key` atribut je explicitní klíč. Žádné implicitní klíč můžete přepsat zadáním explicitní klíč.  
  
 Jeden scénář velmi důležité pro zdroje je při definování <xref:System.Windows.Style>. Ve skutečnosti <xref:System.Windows.Style> je téměř vždy definována jako položku ve slovníku prostředků, protože styly jsou ze své podstaty určené pro opakované použití. Další informace o stylech najdete v tématu [styly a šablony](../controls/styling-and-templating.md).  
  
 Styly pro ovládací prvky mohou být vytvořené pomocí i odkazovaný adresou implicitní klíč. Spolehněte se na tento klíč implicitní styly motivů, které definují výchozí vzhled ovládacího prvku. Implicitní klíč z hlediska požadavku <xref:System.Type> samotného ovládacího prvku. Implicitní klíč z hlediska definice prostředku je <xref:System.Windows.Style.TargetType%2A> daného stylu. Proto pokud vytváříte motivy pro vlastní ovládací prvky, vytváření styly, které pracují s existující styly motivů, nepotřebujete k určení [x: Key – direktiva](../../xaml-services/x-key-directive.md) pro daný <xref:System.Windows.Style>. A pokud chcete použít s motivem styly, není potřeba zadat jakýkoli styl vůbec. Například následující definice stylu funguje, i když <xref:System.Windows.Style> prostředků nezobrazí klíč:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Styl opravdu že klíč: implicitní klíč `typeof(` <xref:System.Windows.Controls.Button> `)`. V kódu, můžete zadat <xref:System.Windows.Style.TargetType%2A> přímo jako typ název (nebo můžete volitelně použít [{x: Type...}](../../xaml-services/x-type-markup-extension.md) Chcete-li vrátit <xref:System.Type>.  
  
 Prostřednictvím mechanismů výchozí motiv styl používaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], stylem jako styl modulu runtime <xref:System.Windows.Controls.Button> na stránce i v případě, <xref:System.Windows.Controls.Button> samotný nebude pokoušet o zadejte jeho <xref:System.Windows.FrameworkElement.Style%2A> vlastnost nebo konkrétní prostředek odkaz na styl. Vašemu stylu na stránce definován najdete výše v pořadí vyhledávání než styl slovníku motivu, pomocí stejného klíče, který má slovníku stylu motivu. Můžete pouze zadat `<Button>Hello</Button>` kamkoli do stránky a styl je definovaný s <xref:System.Windows.Style.TargetType%2A> z `Button` by použít na toto tlačítko. Pokud chcete, můžete stále explicitně klíče styl se stejnou hodnotou typu jako <xref:System.Windows.Style.TargetType%2A>pro přehlednost ve vašem kódu, ale je volitelný.  
  
 Implicitní klíče pro stylů se nevztahují na ovládacím prvku Pokud <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> je `true` (Všimněte si také, <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> může být nastaveno jako součást nativní chování pro ovládací prvek třídy, nikoli explicitně na instanci ovládacího prvku). Také, aby bylo možné podporovat implicitní klíče pro scénáře, / / coleserveritem, musí přepsat ovládací prvek <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (všechny existující ovládací prvky, které jsou k dispozici jako součást [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tomu). Další informace o styly, motivy a ovládací prvek návrhu najdete v tématu [pokyny pro návrh s podporou stylů ovládací prvky](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> má také implicitní klíč. Implicitní klíč pro <xref:System.Windows.DataTemplate> je <xref:System.Windows.DataTemplate.DataType%2A> hodnotu vlastnosti. <xref:System.Windows.DataTemplate.DataType%2A> Můžete taky možné specifikovat jako název typu, nikoli explicitně pomocí [{x: Type...} ](../../xaml-services/x-type-markup-extension.md). Podrobnosti najdete v tématu [přehled datových šablon](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Prostředky a kód](resources-and-code.md)
- [Definice a odkaz prostředku](how-to-define-and-reference-a-resource.md)
- [Přehled správy aplikací](../app-development/application-management-overview.md)
- [x:Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md)
- [Rozšíření značek StaticResource](staticresource-markup-extension.md)
- [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md)
