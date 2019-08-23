---
title: Zdroje XAML
ms.date: 03/30/2017
helpviewer_keywords:
- reusing resources [WPF]
- resources [WPF], reusing
- reusing commonly defined objects [WPF]
- XAML [WPF], reusing resources
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
ms.openlocfilehash: 738a4f397b1677b867126c7bb439b027f951baa0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958820"
---
# <a name="xaml-resources"></a>Zdroje XAML
Prostředek je objekt, který lze znovu použít na různých místech aplikace. Mezi příklady prostředků patří štětce a styly. Tento přehled popisuje, jak používat prostředky v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nástroji. Můžete také vytvořit a přistupovat k prostředkům pomocí kódu nebo mezi kódem a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Další informace najdete v tématu [zdroje a kód](resources-and-code.md).  
  
> [!NOTE]
> Soubory prostředků popsané v tomto tématu se liší od souborů prostředků popsaných v tématu [prostředek aplikace WPF, obsah a datové soubory](../app-development/wpf-application-resource-content-and-data-files.md) a jiné než vložené nebo propojené prostředky popsané v tématu [Správa prostředků aplikace (.NET). ](/visualstudio/ide/managing-application-resources-dotnet).  

<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Používání prostředků v jazyce XAML  
 Následující příklad definuje <xref:System.Windows.Media.SolidColorBrush> jako prostředek v kořenovém elementu stránky. Příklad pak odkazuje na prostředek a použije ho k nastavení vlastností několika podřízených elementů, včetně <xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Controls.TextBlock>, a a <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[FEResourceSH_snip#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Každý element na úrovni architektury (<xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement>) má <xref:System.Windows.FrameworkElement.Resources%2A> vlastnost, což je <xref:System.Windows.ResourceDictionary>vlastnost, která obsahuje prostředky (jako), kterou definuje prostředek. Můžete definovat prostředky pro libovolný element. Prostředky jsou však nejčastěji definovány na kořenovém prvku, který je <xref:System.Windows.Controls.Page> v příkladu.  
  
 Každý prostředek ve slovníku prostředků musí mít jedinečný klíč. Při definování prostředků v kódu přiřadíte jedinečný klíč prostřednictvím [direktivy x:Key –](../../xaml-services/x-key-directive.md). Klíč je obvykle řetězec. můžete ji však také nastavit na jiné typy objektů pomocí příslušných rozšíření značek. Neřetězcové klíče pro prostředky jsou používány některými oblastmi funkcí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]v nástroji, zejména pro styly, prostředky komponent a stylování dat.  
  
 Po definování prostředku můžete odkazovat na prostředek, který se má použít pro hodnotu vlastnosti pomocí syntaxe rozšíření označení prostředku, která určuje název klíče, například:  
  
 [!code-xaml[FEResourceSH_snip#KeyNameUsage](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 V předchozím příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , když zavaděč zpracovává hodnotu `{StaticResource MyBrush}` pro <xref:System.Windows.Controls.Control.Background%2A> vlastnost na <xref:System.Windows.Controls.Button>, logika vyhledávání prostředků nejprve zkontroluje slovník prostředků pro daný <xref:System.Windows.Controls.Button> element. Pokud <xref:System.Windows.Controls.Button> nemá definici klíče `MyBrush` prostředku (nejedná se o jeho kolekci prostředků je prázdné), vyhledávání provede další <xref:System.Windows.Controls.Button>kontrolu nadřazeného elementu, který je <xref:System.Windows.Controls.Page>. Proto při definování prostředku v <xref:System.Windows.Controls.Page> kořenovém elementu, ke kterému <xref:System.Windows.Controls.Page> mají přístup všechny prvky v logickém stromu, a můžete znovu použít stejný prostředek pro nastavení hodnoty <xref:System.Type> libovolné vlastnosti, která přijímá daný prostředek. roce. `MyBrush` V předchozím příkladu stejný prostředek nastaví dvě různé vlastnosti <xref:System.Windows.Controls.Control.Background%2A> : <xref:System.Windows.Controls.Button>a, a a <xref:System.Windows.Shapes.Shape.Fill%2A>. <xref:System.Windows.Shapes.Rectangle>  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Statické a dynamické prostředky  
 Prostředek se může odkazovat buď na statický prostředek, nebo na dynamický prostředek. To se provádí pomocí [rozšíření značek StaticResource](staticresource-markup-extension.md) nebo [rozšíření značek DynamicResource](dynamicresource-markup-extension.md). Rozšíření značek je funkce, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kde můžete zadat odkaz na objekt pomocí rozšíření značek, který zpracovává řetězec atributu a vrátí objekt [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do zavaděče. Další informace o chování rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 Použijete-li rozšíření značek, obvykle zadáte jeden nebo více parametrů ve formě řetězce, které jsou zpracovány pomocí konkrétní přípony označení, nikoli vyhodnoceny v kontextu nastavené vlastnosti. [Přípona značek StaticResource](staticresource-markup-extension.md) zpracuje klíč tím, že vyhledá hodnotu pro tento klíč ve všech dostupných slovníkech prostředků. K tomu dojde během načítání, což je bod v čase, kdy proces načítání potřebuje přiřadit hodnotu vlastnosti, která přebírá statický odkaz na prostředek. [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md) místo toho zpracovává klíč tím, že vytvoří výraz a tento výraz zůstane nevyhodnocený, dokud nebude aplikace skutečně spuštěna, kdy je výraz vyhodnocen a poskytuje hodnotu.  
  
 Při odkazování na prostředek mohou následující okolnosti ovlivnit, zda používáte statický odkaz na prostředek nebo dynamický odkaz na prostředek:  
  
- Celkový návrh způsobu vytváření prostředků pro vaši aplikaci (na stránce v aplikaci, v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]případě, že je v sestavení pouze pro prostředky).  
  
- Funkčnost aplikace: aktualizuje prostředky v reálném čase jako součást požadavků vaší aplikace?  
  
- Příslušné chování vyhledávání tohoto typu odkazu na prostředek.  
  
- Konkrétní vlastnost nebo typ prostředku a nativní chování těchto typů.  
  
### <a name="static-resources"></a>Statické prostředky  
 Odkazy statických prostředků fungují nejlépe v následujících případech:  
  
- Návrh vaší aplikace soustředí ze všech svých prostředků do slovníků prostředků na úrovni stránky nebo aplikace. Statické odkazy na prostředky nejsou znovu vyhodnoceny na základě chování modulu runtime, jako je například opětovné načtení stránky, a proto může docházet k vyzkoušení velkého počtu odkazů na dynamické prostředky, pokud nejsou pro váš prostředek nutné. návrh aplikace  
  
- Nastavujete hodnotu vlastnosti, která není na <xref:System.Windows.DependencyObject> <xref:System.Windows.Freezable>nebo.  
  
- Vytváříte slovník prostředků, který bude zkompilován do knihovny DLL a zabalen jako součást aplikace nebo sdílen mezi aplikacemi.  
  
- Vytváříte motiv pro vlastní ovládací prvek a definujete prostředky, které se používají v rámci motivů. V takovém případě nechcete, aby se nemuselo Hledat v dynamickém vyhledávání odkazů na prostředky, místo toho byste měli mít odkaz na statické prostředky, aby bylo vyhledávání předvídatelné a samoně součástí motivu. S dynamickým odkazem na prostředek, dokonce i odkaz v rámci motivu je nehodnocený až do doby běhu a existuje možnost, že když je motiv použit, některé místní prvky předefinují klíč, na který se váš motiv pokouší odkazovat, a místní prvek se zařadí před na samotný motiv ve vyhledávání. Pokud k tomu dojde, váš motiv se nebude chovat očekávaným způsobem.  
  
- Prostředky se používají k nastavení velkého počtu vlastností závislosti. Vlastnosti závislosti mají efektivní ukládání hodnot do mezipaměti, které jsou povolené systémem vlastností, takže pokud zadáte hodnotu pro vlastnost závislosti, kterou je možné vyhodnotit během načítání, vlastnost Dependency nemusí kontrolovat znovu vyhodnocený výraz a může vrátit Poslední efektivní hodnota. Tato technika může být výhodou výkonu.  
  
- Chcete změnit základní prostředek pro všechny uživatele nebo chcete zachovat samostatné zapisovatelné instance pro každého příjemce pomocí [atributu x:Shared –](../../xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Chování vyhledávání statických prostředků  
  
1. Proces vyhledávání kontroluje požadovaný klíč v rámci slovníku prostředků definovaného prvkem, který nastavuje vlastnost.  
  
2. Proces vyhledávání pak projde logický strom nahoru do nadřazeného prvku a jeho slovníku prostředků. To pokračuje, dokud není dosaženo kořenového prvku.  
  
3. V dalším kroku jsou zkontrolovány prostředky aplikace. Prostředky aplikace jsou tyto prostředky v rámci slovníku prostředků, které jsou definovány <xref:System.Windows.Application> objektem pro vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci.  
  
 Statické odkazy na prostředky v rámci slovníku prostředků musí odkazovat na prostředek, který již byl definován lexikální před odkazem na prostředek. Odkazy na směrování nelze vyřešit pomocí odkazu na statický prostředek. Z tohoto důvodu platí, že pokud používáte statické odkazy na prostředky, je nutné navrhnout strukturu slovníku prostředků tak, aby prostředky určené pro použití podle prostředků byly definovány na začátku každého příslušného slovníku prostředků nebo téměř na nich.  
  
 Statické vyhledávání prostředků může být rozšířeno na motivy nebo do systémových prostředků, ale to je podporováno pouze proto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , že zavaděč odloží požadavek. Odložení je nezbytné, aby byl motiv modulu runtime v okamžiku, kdy se stránka správně načte, v aplikaci správně načítat. Statické odkazy na prostředky, které jsou známy pouze v motivech nebo jako systémové prostředky, se však nedoporučují. Důvodem je, že tyto odkazy nejsou znovu vyhodnoceny, pokud je motiv změněn uživatelem v reálném čase. Odkaz na dynamický prostředek je spolehlivější, když požádáte o motiv nebo systémové prostředky. Výjimkou je, když prvek motivu sám požaduje jiný prostředek. Tyto odkazy by měly být statickými odkazy na prostředky z výše zmíněných důvodů.  
  
 Chování výjimky, pokud se nenalezne odkaz na statický prostředek, se liší. Pokud byl prostředek odložen, dojde k výjimce za běhu. Pokud prostředek nebyl odložen, dojde k výjimce v době načítání.  
  
### <a name="dynamic-resources"></a>Dynamické prostředky  
 Dynamické prostředky fungují nejlépe v následujících případech:  
  
- Hodnota prostředku závisí na podmínkách, které nejsou známy do modulu runtime. To zahrnuje systémové prostředky nebo prostředky, které jsou jinak nastavitelné uživatelem. Můžete například vytvořit hodnoty Setter, které odkazují na vlastnosti systému, které jsou vystaveny pomocí <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>nebo <xref:System.Windows.SystemParameters>. Tyto hodnoty jsou skutečně dynamické, protože nakonec pocházejí z běhového prostředí uživatele a operačního systému. Můžete mít také motivy na úrovni aplikace, které mohou být změněny, kde přístup k prostředkům na úrovni stránky musí také zachytit změnu.  
  
- Vytváříte nebo odkazujete na styly motivů pro vlastní ovládací prvek.  
  
- Máte v úmyslu upravit obsah <xref:System.Windows.ResourceDictionary> během životnosti aplikace.  
  
- Máte složitou strukturu prostředků, která má vzájemné závislosti, kde se může vyžadovat dopředný odkaz. Statické odkazy na prostředky nepodporují dopředné odkazy, ale dynamické odkazy na prostředky je podporují, protože prostředek není nutné vyhodnotit do doby, než je modul runtime, a předávací odkazy nejsou proto relevantní koncept.  
  
- Odkazujete na prostředek, který je zvláště velký z perspektivy kompilace nebo pracovní sady, a prostředek se nemusí použít ihned při načtení stránky. Statické odkazy na prostředky se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] při načtení stránky vždy načítají; dynamický odkaz na prostředek se ale nenačte, dokud se nepoužije.  
  
- Vytváříte styl, ve kterém mohou být hodnoty setter z jiných hodnot, které jsou ovlivněny motivy nebo jinými uživatelskými nastaveními.  
  
- Prostředky se aplikují na prvky, které mohou být v logickém stromu během životního cyklu aplikace znovu nadřazené. Změna nadřazené položky také potenciálně změní rozsah vyhledávání prostředků, takže pokud chcete, aby byl prostředek pro předaný element znovu vyhodnocen v závislosti na novém oboru, vždy použijte dynamický odkaz na prostředek.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Chování při hledání dynamického prostředku  
 Chování vyhledávání prostředků pro odkaz na dynamický prostředek paralelně vytvoří chování vyhledávání v kódu, pokud voláte <xref:System.Windows.FrameworkElement.FindResource%2A> nebo. <xref:System.Windows.FrameworkElement.SetResourceReference%2A>  
  
1. Proces vyhledávání kontroluje požadovaný klíč v rámci slovníku prostředků definovaného prvkem, který nastavuje vlastnost.  
  
    - Pokud element definuje <xref:System.Windows.FrameworkElement.Style%2A> vlastnost <xref:System.Windows.Style.Resources%2A> , slovník v rámci <xref:System.Windows.Style> je zaškrtnut.  
  
    - Pokud element definuje <xref:System.Windows.Controls.Control.Template%2A> vlastnost <xref:System.Windows.FrameworkTemplate.Resources%2A> , slovník v rámci <xref:System.Windows.FrameworkTemplate> je zaškrtnut.  
  
2. Proces vyhledávání pak projde logický strom nahoru do nadřazeného prvku a jeho slovníku prostředků. To pokračuje, dokud není dosaženo kořenového prvku.  
  
3. V dalším kroku jsou zkontrolovány prostředky aplikace. Prostředky aplikace jsou tyto prostředky v rámci slovníku prostředků, které jsou definovány <xref:System.Windows.Application> objektem pro vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci.  
  
4. Slovník prostředků motivu je zaškrtnut pro aktuálně aktivní motiv. Pokud se motiv změní za běhu, hodnota se znovu vyhodnotí.  
  
5. Jsou zaškrtnuté systémové prostředky.  
  
 Chování výjimky (pokud existuje) se liší:  
  
- Pokud byl prostředek vyžádán <xref:System.Windows.FrameworkElement.FindResource%2A> voláním a nebyl nalezen, je vyvolána výjimka.  
  
- Pokud byl prostředek vyžádán <xref:System.Windows.FrameworkElement.TryFindResource%2A> voláním a nebyl nalezen, není vyvolána žádná výjimka, ale vrácená hodnota je. `null` Pokud je vlastnost nastavena na hodnotu `null`, je stále možné, že bude vyvolána hlubší výjimka (to závisí na nastavené individuální vlastnosti).  
  
- Pokud byl prostředek vyžádán odkazem dynamického prostředku v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]a nebyl nalezen, bude chování záviset na obecném systému vlastností, ale obecné chování je, jako by na úrovni, kde existuje prostředek, nedošlo k žádné operaci nastavení vlastnosti. Například pokud se pokusíte nastavit pozadí na jednotlivé prvky tlačítka pomocí prostředku, který nebylo možné vyhodnotit, pak žádná sada hodnot nevrátí hodnotu, ale efektivní hodnota může být stále z jiných účastníků v rámci hodnoty systému vlastností a priority hodnoty. Například hodnota pozadí může být stále pocházet z lokálně definovaného stylu tlačítka nebo ze stylu motivu. Pro vlastnosti, které nejsou definovány styly motivů, může platit efektivní hodnota po neúspěšném vyhodnocení prostředku z výchozí hodnoty v metadatech vlastností.  
  
#### <a name="restrictions"></a>Omezení  
 Odkazy na dynamické prostředky mají určitá významná omezení. Aspoň jedna z následujících možností musí být true:  
  
- Nastavená vlastnost musí být vlastnost v <xref:System.Windows.FrameworkElement> nebo. <xref:System.Windows.FrameworkContentElement> Tato vlastnost musí být zálohována pomocí <xref:System.Windows.DependencyProperty>.  
  
- Odkaz je určen pro hodnotu v rámci <xref:System.Windows.Style>. <xref:System.Windows.Setter>  
  
- Vlastnost <xref:System.Windows.Freezable> nastavená musí být vlastnost v, která je k dispozici jako hodnota <xref:System.Windows.FrameworkElement> buď vlastnosti, <xref:System.Windows.Setter> nebo <xref:System.Windows.FrameworkContentElement> nebo hodnoty.  
  
 Vzhledem k tomu, že nastavená vlastnost <xref:System.Windows.DependencyProperty> musí <xref:System.Windows.Freezable> být vlastnost nebo, může se většina změn vlastností šířit do uživatelského rozhraní, protože Změna vlastnosti (změněná hodnota dynamického prostředku) je potvrzena systémem vlastností. Většina ovládacích prvků zahrnuje logiku, která vynutí jiné rozložení ovládacího prvku, <xref:System.Windows.DependencyProperty> Pokud změny a tato vlastnost mohou ovlivnit rozložení. Nicméně ne všechny vlastnosti, které mají [rozšíření značek DynamicResource](dynamicresource-markup-extension.md) jako jejich hodnota, zaručují poskytnutí hodnoty takovým způsobem, že se v uživatelském rozhraní aktualizují v reálném čase. Tato funkce se stále může lišit v závislosti na vlastnosti a také v závislosti na typu, který vlastní vlastnost, nebo dokonce na logické struktuře aplikace.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Styly, šablony a implicitní klíče  
 Dříve bylo uvedeno, že všechny položky v <xref:System.Windows.ResourceDictionary> musí mít klíč. To však neznamená, že všechny prostředky musí mít explicitní `x:Key`. Několik typů objektů podporuje implicitní klíč, pokud je definován jako prostředek, kde hodnota klíče je svázána s hodnotou jiné vlastnosti. To se označuje jako implicitní klíč, zatímco `x:Key` atribut je explicitní klíč. Můžete přepsat libovolný implicitní klíč zadáním explicitního klíče.  
  
 Jedním z velmi důležitých scénářů pro prostředky je při definování <xref:System.Windows.Style>. Ve skutečnosti <xref:System.Windows.Style> je téměř vždy definováno jako položka ve slovníku prostředků, protože styly jsou podstatně určeny k opakovanému použití. Další informace o stylech naleznete v tématu [stylování and šablonování](../controls/styling-and-templating.md).  
  
 Styly pro ovládací prvky mohou být vytvořeny pomocí a odkazovány pomocí implicitního klíče. Styly motivů, které definují výchozí vzhled ovládacího prvku, spoléhají na tento implicitní klíč. Implicitní klíč z hlediska vyžádání je <xref:System.Type> z hlediska samotného ovládacího prvku. Implicitní klíč z hlediska definování prostředku je <xref:System.Windows.Style.TargetType%2A> stylem. Proto pokud vytváříte motivy pro vlastní ovládací prvky, vytváření stylů, které pracují se stávajícími styly motivů, není nutné zadávat pro <xref:System.Windows.Style>tuto [direktivu x:Key –](../../xaml-services/x-key-directive.md) . A pokud chcete použít styly motivů, nemusíte vůbec zadávat žádný styl. Například následující definice stylu funguje, i když se zdá, že <xref:System.Windows.Style> prostředek nemá klíč:  
  
 [!code-xaml[FEResourceSH_snip#ImplicitStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Tento styl má ve skutečnosti klíč: implicitní klíč `typeof(`. <xref:System.Windows.Controls.Button> `)` V kódu můžete zadat <xref:System.Windows.Style.TargetType%2A> přímo jako název typu (případně můžete použít [{x:Type...}](../../xaml-services/x-type-markup-extension.md) ). pro vrácení <xref:System.Type>.  
  
 Pomocí výchozích mechanismů stylu motivů používaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástrojem je tento styl použit jako styl <xref:System.Windows.Controls.Button> modulu runtime na stránce, i když se <xref:System.Windows.Controls.Button> sám nepokouší zadat jeho <xref:System.Windows.FrameworkElement.Style%2A> vlastnost nebo konkrétní prostředek. odkaz na styl Váš styl definovaný na stránce se nachází dříve v sekvenci vyhledávání než styl slovníku motivu pomocí stejného klíče, který má styl slovníku motivů. Mohli byste jenom zadat `<Button>Hello</Button>` kamkoli na stránce a styl, který jste definovali, <xref:System.Windows.Style.TargetType%2A> `Button` se použije pro toto tlačítko. Pokud chcete, můžete stále explicitně vyklíčovat styl se stejnou hodnotou typu jako <xref:System.Windows.Style.TargetType%2A>pro přehlednost v kódu, ale to je volitelné.  
  
 Implicitní klíče pro styly neplatí pro ovládací prvek, pokud <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> je `true` (také Upozorňujeme, <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> že je možné nastavit jako součást nativního chování pro třídu ovládacího prvku namísto explicitního použití instance ovládacího prvku). Aby bylo možné podporovat implicitní klíče pro odvozené třídy, ovládací prvek musí přepsat <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (všechny existující ovládací prvky, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou součástí tohoto příkazu). Další informace o stylech, motivech a návrhu ovládacích prvků naleznete v tématu [pokyny pro návrh ovládacích ovládacích prvků](../controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate>má také implicitní klíč. Implicitní klíč pro <xref:System.Windows.DataTemplate> <xref:System.Windows.DataTemplate.DataType%2A> je hodnota vlastnosti. <xref:System.Windows.DataTemplate.DataType%2A>lze také zadat jako název typu místo explicitního použití [{x:Type...}](../../xaml-services/x-type-markup-extension.md). Podrobnosti najdete v tématu [Přehled šablonování dat](../data/data-templating-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.ResourceDictionary>
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Prostředky a kód](resources-and-code.md)
- [Definice a odkaz prostředku](how-to-define-and-reference-a-resource.md)
- [Přehled správy aplikací](../app-development/application-management-overview.md)
- [x:Type – rozšíření značek](../../xaml-services/x-type-markup-extension.md)
- [Rozšíření značek StaticResource](staticresource-markup-extension.md)
- [Rozšíření značek DynamicResource](dynamicresource-markup-extension.md)
