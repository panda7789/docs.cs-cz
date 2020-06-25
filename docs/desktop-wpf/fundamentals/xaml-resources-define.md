---
title: Definování prostředků XAML
description: Přečtěte si o prostředcích XAML v WPF pro .NET Core. Seznamte se s typy prostředků XAML a Naučte se, jak definovat prostředky XAML.
author: adegeo
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: f8eaf3fd931aa6804b0b9a9c19c6bcc042678ebf
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325708"
---
# <a name="overview-of-xaml-resources"></a>Přehled prostředků XAML

Prostředek je objekt, který lze znovu použít na různých místech aplikace. Mezi příklady prostředků patří štětce a styly. Tento přehled popisuje, jak používat prostředky v jazyk Extensible Application Markup Language (XAML) (XAML). Můžete také vytvořit prostředky a přistupovat k nim pomocí kódu.

> [!NOTE]
> Prostředky XAML popsané v tomto článku se liší od *prostředků aplikace* , které jsou obecně soubory přidané do aplikace, jako je například obsah, data nebo vložené soubory.

<!-- TODO: File redirect from docs\framework\wpf\advanced\xaml-resources.md -->

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="using-resources-in-xaml"></a>Používání prostředků v jazyce XAML

Následující příklad definuje <xref:System.Windows.Media.SolidColorBrush> jako prostředek v kořenovém elementu stránky. Příklad pak odkazuje na prostředek a použije ho k nastavení vlastností několika podřízených elementů, včetně <xref:System.Windows.Shapes.Ellipse> , a <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.Button> .

[!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]

Každý element na úrovni architektury ( <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> ) má <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost, která je <xref:System.Windows.ResourceDictionary> typu, který obsahuje definované prostředky. Můžete definovat prostředky pro libovolný element, jako je například <xref:System.Windows.Controls.Button> . Prostředky jsou však nejčastěji definovány na kořenovém prvku, který je <xref:System.Windows.Controls.Page> v příkladu.

Každý prostředek ve slovníku prostředků musí mít jedinečný klíč. Při definování prostředků v kódu přiřadíte jedinečný klíč prostřednictvím [direktivy x:Key –](../xaml-services/xkey-directive.md). Klíč je obvykle řetězec. můžete ji však také nastavit na jiné typy objektů pomocí příslušných rozšíření značek. Neřetězcové klíče pro prostředky jsou používány některými oblastmi funkcí v technologii WPF, zejména pro styly, prostředky komponent a pro datové styly.

Můžete použít definovaný prostředek se syntaxí rozšíření značek prostředku, která určuje název prostředku. Například použijte prostředek jako hodnotu vlastnosti v jiném elementu.

[!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]

V předchozím příkladu, když zavaděč XAML zpracovává hodnotu `{StaticResource MyBrush}` pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost na <xref:System.Windows.Controls.Button> , logika vyhledávání prostředků nejprve zkontroluje slovník prostředků pro daný <xref:System.Windows.Controls.Button> element. Pokud nemá <xref:System.Windows.Controls.Button> definici klíče prostředků `MyBrush` (v tomto příkladu to není; jeho kolekce prostředků je prázdná), vyhledávání provede další kontrolu nadřazeného elementu <xref:System.Windows.Controls.Button> , který je <xref:System.Windows.Controls.Page> . Definujete-li prostředek na <xref:System.Windows.Controls.Page> kořenovém prvku, budou mít k němu přístup všechny prvky v logickém stromu <xref:System.Windows.Controls.Page> . A můžete použít stejný prostředek pro nastavení hodnoty libovolné vlastnosti, která bude přijímat stejný typ, jaký prostředek představuje. V předchozím příkladu stejný `MyBrush` prostředek nastaví dvě různé vlastnosti: <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> a, a a <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> .

## <a name="static-and-dynamic-resources"></a>Statické a dynamické prostředky

Prostředek se může odkazovat buď na statický, nebo na dynamický. Odkazy se vytvářejí buď pomocí [rozšíření značek StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) , nebo pomocí [rozšíření značek DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md). Rozšíření značek je funkce jazyka XAML, která umožňuje zadat odkaz na objekt pomocí rozšíření značek, který zpracovává řetězec atributu a vrátí objekt do zavaděče XAML. Další informace o chování rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).

Použijete-li rozšíření značek, obvykle zadáte jeden nebo více parametrů ve formě řetězce, které jsou zpracovány konkrétní příponou označení. [Přípona značek StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md) zpracuje klíč tím, že vyhledá hodnotu pro tento klíč ve všech dostupných slovníkech prostředků. Zpracování probíhá během načítání, což je, když proces načítání potřebuje přiřadit hodnotu vlastnosti. [Rozšíření značek DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) místo toho zpracovává klíč tím, že vytvoří výraz a tento výraz zůstane nevyhodnocený, dokud se aplikace nespustí, přičemž v takovém případě je výraz vyhodnocen a poskytuje hodnotu.

Při odkazování na prostředek mohou následující okolnosti ovlivnit, zda používáte statický odkaz na prostředek nebo dynamický odkaz na prostředek:

- Při určování celkového návrhu způsobu vytváření prostředků pro vaši aplikaci (na stránce, v aplikaci, ve volném XAML nebo v sestavení pouze pro prostředky) Vezměte v úvahu následující skutečnosti:

- Funkce aplikace Aktualizujete prostředky v rámci požadavků vaší aplikace v reálném čase?
- Příslušné chování vyhledávání tohoto typu odkazu na prostředek.
- Konkrétní vlastnost nebo typ prostředku a nativní chování těchto typů.

## <a name="static-resources"></a>Statické prostředky

Odkazy statických prostředků fungují nejlépe v následujících případech:

- Návrh vaší aplikace soustředí většinu svých prostředků na stránky nebo slovníky prostředků na úrovni aplikace. Statické odkazy na prostředky nejsou znovu vyhodnoceny na základě chování modulu runtime, jako je například opětovné načtení stránky. Takže může vycházet z nějakého zvýšení výkonu a vyhnout se tak velkému počtu dynamických odkazů na prostředky, pokud to není nutné na základě návrhu prostředků a aplikací.

- Nastavujete hodnotu vlastnosti, která není na <xref:System.Windows.DependencyObject> nebo <xref:System.Windows.Freezable> .

- Vytváříte slovník prostředků, který se zkompiluje do knihovny DLL a zabalí se jako součást aplikace nebo se sdílí mezi aplikacemi.

- Vytváříte motiv pro vlastní ovládací prvek a definujete prostředky, které se používají v rámci motivů. V tomto případě obvykle nechcete, aby bylo vyhledávání v odkazu dynamického prostředku. místo toho chcete, aby bylo chování odkazu statického prostředku tak, aby bylo vyhledávání předvídatelné a samoně součástí motivu. S odkazem na dynamický prostředek, dokonce i odkaz v rámci motivu je ponechán nehodnocený, dokud nespustíte rutinu run-time. a existuje možnost, že když je motiv použit, některé lokální prvky předefinují klíč, na který se váš motiv pokouší odkazovat, a místní prvek bude před samotným motivem ve vyhledávání. Pokud k tomu dojde, váš motiv se nebude chovat podle očekávání.

- Prostředky se používají k nastavení velkého počtu vlastností závislosti. Vlastnosti závislosti mají efektivní ukládání hodnot do mezipaměti, které jsou povolené systémem vlastností, takže pokud zadáte hodnotu pro vlastnost závislosti, kterou je možné vyhodnotit během načítání, vlastnost Dependency nemusí kontrolovat znovu vyhodnocený výraz a může vrátit poslední efektivní hodnotu. Tato technika může být výhodou výkonu.

- Chcete změnit základní prostředek pro všechny uživatele nebo chcete zachovat samostatné zapisovatelné instance pro každého příjemce pomocí [atributu x:Shared –](../xaml-services/xshared-attribute.md).

### <a name="static-resource-lookup-behavior"></a>Chování vyhledávání statických prostředků

Následující článek popisuje proces vyhledávání, který se automaticky stane, když na statický prostředek odkazuje vlastnost nebo element:

01. Proces vyhledávání kontroluje požadovaný klíč v rámci slovníku prostředků definovaného prvkem, který nastavuje vlastnost.

01. Proces vyhledávání pak projde logický strom směrem nahoru k nadřazenému elementu a jeho slovníku prostředků. Tento proces pokračuje, dokud není dosaženo kořenového prvku.

01. Prostředky aplikace jsou zkontrolovány. Prostředky aplikací jsou tyto prostředky v rámci slovníku prostředků, který je definovaný <xref:System.Windows.Application> objektem pro vaši aplikaci WPF.

Statické odkazy na prostředky v rámci slovníku prostředků musí odkazovat na prostředek, který již byl definován lexikální před odkazem na prostředek. Odkazy na směrování nelze vyřešit pomocí odkazu na statický prostředek. Z tohoto důvodu je třeba navrhnout strukturu slovníku prostředků tak, aby prostředky byly definovány na začátku každého příslušného slovníku prostředků nebo téměř na nich.

Statické vyhledávání prostředků může být rozšířeno na motivy nebo do systémových prostředků, ale toto vyhledávání je podporováno pouze proto, že zavaděč XAML odloží požadavek. Odložení je nezbytné, aby byl motiv modulu runtime v okamžiku, kdy se stránka správně načte, v aplikaci správně načítat. Nicméně statické odkazy na klíče, které jsou známy pouze v motivech nebo jako systémové prostředky, nejsou doporučovány, protože tyto odkazy nejsou znovu vyhodnoceny, pokud je motiv změněn uživatelem v reálném čase. Odkaz na dynamický prostředek je spolehlivější, když požádáte o motiv nebo systémové prostředky. Výjimkou je, když prvek motivu sám požaduje jiný prostředek. Tyto odkazy by měly být statickými odkazy na prostředky z výše zmíněných důvodů.

Chování výjimky, pokud není nalezen statický odkaz na prostředek, se liší. Pokud byl prostředek odložen, dojde k výjimce za běhu. Pokud prostředek nebyl odložen, dojde k výjimce v době načítání.

## <a name="dynamic-resources"></a>Dynamické prostředky

Dynamické prostředky fungují nejlépe v těchto případech:

- Hodnota prostředku, včetně systémových prostředků nebo prostředků, které jinak nastaví uživatel, závisí na podmínkách, které nejsou známy až do doby běhu. Můžete například vytvořit hodnoty Setter, které odkazují na vlastnosti systému, které jsou zpřístupněny pomocí <xref:System.Windows.SystemColors> , <xref:System.Windows.SystemFonts> nebo <xref:System.Windows.SystemParameters> . Tyto hodnoty jsou skutečně dynamické, protože nakonec pocházejí z běhového prostředí uživatele a operačního systému. Můžete mít také motivy na úrovni aplikace, které mohou být změněny, kde přístup k prostředkům na úrovni stránky musí také zachytit změnu.

- Vytváříte nebo odkazujete na styly motivů pro vlastní ovládací prvek.

- Máte v úmyslu upravit obsah <xref:System.Windows.ResourceDictionary> během životnosti aplikace.

- Máte složitou strukturu prostředků, která má vzájemné závislosti, kde se může vyžadovat dopředný odkaz. Statické odkazy na prostředky nepodporují dopředné odkazy, ale dynamické odkazy na prostředky je podporují, protože prostředek není nutné vyhodnotit do doby, než je modul runtime, a předávací odkazy nejsou proto relevantní koncept.

- Odkazujete na prostředek, který je velký z perspektivy kompilace nebo pracovní sady, a prostředek se nemusí použít ihned při načtení stránky. Statické odkazy na prostředky se při načtení stránky vždy načítají z kódu XAML. Dynamický odkaz na prostředek se ale nenačte, dokud se nepoužije.

- Vytváříte styl, ve kterém mohou být hodnoty setter z jiných hodnot, které jsou ovlivněny motivy nebo jinými uživatelskými nastaveními.

- Prostředky se aplikují na prvky, které můžou být v logickém stromu během životnosti aplikace znovu nadřazené. Změna nadřazené položky také potenciálně změní rozsah vyhledávání prostředků, takže pokud chcete, aby byl prostředek pro předaný element znovu vyhodnocen v závislosti na novém oboru, vždy použijte dynamický odkaz na prostředek.

### <a name="dynamic-resource-lookup-behavior"></a>Chování při hledání dynamického prostředku

Chování vyhledávání prostředků pro odkaz na dynamický prostředek paralelně vytvoří chování vyhledávání v kódu, pokud voláte <xref:System.Windows.FrameworkElement.FindResource%2A> nebo <xref:System.Windows.FrameworkElement.SetResourceReference%2A> :

01. Vyhledávání vyhledá požadovaný klíč v rámci slovníku prostředků definovaného prvkem, který nastavuje vlastnost:

    - Pokud element definuje <xref:System.Windows.FrameworkElement.Style%2A> vlastnost, <xref:System.Windows.FrameworkElement.Style?displayProperty=fullName> element má svůj <xref:System.Windows.Style.Resources> slovník zaškrtnuto.

    - Pokud element definuje <xref:System.Windows.Controls.Control.Template%2A> vlastnost, <xref:System.Windows.FrameworkTemplate.Resources?displayProperty=fullName> je zaškrtnut slovník elementu.

01. Vyhledávání projde logický strom směrem nahoru k nadřazenému prvku a jeho slovníku prostředků. Tento proces pokračuje, dokud není dosaženo kořenového prvku.

01. Prostředky aplikace jsou zkontrolovány. Prostředky aplikací jsou tyto prostředky v rámci slovníku prostředků, které jsou definovány <xref:System.Windows.Application> objektem pro vaši aplikaci WPF.

01. Slovník prostředků motivu je kontrolován pro aktuálně aktivní motiv. Pokud se motiv změní za běhu, hodnota se znovu vyhodnotí.

01. Jsou zaškrtnuté systémové prostředky.

Chování výjimky (pokud existuje) se liší:

- Pokud byl prostředek vyžádán <xref:System.Windows.FrameworkElement.FindResource%2A> voláním a nebyl nalezen, je vyvolána výjimka.

- Pokud byl prostředek vyžádán <xref:System.Windows.FrameworkElement.TryFindResource%2A> voláním a nebyl nalezen, není vyvolána žádná výjimka a vrácená hodnota je `null` . Pokud vlastnost nastavená nepřijímá `null` , je stále možné, že bude vyvolána hlubší výjimka v závislosti na nastavené individuální vlastnosti.

- Pokud byl prostředek vyžádán odkazem dynamického prostředku v jazyce XAML a nebyl nalezen, bude chování záviset na obecném systému vlastností. Obecné chování je, jako kdyby na úrovni, kde existuje prostředek, nedošlo k žádné operaci nastavení vlastnosti. Například pokud se pokusíte nastavit pozadí na jednotlivé prvky tlačítka pomocí prostředku, který nebylo možné vyhodnotit, pak se nenastaví žádná hodnota, ale efektivní hodnota může být z jiných účastníků v rámci nastavení systému vlastností a hodnoty. Hodnota pozadí může být například stále z lokálně definovaného stylu tlačítka nebo ze stylu motivu. Pro vlastnosti, které nejsou definovány styly motivů, může platit efektivní hodnota po neúspěšném vyhodnocení prostředku z výchozí hodnoty v metadatech vlastností.

### <a name="restrictions"></a>Omezení

Odkazy na dynamické prostředky mají určitá významná omezení. Alespoň jedna z následujících podmínek musí být pravdivá:

- Nastavená vlastnost musí být vlastnost v <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> . Tato vlastnost musí být zálohována pomocí <xref:System.Windows.DependencyProperty> .

- Odkaz je určen pro hodnotu v rámci `StyleSetter` .

- Vlastnost nastavená musí být vlastnost v <xref:System.Windows.Freezable> , která je k dispozici jako hodnota buď <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> vlastnosti, nebo nebo <xref:System.Windows.Setter> hodnoty.

Vzhledem k tomu, že nastavená vlastnost musí být <xref:System.Windows.DependencyProperty> <xref:System.Windows.Freezable> vlastnost nebo, může se většina změn vlastností šířit do uživatelského rozhraní, protože Změna vlastnosti (změněná hodnota dynamického prostředku) je potvrzena systémem vlastností. Většina ovládacích prvků zahrnuje logiku, která vynutí jiné rozložení ovládacího prvku, pokud <xref:System.Windows.DependencyProperty> změny a tato vlastnost mohou ovlivnit rozložení. Nicméně ne všechny vlastnosti, které mají [rozšíření značek DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md) jako jejich hodnota, jsou zaručeny pro poskytování aktualizací v reálném čase v uživatelském rozhraní. Tato funkce se pořád může lišit v závislosti na vlastnosti, a to v závislosti na typu, který vlastní vlastnost, nebo dokonce na logické struktuře vaší aplikace.

## <a name="styles-datatemplates-and-implicit-keys"></a>Styly, šablony a implicitní klíče

I když všechny položky v <xref:System.Windows.ResourceDictionary> musí mít klíč, to neznamená, že všechny prostředky musí mít explicitní `x:Key` . Několik typů objektů podporuje implicitní klíč, pokud je definován jako prostředek, kde hodnota klíče je svázána s hodnotou jiné vlastnosti. Tento typ klíče je známý jako implicitní klíč, zatímco `x:Key` atribut je explicitní klíč. Můžete přepsat libovolný implicitní klíč zadáním explicitního klíče.

Jeden z důležitých scénářů pro prostředky je při definování <xref:System.Windows.Style> . Ve skutečnosti <xref:System.Windows.Style> je téměř vždy definováno jako položka ve slovníku prostředků, protože styly jsou podstatně určeny k opakovanému použití. Další informace o stylech naleznete v tématu [stylování and šablonování](styles-templates-overview.md).

Styly pro ovládací prvky mohou být vytvořeny pomocí a odkazovány pomocí implicitního klíče. Styly motivů, které definují výchozí vzhled ovládacího prvku, spoléhají na tento implicitní klíč. Z hlediska vyžádání je implicitní klíč <xref:System.Type> samotného ovládacího prvku. Z hlediska definování prostředků je implicitní klíč ve <xref:System.Windows.Style.TargetType%2A> stylu. Proto pokud vytváříte motivy pro vlastní ovládací prvky nebo vytváříte styly, které komunikují se stávajícími styly motivů, není pro ni nutné zadávat [direktivu x:Key –](../xaml-services/xkey-directive.md) <xref:System.Windows.Style> . A pokud chcete použít styly motivů, nemusíte vůbec zadávat žádný styl. Následující definice stylu například funguje, i když se zdá, že <xref:System.Windows.Style> prostředek nemá klíč:

[!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]

Tento styl má ve skutečnosti klíč: implicitní klíč `typeof(System.Windows.Controls.Button)` . V kódu můžete zadat <xref:System.Windows.Style.TargetType%2A> přímo jako název typu (případně můžete použít [{x:Type...}](../xaml-services/xtype-markup-extension.md) ). pro vrácení <xref:System.Type> .

Pomocí výchozího mechanismu stylu motivu používaného WPF je tento styl použit jako styl modulu runtime <xref:System.Windows.Controls.Button> na stránce, i když se <xref:System.Windows.Controls.Button> sám o sobě nepokusí zadat jeho <xref:System.Windows.FrameworkElement.Style%2A> vlastnost nebo konkrétní odkaz na prostředek na styl. Váš styl definovaný na stránce se nachází dříve v sekvenci vyhledávání než styl slovníku motivu pomocí stejného klíče, který má styl slovníku motivů. Mohli byste jenom zadat `<Button>Hello</Button>` kamkoli na stránce a styl, který jste definovali, <xref:System.Windows.Style.TargetType%2A> se `Button` použije pro toto tlačítko. Pokud chcete, můžete stále explicitně klíčovat styl se stejnou hodnotou typu, která <xref:System.Windows.Style.TargetType%2A> je pro přehlednost v kódu, ale volitelná.

Implicitní klíče pro styly neplatí pro ovládací prvek, pokud <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> je `true` . (Všimněte si také, že <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> může být nastaveno jako součást nativního chování pro třídu ovládacího prvku, nikoli explicitně na instanci ovládacího prvku.) Aby bylo možné podporovat implicitní klíče pro odvozené třídy, ovládací prvek musí přepsat <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (všechny existující ovládací prvky, které jsou součástí WPF jako součást tohoto přepsání). Další informace o stylech, motivech a návrhu ovládacích prvků naleznete v tématu [pokyny pro návrh ovládacích ovládacích prvků](../../framework/wpf/controls/guidelines-for-designing-stylable-controls.md).

<xref:System.Windows.DataTemplate>má také implicitní klíč. Implicitní klíč pro <xref:System.Windows.DataTemplate> je <xref:System.Windows.DataTemplate.DataType%2A> hodnota vlastnosti. <xref:System.Windows.DataTemplate.DataType%2A>lze také zadat jako název typu místo explicitního použití [{x:Type...}](../xaml-services/xtype-markup-extension.md). Podrobnosti najdete v tématu [Přehled šablonování dat](../../framework/wpf/data/data-templating-overview.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.ResourceDictionary>
- [Prostředky aplikace](../../framework/wpf/advanced/optimizing-performance-application-resources.md)
- [Prostředky a kód](../../framework/wpf/advanced/resources-and-code.md)
- [Definování prostředku a odkazování na něj](../../framework/wpf/advanced/how-to-define-and-reference-a-resource.md)
- [Přehled správy aplikací](../../framework/wpf/app-development/application-management-overview.md)
- [rozšíření značek x:Type](../xaml-services/xtype-markup-extension.md)
- [Rozšíření značek StaticResource](../../framework/wpf/advanced/staticresource-markup-extension.md)
- [Rozšíření značek DynamicResource](../../framework/wpf/advanced/dynamicresource-markup-extension.md)
