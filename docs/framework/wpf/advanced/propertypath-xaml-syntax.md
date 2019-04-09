---
title: PropertyPath – syntaxe v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 7db435e45ddc55346af5ea5fdbcce611173c774b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122912"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath – syntaxe v jazyce XAML
<xref:System.Windows.PropertyPath> Objekt podporuje komplexní vložené [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi pro různé vlastnosti, které provést nastavení <xref:System.Windows.PropertyPath> typu jako jeho hodnotu. Toto téma dokumenty <xref:System.Windows.PropertyPath> syntaxe jako použitý pro vazbu a animace syntaxe.  

<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>Kde se používá PropertyPath  
 <xref:System.Windows.PropertyPath> je běžné objekt, který se používá v několika [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkce. Bez ohledu na použití společné <xref:System.Windows.PropertyPath> k předání informací o cestě vlastnost využití pro jednotlivé oblasti funkce kde <xref:System.Windows.PropertyPath> se používá jako typ se liší. Je tedy praktičtější dokumentu syntaxe na základě podle funkcí.  
  
 Především [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.PropertyPath> k popisu cesty objektový model pro procházení vlastností zdroje dat objektu a k popisu cílovou cestu pro cílové animace.  
  
 Některé vlastnosti stylu a šablony, jako <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> trvat název kvalifikovaný vlastnosti, která se podobá na první pohled <xref:System.Windows.PropertyPath>. Ale to není skutečně představuje <xref:System.Windows.PropertyPath>; místo toho je kvalifikovaný *owner.property* řetězec formátu využití, který je povolen ve WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru v kombinaci s konvertor typu pro <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>Propertypath – pro objekty v datové vazbě  
 Datová vazba [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce zajišťovaný cílová hodnota libovolné vlastnosti závislostí lze svázat. Zdroj datové vazby však nemusí být vlastnost závislosti; může být libovolný typ vlastnosti, který je rozpoznán zprostředkovatelem dat. Cesty vlastností slouží zejména pro <xref:System.Windows.Data.ObjectDataProvider>, který se používá pro získání zdroje připojení z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty a jejich vlastnosti.  
  
 Všimněte si, že vazba dat k [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] nepoužívá <xref:System.Windows.PropertyPath>, protože nepoužívá <xref:System.Windows.Data.Binding.Path%2A> v <xref:System.Windows.Data.Binding>. Místo toho použít <xref:System.Windows.Data.Binding.XPath%2A> a zadejte platnou syntaxi XPath do [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] data. <xref:System.Windows.Data.Binding.XPath%2A> je také zadán jako řetězec, ale není dokumentováno. Zobrazit [svázání dat XML pomocí XMLDataProvider a dotazů XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Klíčem k pochopení cesty vlastností v datové vazbě je, že je možné cílit na vazby na hodnotu jednotlivých vlastností nebo místo toho lze svázat vlastnosti cíle, které přijímají seznamy nebo kolekce. Pokud vytváříte vazbu kolekce, například vytvoření vazby <xref:System.Windows.Controls.ListBox> , který se rozbalí v závislosti na tom, kolik datových položek jsou v kolekci, pak vaše cesta k vlastnosti by měla odkazovat na objekt kolekce, ne z individuálních kolekce položek. Modul vazby dat bude odpovídat použít jako zdroj dat na typ cíl vazby automaticky, což vede k chování například naplnění kolekce <xref:System.Windows.Controls.ListBox> s polem položek.  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>Jedinou vlastnost okamžité objektu jako kontext dat  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *Vlastnost propertyName* musíte vyřešit název vlastnosti, která je v aktuálním <xref:System.Windows.FrameworkElement.DataContext%2A> pro <xref:System.Windows.Data.Binding.Path%2A> využití. Pokud vaše vazby k aktualizaci ve zdroji, tato vlastnost musí být pro čtení a zápis a zdrojový objekt musí být Měnitelná.  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Jeden Indexer okamžitě objektu jako kontext dat  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` musí být typu index do slovníku nebo zatřiďovací tabulku nebo celočíselný index pole. Hodnotu klíče musí být typ, který je přímo umožňujících vazbu na vlastnost, kde se používá. Například zatřiďovací tabulku, která obsahuje řetězec klíče a hodnoty řetězce je možné tímto způsobem se vytvořit vazbu na Text <xref:System.Windows.Controls.TextBox>. Nebo, pokud klíč odkazuje na kolekci nebo podindex, můžete použít tuto syntaxi pro vytvoření vazby vlastnosti cílové kolekce. V opačném případě budete muset odkaz určité vlastnosti, prostřednictvím syntaxí, jako `<Binding Path="[key].propertyName" .../>`.  
  
 V případě potřeby, můžete zadat typ indexu. Podrobnosti k tomuto cesty indexované vlastnosti najdete v tématu <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>Více vlastností (nepřímé vlastnost cílení)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` musíte vyřešit název vlastnosti, která je aktuálně <xref:System.Windows.FrameworkElement.DataContext%2A>. Vlastnosti cesty `propertyName` a `propertyName2` může být jakékoli vlastnosti, které existují v relaci, kde `propertyName2` je vlastnost, která existuje na typ, který je hodnota `propertyName`.  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>Jedinou vlastností, připojené nebo jinak kvalifikovaný typ  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Závorky označuje, že tato vlastnost v <xref:System.Windows.PropertyPath> třeba vytvořit pomocí částečné kvalifikace. Obor názvů XML lze najít typ s vhodné mapování. `ownerType` Hledání typy, které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor má přístup, až <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklarací v každé sestavení. Většina aplikací má výchozí obor názvů XML namapované na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] obor názvů, takže předpona je obvykle potřeba, pouze pro vlastní typy nebo typy jinak mimo tento obor názvů.  `propertyName` Název vlastnosti stávajících se musí přeložit `ownerType`. Tato syntaxe je obvykle použita pro jednu z následujících případech:  
  
-   Cesta je určena v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , který je ve stylu nebo šablony, která nemá zadaný typ cíle. Kvalifikované použití obecně není platný pro případy, než to, a protože v jiných – vizuální styl, nešablonové případech vlastnost existuje instance, není typu.  
  
-   Vlastnost je připojené vlastnosti.  
  
-   Jsou vytvoření vazby na statickou vlastnost.  
  
 Pro použití jako cíl scénáře vlastnost zadaná jako `propertyName` musí být <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Procházení zdroje (vytvoření vazby na hierarchie kolekce)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 / V této syntaxe slouží k navigaci v rámci zdrojového objektu hierarchických dat a více kroků na hierarchii s po sobě jdoucích / znaky jsou podporovány. Zdrojové účty procházení pro aktuální pozici ukazatele záznamu, což je určeno synchronizaci dat s uživatelským rozhraním z jeho zobrazení. Podrobnosti o vázání s objekty zdrojů hierarchických dat a koncept aktuální ukazatel záznam v datové vazbě naleznete v tématu [použití vzoru seznam-podrobnosti s hierarchickými daty](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) nebo [Data Binding Overview](../data/data-binding-overview.md).  
  
> [!NOTE]
>  Na první pohled, vypadá podobně jako tato syntaxe [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Skutečného [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] výraz pro vytvoření vazby na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroj dat se nepoužívá jako <xref:System.Windows.Data.Binding.Path%2A> hodnotu a místo toho byste měli použít pro vzájemně vylučují <xref:System.Windows.Data.Binding.XPath%2A> vlastnost.  
  
### <a name="collection-views"></a>Zobrazení kolekcí  
 Chcete-li zobrazení s názvem kolekce, zadejte před název zobrazení kolekce znak hash (`#`).  
  
### <a name="current-record-pointer"></a>Aktuální záznam ukazatele  
 Pokud chcete odkázat na aktuální záznam ukazatel pro zobrazení kolekce nebo scénáře vázání dat. hlavní podrobností, začněte řetězec cesty s lomítkem (`/`). Libovolnou cestu poslední lomítko procházet řízený od aktuální ukazatel záznamu.  
  
### <a name="multiple-indexers"></a>Několik indexerů  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Pokud daný objekt podporuje několik indexerů, lze tyto indexování v pořadí, podobně jako pole odkazující na syntaxi. U daného objektu může být aktuální kontext nebo hodnotu vlastnosti, která obsahuje více objektů indexu.  
  
 Ve výchozím nastavení jsou hodnoty indexeru typována pomocí vlastnosti základní objekt. V případě potřeby, můžete zadat typ indexu. Informace o psaní indexery, naleznete v tématu <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>Kombinování syntaxe  
 Můžete promíchaný všech syntaxe uvedené výše. Například tady je příklad, který vytvoří vlastnost cestu na barvu na konkrétní x, y `ColorGrid` vlastnost, která obsahuje pole pixel mřížky <xref:System.Windows.Media.SolidColorBrush> objekty:  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>Řídicí sekvence pro vlastnosti řetězce cesty  
 Pro některé objekty obchodní můžete setkat s případem, kde řetězec cesty vlastnost vyžaduje řídicí sekvenci, aby bylo možné správně analyzovat. Nutnost řídicí by mělo být taková situace vzácná, protože řada z těchto znaků má podobné pojmenování interakce problémy v jazycích, které by obvykle slouží k definování obchodního objektu.  
  
-   Uvnitř indexery ([]) řídící znak stříšky (^) další znak.  
  
-   Musíte je přeskočit (s použitím entity XML) určitých znaků, které jsou pro definice jazyka XML. Použití `&` znaku "&". Použití `>` řídicí koncová značka ">".  
  
-   Musíte je přeskočit (pomocí zpětného lomítka `\`) znaky, které jsou pro WPF XAML chování analyzátor pro zpracování rozšíření značek.  
  
    -   Zpětné lomítko (`\`) je řídicí znak samotný.  
  
    -   Znaménko rovná se (`=`) odděluje název vlastnosti z hodnoty vlastnosti.  
  
    -   Čárka (`,`) odděluje vlastnosti.  
  
    -   Pravá složená závorka (`}`) je koncem rozšíření značek.  
  
> [!NOTE]
>  Technicky vzato tyto řídicí sekvence fungovat pro vlastnost cestu scénáře také, ale jsou obvykle procházení objektové modely pro existující objekty WPF a uvozovací znaky by měl být zbytečné.  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>PropertyPath animace cílů  
 Vlastnost target animace musí být vlastnost závislosti, která přebírá buď <xref:System.Windows.Freezable> nebo primitivního typu. Cílové vlastnosti typu a konečný výsledek animovaný může však existovat na různé objekty. Pro animace cesta k vlastnosti slouží k definování připojení mezi cílový objekt animace pojmenované vlastnosti a zamýšleného cílového animace, o překračování vztahů vlastnosti objektu v hodnotách vlastnosti.  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>Obecné – vlastnosti objektu důležité informace týkající se animace  
 Další informace o animace koncepty, najdete v části [přehled scénářů](../graphics-multimedia/storyboards-overview.md) a [přehled animace](../graphics-multimedia/animation-overview.md).  
  
 Typ hodnoty nebo animované vlastnosti musí být buď <xref:System.Windows.Freezable> typů nebo primitiv. Vlastnost, která spustí cesta se musí přeložit název vlastnosti závislosti, která existuje na zadaný <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 Kvůli podpoře klonování pro animace <xref:System.Windows.Freezable> , který je již zmrazen, objektu určeného parametrem <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> musí být <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy.  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>Jedinou vlastnost cílového objektu  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` musíte vyřešit název vlastnosti závislosti, která existuje na zadaný <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>Cílení na nepřímé vlastnost  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` musí být vlastnost, která je buď <xref:System.Windows.Freezable> hodnotový typ nebo primitivní, který existuje v zadané <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 `propertyName2` musí být název, která existuje na objekt, který je hodnota vlastnosti závislosti `propertyName`. Jinými slovy `propertyName2` musí existovat jako vlastnost závislosti na typu, který je `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Nepřímé cílení animací je nutné z důvodu použité styly a šablony. Chcete-li cílit na animace, musíte <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> v cílové objektů, které se vytváří název [x: Name](../../xaml-services/x-name-directive.md) nebo <xref:System.Windows.FrameworkElement.Name%2A>. Přestože šablony a prvky stylů také může mít názvy, názvy platí pouze v rámci namescope stylu a šablon. (Pokud styly a šablony značce aplikace sdílet obory názvů, názvy nemohl být jedinečné. Styly a šablony doslova sdílejí mezi instancemi a by perpetuate duplicitní názvy.) Proto pokud jednotlivé vlastnosti elementu, který chcete animovat pochází stylu nebo šablony, budete muset spustit s instancí s názvem elementu, který není ze šablony stylů a směrovat do stylu nebo šablony vizuálního stromu můžete přejít na vlastnost chcete animovat.  
  
 Například <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Panel> je kompletní <xref:System.Windows.Media.Brush> (ve skutečnosti <xref:System.Windows.Media.SolidColorBrush>), které přišly z motivu šablony. Animování <xref:System.Windows.Media.Brush> úplně, došlo by musí být BrushAnimation (pravděpodobně jeden pro každý <xref:System.Windows.Media.Brush> typu) a neexistuje žádný takový typ. Pro animaci štětce, místo toho animovat vlastnosti z konkrétní <xref:System.Windows.Media.Brush> typu. Je potřeba získat z <xref:System.Windows.Media.SolidColorBrush> k jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> použít <xref:System.Windows.Media.Animation.ColorAnimation> existuje. Cesta vlastnosti v tomto příkladu bude `Background.Color`.  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>Přidružené vlastnosti  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Závorky označuje, že tato vlastnost v <xref:System.Windows.PropertyPath> třeba vytvořit pomocí částečné kvalifikace. Obor názvů XML může použít k vyhledání typu. `ownerType` Hledání typy, které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor má přístup, až <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklarací v každé sestavení. Většina aplikací má výchozí obor názvů XML namapované na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] obor názvů, takže předpona je obvykle potřeba, pouze pro vlastní typy nebo typy jinak mimo tento obor názvů. `propertyName` Název vlastnosti stávajících se musí přeložit `ownerType`. Vlastnost zadaná jako `propertyName` musí být <xref:System.Windows.DependencyProperty>. (Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojené vlastnosti jsou implementovány jako vlastnosti závislostí, abyste tento problém je pouze z hlediska vlastní připojené vlastnosti.)  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>Indexery  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 Většina vlastností závislostí nebo <xref:System.Windows.Freezable> nepodporují indexeru. Proto je pouze využití pro indexer v cestě animace zprostředkující pozici mezi vlastnost, která začíná pojmenované cílového řetězce a konečný výsledek animované vlastnosti. V zadané syntaxi, která je `propertyName2`. Použití indexeru pro instanci, může být nutné v případě, že vlastnost zprostředkující, jako je kolekce <xref:System.Windows.Media.TransformGroup>, v cestě vlastnosti, jako `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>PropertyPath v kódu  
 Kód pro využití <xref:System.Windows.PropertyPath>, jak vytvořit <xref:System.Windows.PropertyPath>, najdete v tématu o <xref:System.Windows.PropertyPath>.  
  
 Obecně platí <xref:System.Windows.PropertyPath> je navržen pro použití dva různé konstruktory, jeden pro použití vazby a nejjednodušší použití animace a jeden pro použití komplexní animace. Použití <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpis pro vazby použití, kde je objekt na řetězec. Použití <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpis pro jednoduchý animace cesty, kde je objekt <xref:System.Windows.DependencyProperty>. Použití <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> podpis pro komplexní animace. Tento druhý konstruktor používá řetězec tokenu pro první parametr a pole objektů, které vyplnění pozic v řetězec tokenu k definování relace vlastnost cesty.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.PropertyPath>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Přehled scénářů](../graphics-multimedia/storyboards-overview.md)
