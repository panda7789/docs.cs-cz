---
title: Definování prostředků XAML
description: Další informace o prostředcích XAML v WPF pro .NET Core. Seznamte se s typy prostředků XAML a zjistěte, jak definovat prostředky XAML.
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: b278bb92afc308578d60e347871e0150b26a95db
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "82071281"
---
# <a name="overview-of-xaml-resources"></a>Přehled zdrojů XAML

Prostředek je objekt, který lze znovu použít na různých místech aplikace. Příklady zdrojů zahrnují stopy a styly. Tento přehled popisuje, jak používat prostředky v jazyce Xml (XAML). Můžete také vytvořit a přístup k prostředkům pomocí kódu.

> [!NOTE]
> Prostředky XAML popsané v tomto článku se liší od *prostředků aplikace,* což jsou obecně soubory přidané do aplikace, jako je obsah, data nebo vložené soubory.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Použití prostředků v XAML

Následující příklad definuje <xref:System.Windows.Media.SolidColorBrush> jako prostředek na kořenový prvek stránky. Příklad pak odkazuje na prostředek a používá jej k nastavení <xref:System.Windows.Shapes.Ellipse>vlastností <xref:System.Windows.Controls.TextBlock>několika <xref:System.Windows.Controls.Button>podřízených prvků, včetně , a a .

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Každý prvek na<xref:System.Windows.FrameworkElement> úrovni <xref:System.Windows.FrameworkContentElement>rozhraní <xref:System.Windows.FrameworkElement.Resources%2A> ( nebo ) <xref:System.Windows.ResourceDictionary> má vlastnost, což je typ, který obsahuje definované prostředky. Můžete definovat prostředky na libovolný prvek, například <xref:System.Windows.Controls.Button>. Prostředky jsou však nejčastěji definovány na <xref:System.Windows.Controls.Page> kořenový prvek, který je v příkladu.

Každý prostředek ve slovníku prostředků musí mít jedinečný klíč. Když definujete prostředky ve značkách, přiřadíte jedinečný klíč prostřednictvím [x:Key Directive](../xaml-services/xkey-directive.md). Obvykle je klíčem řetězec; můžete jej však také nastavit na jiné typy objektů pomocí příslušných rozšíření značek. Klíče bez řetězce pro prostředky používají určité oblasti prvků v WPF, zejména pro styly, prostředky komponent a styly dat.

Můžete použít definovaný prostředek se syntaxí rozšíření značek prostředků, která určuje název klíče prostředku. Například použijte prostředek jako hodnotu vlastnosti na jiný prvek.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

V předchozím příkladu, když zavaděč XAML zpracuje `{StaticResource MyBrush}` hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti na <xref:System.Windows.Controls.Button>, logika <xref:System.Windows.Controls.Button> vyhledávání prostředků nejprve zkontroluje slovník prostředků pro prvek. Pokud <xref:System.Windows.Controls.Button> nemá definici klíče `MyBrush` prostředku (v tomto příkladu nemá; jeho kolekce prostředků je prázdná), vyhledávání <xref:System.Windows.Controls.Button>další <xref:System.Windows.Controls.Page>kontroly nadřazený prvek , který je . Pokud definujete prostředek <xref:System.Windows.Controls.Page> na kořenový prvek, všechny prvky <xref:System.Windows.Controls.Page> v logickém stromu může přistupovat k němu. A můžete znovu použít stejný prostředek pro nastavení hodnoty libovolné vlastnosti, která přijímá stejný typ, který představuje prostředek. V předchozím příkladu `MyBrush` stejný prostředek nastaví <xref:System.Windows.Controls.Control.Background%2A> dvě <xref:System.Windows.Controls.Button>různé vlastnosti: <xref:System.Windows.Shapes.Rectangle>a , a <xref:System.Windows.Shapes.Shape.Fill%2A> .

## <a name="static-and-dynamic-resources"></a>Statické a dynamické prostředky

Prostředek lze odkazovat jako statické nebo dynamické. Odkazy jsou vytvářeny pomocí [rozšíření StaticResource Markup Extension](../../framework/wpf/advanced/staticresource-markup-extension.md) nebo [DynamicResource Markup Extension](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Rozšíření značek je funkce XAML, která umožňuje určit odkaz na objekt tak, že rozšíření značek zpracuje řetězec atributu a vrátí objekt zavaděči XAML. Další informace o chování rozšíření značek naleznete v [tématu Markup Extensions a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Při použití rozšíření značky obvykle zadáte jeden nebo více parametrů v řetězcové podobě, které jsou zpracovány tímto konkrétním rozšířením značek. [Rozšíření staticresource markup](../../framework/wpf/advanced/staticresource-markup-extension.md) zpracovává klíč vyhledáním hodnoty pro tento klíč ve všech dostupných slovníků prostředků. Zpracování probíhá během načítání, což je, když proces načítání potřebuje přiřadit hodnotu vlastnosti. [Rozšíření dynamicResource Markup extension](../../framework/wpf/advanced/dynamicresource-markup-extension.md) místo toho zpracovává klíč vytvořením výrazu a tento výraz zůstane nevyhodnotiný, dokud se aplikace nespustí, kdy je výraz vyhodnocen a poskytuje hodnotu.

Když odkazujete na prostředek, následující aspekty mohou ovlivnit, zda používáte odkaz na statický prostředek nebo odkaz na dynamický prostředek:

- Při určování celkového návrhu způsobu vytváření prostředků pro vaši aplikaci (na stránku, v aplikaci, ve volné xaml nebo v sestavení pouze pro prostředky) zvažte následující:

- Funkce aplikace. Jsou aktualizace prostředků v reálném čase součástí požadavků na aplikaci?
- Příslušné chování vyhledávání tohoto typu odkazu na prostředek.
- Konkrétní typ vlastnosti nebo prostředku a nativní chování těchto typů.

## <a name="static-resources"></a>Statické prostředky

Odkazy na statické prostředky fungují nejlépe z následujících okolností:

- Návrh aplikace soustřeďuje většinu svých prostředků do slovníků prostředků na úrovni stránky nebo aplikace. Statické odkazy na prostředky nejsou přehodnoceny na základě chování za běhu, jako je například opětovné načtení stránky. Takže může být některé výhody výkonu, aby se zabránilo velký počet odkazů na dynamické prostředky, pokud nejsou nezbytné na základě vašeho prostředku a návrhu aplikace.

- Nastavujete hodnotu vlastnosti, která není <xref:System.Windows.DependencyObject> na <xref:System.Windows.Freezable>nebo .

- Vytváříte slovník prostředků, který bude zkompilován do dll a zabalen jako součást aplikace nebo sdílen mezi aplikacemi.

- Vytváříte motiv pro vlastní ovládací prvek a definujete prostředky, které se používají v rámci motivů. V tomto případě obvykle nechcete chování vyhledávání odkazů na dynamický prostředek; místo toho chcete statické chování odkazu na prostředky tak, aby vyhledávání bylo předvídatelné a samostatné motivu. S odkazem na dynamický prostředek i odkaz v rámci motivu je ponechána nevyhodnotiná až do běhu. a je pravděpodobné, že při použití motivu některé místní prvek předefinuje klíč, který se motiv pokouší odkazovat, a místní prvek bude spadat před samotný motiv ve vyhledávání. Pokud k tomu dojde, motiv se nebude chovat podle očekávání.

- Prostředky používáte k nastavení velkého počtu vlastností závislostí. Vlastnosti závislostí mají efektivní ukládání hodnoty do mezipaměti, jak je povoleno systémem vlastností, takže pokud zadáte hodnotu vlastnosti závislosti, kterou lze vyhodnotit v době zatížení, vlastnost závislosti nemusí kontrolovat přehodnocený výraz a může vrátit poslední efektivní hodnotu. Tato technika může být výhoda výkonu.

- Chcete změnit základní prostředek pro všechny spotřebitele nebo chcete udržovat samostatné zapisovatelné instance pro každého příjemce pomocí [atributu x:Shared Attribute](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Chování vyhledávání statických prostředků

Následující text popisuje proces vyhledávání, ke kterému automaticky dochází, když je statický prostředek odkazován vlastností nebo elementem:

01. Proces vyhledávání kontroluje požadovaný klíč v rámci slovníku prostředků definovaného elementem, který nastavuje vlastnost.

01. Proces vyhledávání pak prochází logický strom směrem nahoru k nadřazenému prvku a jeho slovníku prostředků. Tento proces pokračuje, dokud není dosaženo kořenového prvku.

01. Prostředky aplikace jsou kontrolovány. Prostředky aplikace jsou prostředky v rámci slovníku <xref:System.Windows.Application> prostředků, který je definován objektem pro vaši aplikaci WPF.

Statické odkazy na prostředky ze slovníku prostředků musí odkazovat na prostředek, který již byl definován lexikálně před odkazem na prostředek. Dopředné odkazy nelze přeložit pomocí statického odkazu na prostředky. Z tohoto důvodu navrhněte strukturu slovníku prostředků tak, aby prostředky byly definovány na začátku každého příslušného slovníku prostředků nebo v jeho blízkosti.

Vyhledávání statických prostředků se může rozšířit do motivů nebo do systémových prostředků, ale toto vyhledávání je podporováno pouze proto, že zavaděč XAML požadavek odloží. Časově rozlišení je nezbytné, aby motiv za běhu v době, kdy se stránka načte, správně naplatil na aplikaci. Statické odkazy na prostředky na klíče, o kterých je známo, že existují pouze v tématech nebo jako systémové prostředky, se však nedoporučují, protože tyto odkazy nejsou znovu vyhodnoceny, pokud je motiv změněn uživatelem v reálném čase. Dynamický odkaz na prostředky je spolehlivější při požadavku na motiv nebo systémové prostředky. Výjimkou je, když samotný prvek motivu požaduje jiný prostředek. Tyto odkazy by měly být odkazy na statické prostředky, z důvodů uvedených výše.

Chování výjimky, pokud není nalezen odkaz na statický prostředek se liší. Pokud byl prostředek odložen, dojde k výjimce za běhu. Pokud zdroj nebyl odložen, dojde k výjimce v době načítání.

## <a name="dynamic-resources"></a>Dynamické zdroje

Dynamické zdroje fungují nejlépe, když:

- Hodnota prostředku, včetně systémových prostředků nebo prostředků, které jsou jinak uživateli settable, závisí na podmínkách, které nejsou známy až do běhu. Můžete například vytvořit hodnoty nastavení, které odkazují na <xref:System.Windows.SystemColors> <xref:System.Windows.SystemFonts>vlastnosti <xref:System.Windows.SystemParameters>systému jako vystavené rozhraním , , nebo . Tyto hodnoty jsou skutečně dynamické, protože nakonec pocházejí z runtime prostředí uživatele a operačního systému. Můžete mít také motivy na úrovni aplikace, které se mohou změnit, kde musí změna zachytit také přístup prostředků na úrovni stránky.

- Vytváříte nebo odkazujete na styly motivů pro vlastní ovládací prvek.

- Máte v úmyslu upravit <xref:System.Windows.ResourceDictionary> obsah během životnosti aplikace.

- Máte složitou strukturu prostředků, která má vzájemné závislosti, kde může být vyžadován odkaz dopředné. Statické odkazy na prostředky nepodporují odkazy vpřed, ale odkazy na dynamické prostředky je podporují, protože prostředek nemusí být vyhodnocován až do běhu za běhu a odkazy dopředné proto nejsou relevantní koncept.

- Odkazujete na prostředek, který je velký z hlediska kompilace nebo pracovní sady, a prostředek nemusí být použit okamžitě při načtení stránky. Statické odkazy na prostředky se vždy načítají z XAML při načtení stránky. Odkaz na dynamický prostředek se však nenačte, dokud není použit.

- Vytváříte styl, ve kterém mohou hodnoty nastavení pocházet z jiných hodnot, které jsou ovlivněny motivy nebo jinými uživatelskými nastaveními.

- Prostředky aplikujete na prvky, které mohou být reparented v logickém stromu během životnosti aplikace. Změna nadřazeného objektu také potenciálně změní obor vyhledávání prostředků, takže pokud chcete, aby byl prostředek pro znovunadřazený prvek znovu vyhodnocen na základě nového oboru, vždy použijte odkaz na dynamický prostředek.

### <a name="dynamic-resource-lookup-behavior"></a>Chování dynamického vyhledávání prostředků

Chování vyhledávání prostředků pro odkaz na dynamický prostředek paralely chování <xref:System.Windows.FrameworkElement.FindResource%2A> vyhledávání <xref:System.Windows.FrameworkElement.SetResourceReference%2A>v kódu, pokud voláte nebo :

01. Vyhledávání zkontroluje požadovaný klíč v rámci slovníku prostředků definovaného elementem, který nastavuje vlastnost:

    - Pokud prvek definuje <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> prvek má svůj <xref:System.Windows.Style.Resources> slovník zaškrtnuto.

    - Pokud prvek definuje <xref:System.Windows.Controls.Control.Template%2A> vlastnost, <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> je zkontrolován slovník prvku.

01. Vyhledávání prochází logický strom směrem nahoru k nadřazenému prvku a jeho slovníku prostředků. Tento proces pokračuje, dokud není dosaženo kořenového prvku.

01. Prostředky aplikace jsou kontrolovány. Prostředky aplikace jsou prostředky v rámci slovníku <xref:System.Windows.Application> prostředků, které jsou definovány objektem pro vaši aplikaci WPF.

01. Slovník prostředků motivu je zkontrolován pro aktuálně aktivní motiv. Pokud se motiv změní za běhu, hodnota se přehodnotí.

01. Systémové prostředky jsou kontrolovány.

Chování výjimky (pokud existuje) se liší:

- Pokud byl prostředek požadován <xref:System.Windows.FrameworkElement.FindResource%2A> voláním a nebyl nalezen, je vyvolána výjimka.

- Pokud byl prostředek požadován <xref:System.Windows.FrameworkElement.TryFindResource%2A> voláním a nebyl nalezen, není vyvolána žádná `null`výjimka a vrácená hodnota je . Pokud nastavená vlastnost nepřijímá `null`, pak je stále možné, že bude vyvolána hlubší výjimka, v závislosti na jednotlivé vlastnosti, která je nastavena.

- Pokud byl prostředek požadován odkazem na dynamický prostředek v xaml a nebyl nalezen, závisí chování na systému obecných vlastností. Obecné chování je, jako kdyby došlo k žádné operaci nastavení vlastnosti došlo na úrovni, kde existuje prostředek. Pokud se například pokusíte nastavit pozadí na jednotlivém prvku tlačítka pomocí prostředku, který nelze vyhodnotit, nebude možné vyčíslit žádné výsledky sady hodnot, ale efektivní hodnota může stále pocházet od ostatních účastníků systému vlastností a priority hodnoty. Hodnota pozadí může například stále pocházet z místně definovaného stylu tlačítka nebo ze stylu motivu. U vlastností, které nejsou definovány styly motivu, může efektivní hodnota po neúspěšném vyhodnocení prostředků pocházet z výchozí hodnoty v metadatech vlastnosti.

### <a name="restrictions"></a>Omezení

Dynamické odkazy na prostředky mají některá významná omezení. Musí být splněna alespoň jedna z následujících podmínek:

- Nastavená vlastnost musí být vlastnost <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement>na nebo . Tato vlastnost musí být <xref:System.Windows.DependencyProperty>podpořena .

- Odkaz je pro hodnotu `StyleSetter`v rámci .

- Vlastnost, která je nastavena, <xref:System.Windows.Freezable> musí být vlastnost, která <xref:System.Windows.FrameworkElement> je <xref:System.Windows.FrameworkContentElement> poskytována <xref:System.Windows.Setter> jako hodnota nebo vlastnost nebo hodnota.

Vzhledem k tomu, <xref:System.Windows.DependencyProperty> že <xref:System.Windows.Freezable> nastavená vlastnost musí být vlastnost nebo vlastnost, většina změn vlastností se může šířit do uj, protože změna vlastnosti (změněná hodnota dynamického prostředku) je potvrzena systémem vlastností. Většina ovládacích prvků obsahuje logiku, <xref:System.Windows.DependencyProperty> která vynutí jiné rozložení ovládacího prvku, pokud změny a tato vlastnost může ovlivnit rozložení. Však ne všechny vlastnosti, které mají [DynamicResource Markup Extension](../../framework/wpf/advanced/dynamicresource-markup-extension.md) jako jejich hodnota je zaručeno, že poskytují aktualizace v reálném čase v ui. Tato funkce se stále může lišit v závislosti na vlastnosti, stejně jako v závislosti na typu, který vlastní vlastnost, nebo dokonce logické struktury vaší aplikace.

## <a name="styles-datatemplates-and-implicit-keys"></a>Styly, šablony dat a implicitní klíče

Přestože všechny <xref:System.Windows.ResourceDictionary> položky v musí mít klíč, to neznamená, `x:Key`že všechny prostředky musí mít explicitní . Několik typů objektů podporuje implicitní klíč, pokud je definován jako prostředek, kde je hodnota klíče vázána na hodnotu jiné vlastnosti. Tento typ klíče se označuje jako implicitní `x:Key` klíč, zatímco atribut je explicitní klíč. Libovolný implicitní klíč můžete přepsat zadáním explicitního klíče.

Jeden důležitý scénář pro prostředky <xref:System.Windows.Style>je při definování . Ve skutečnosti <xref:System.Windows.Style> a je téměř vždy definovánjako položka ve slovníku prostředků, protože styly jsou ze své podstaty určeny pro opakované použití. Další informace o stylech naleznete v [tématu Styling a Templating](styles-templates-overview.md).

Styly pro ovládací prvky lze vytvořit s implicitním klíčem a odkazovat na ně. Styly motivů, které definují výchozí vzhled ovládacího prvku, spoléhají na tento implicitní klíč. Z hlediska vyžádání je implicitní klíč <xref:System.Type> samotného ovládacího prvku. Z hlediska definování prostředků implicitní klíč je <xref:System.Windows.Style.TargetType%2A> stylu. Pokud tedy vytváříte motivy pro vlastní ovládací prvky nebo vytváříte styly, které interagují <xref:System.Windows.Style>s existujícími styly motivů, není nutné pro to zadávat [direktivu x:Key](../xaml-services/xkey-directive.md) . A pokud chcete použít tematou styly, nemusíte vůbec zadávat žádný styl. Například následující definice stylu funguje, <xref:System.Windows.Style> i když se zdá, že prostředek nemá klíč:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Tento styl opravdu má klíč: `typeof(System.Windows.Controls.Button)`implicitní klíč . Ve značkách můžete zadat <xref:System.Windows.Style.TargetType%2A> přímo jako název typu (nebo můžete volitelně použít [{x:Type...}](../xaml-services/xtype-markup-extension.md) vrátíte <xref:System.Type>.

Prostřednictvím výchozí chod mechanismů motivu používaný wpf, tento styl se <xref:System.Windows.Controls.Button> použije jako runtime <xref:System.Windows.Controls.Button> styl na stránce, <xref:System.Windows.FrameworkElement.Style%2A> i když sám se nepokouší určit jeho vlastnost nebo konkrétní prostředek odkaz na styl. Styl definovaný na stránce se nachází dříve ve vyhledávací sekvenci než styl slovníku motivů pomocí stejného klíče, jako má styl slovníku motivů. Můžete pouze `<Button>Hello</Button>` určit kdekoli na stránce a styl, který jste definovali s <xref:System.Windows.Style.TargetType%2A> by `Button` se vztahují na toto tlačítko. Pokud chcete, můžete stále explicitně klíč styl se <xref:System.Windows.Style.TargetType%2A> stejnou hodnotou typu jako pro přehlednost ve značky, ale to je volitelné.

Implicitní klíče pro styly neplatí na ovládací prvek, pokud <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> je `true`. (Všimněte <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> si také, že může být nastavena jako součást nativní chování pro třídu ovládacího prvku, nikoli explicitně na instanci ovládacího prvku.) Také pro podporu implicitní klíče pro scénáře odvozené třídy, musí ovládací prvek přepsat <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (všechny existující ovládací prvky poskytované jako součást WPF zahrnují toto přepsání). Další informace o stylech, motivech a návrhu ovládacích prvků naleznete v [tématu Pokyny pro návrh stylovatelných ovládacích prvků](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>má také implicitní klíč. Implicitní klíč <xref:System.Windows.DataTemplate> pro <xref:System.Windows.DataTemplate.DataType%2A> a je hodnota vlastnosti. <xref:System.Windows.DataTemplate.DataType%2A>lze také zadat jako název typu, nikoli explicitně pomocí [{x:Type...}](../xaml-services/xtype-markup-extension.md). Podrobnosti naleznete [v tématu Přehled datových šablon](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.ResourceDictionary>
- [Prostředky aplikace](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Zdroje a kód](../../framework/wpf/advanced/resources-and-code.md)
- [Definování a odkaz ování zdroje](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Přehled správy aplikací](../../framework/wpf/app-development/application-management-overview.md)
- [x:Rozšíření značek typu](../xaml-services/xtype-markup-extension.md)
- [Rozšíření značek StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [Rozšíření značek DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
