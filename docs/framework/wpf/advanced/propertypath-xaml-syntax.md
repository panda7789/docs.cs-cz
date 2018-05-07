---
title: PropertyPath – syntaxe v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 547c7d009d2fecf863284324c7ea45006d20d20c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath – syntaxe v jazyce XAML
<xref:System.Windows.PropertyPath> Objekt podporuje komplexní vložené [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe pro nastavení různé vlastnosti, které provést <xref:System.Windows.PropertyPath> typ jako jeho hodnotu. Toto téma dokumenty <xref:System.Windows.PropertyPath> syntaxe jako použít pro vazby a animace syntaxe.  
    
  
<a name="where"></a>   
## <a name="where-propertypath-is-used"></a>Kde se používá PropertyPath  
 <xref:System.Windows.PropertyPath> je běžné objekt, který se používá v několika [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkce. Navzdory pomocí nejběžnější <xref:System.Windows.PropertyPath> vyjádřit informace o cestě vlastnost použití pro každou funkci oblasti kde <xref:System.Windows.PropertyPath> se používá jako typ se liší. Proto je praktičtější dokumentu syntaxe na základě na funkce.  
  
 Především se stává [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.PropertyPath> k popisu cesty objektový model pro procházení vlastnosti objektu zdroje dat a k popisu cílová cesta pro cílové animace.  
  
 Některé vlastnosti stylu a šablony, jako <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> trvat vlastnost kvalifikovaný název, který na první pohled se podobá <xref:System.Windows.PropertyPath>. Toto není hodnotu true, ale <xref:System.Windows.PropertyPath>; místo toho je kvalifikovaný *owner.property* řetězec formátu využití, který je povolený pomocí WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru v kombinaci s převaděč typů pro <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath pro objekty v datová vazba  
 Datová vazba je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, jimiž lze vázat na cílovou hodnotu vlastnosti žádné závislosti. Zdroj dat vazbu však nemusí být vlastnost závislosti; může být žádný vlastnost typ, který je rozpoznáno poskytovatel dat použít. Cesty k vlastnostem se používají zejména pro <xref:System.Windows.Data.ObjectDataProvider>, který se používá k získání vazby zdroje z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty a jejich vlastnosti.  
  
 Všimněte si, že datová vazba na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] nepoužívá <xref:System.Windows.PropertyPath>, protože nepoužívá <xref:System.Windows.Data.Binding.Path%2A> v <xref:System.Windows.Data.Binding>. Místo toho použít <xref:System.Windows.Data.Binding.XPath%2A> a zadejte platné syntaxe jazyka XPath do [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] data. <xref:System.Windows.Data.Binding.XPath%2A> rovněž je zadán jako řetězec, ale není dokumentováno zde; v tématu [vazby na Data XML pomocí služby XMLDataProvider a dotazy jazyka XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Klíčem k pochopení cesty k vlastnostem v datová vazba je, že můžete určit cílovou vazby na jednotlivé vlastnosti hodnotu, nebo místo toho můžete vázat na vlastností cíle, které provést seznamy nebo kolekce. Pokud vytváříte vazbu kolekcí, například vytvoření vazby <xref:System.Windows.Controls.ListBox> , bude rozbalte v závislosti na tom, kolik datových položek jsou v kolekci, pak cestu k vlastnost by měla odkazovat objektu kolekce, ne z individuálních kolekce položek. Modul vazby dat bude shodovat s kolekci použít jako zdroj dat na typ cíle vazba automaticky, výsledkem chování například naplnění <xref:System.Windows.Controls.ListBox> s položky pole.  
  
<a name="singlecurrent"></a>   
### <a name="single-property-on-the-immediate-object-as-data-context"></a>Vlastnosti jediné okamžitou objektu jako kontextu dat  
  
```xml  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* musí být název vlastnosti, která je v aktuálním řešení <xref:System.Windows.FrameworkElement.DataContext%2A> pro <xref:System.Windows.Data.Binding.Path%2A> využití. Pokud vaše vazby aktualizuje zdroj, vlastnosti musí být pro čtení a zápis a zdrojový objekt musí být měnitelný.  
  
<a name="singleindex"></a>   
### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Jeden indexeru okamžitě objektu jako kontextu dat  
  
```xml  
<Binding Path="[key]" .../>  
```  
  
 `key` musí být buď typu index do slovníku nebo zatřiďovací tabulku, nebo celočíselný index pole. Hodnota klíče navíc musí být typ, který je přímo vazbu na vlastnost, kdy se používá. Například zatřiďovací tabulka, která obsahuje řetězec klíče a hodnoty řetězce můžete tímto způsobem pro vazbu použit na Text pro <xref:System.Windows.Controls.TextBox>. Nebo, pokud klíč odkazuje na kolekci nebo podindex, můžete použít tuto syntaxi vytvoření vazby na vlastnost cílové kolekce. Jinak, potřebujete odkazovat na konkrétní vlastnosti, prostřednictvím syntaxí, jako `<Binding Path="[``key``].``propertyName``" .../>`.  
  
 Typ indexu můžete zadat, pokud je to nutné. Podrobnosti k tomuto cestu indexované vlastnosti najdete v tématu <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="multipleindirect"></a>   
### <a name="multiple-property-indirect-property-targeting"></a>Více vlastností (nepřímé vlastnost cílení na)  
  
```xml  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` musí být název vlastnosti, která je aktuální řešení <xref:System.Windows.FrameworkElement.DataContext%2A>. Vlastnosti cesty `propertyName` a `propertyName2` může být jakékoli vlastnosti, které existují v relaci, kde `propertyName2` je vlastnost, která existuje na typ, který je hodnota `propertyName`.  
  
<a name="singleattached"></a>   
### <a name="single-property-attached-or-otherwise-type-qualified"></a>Jedinou vlastností, připojené nebo v opačném případě zadejte kvalifikovaný  
  
```xml  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Závorkách označuje, že v této vlastnosti <xref:System.Windows.PropertyPath> by měl být vytvářeny pomocí částečné kvalifikaci. Může použít obor názvů XML se najít typ s příslušné mapování. `ownerType` Hledání typy, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor má přístup, až <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklarací v každé sestavení. Většina aplikací mít výchozí obor názvů XML namapované na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] obor názvů, takže předponu je obvykle nezbytné pro vlastní typy nebo typy jinak mimo tento obor názvů.  `propertyName` být název vlastnosti stávajících se musí přeložit `ownerType`. Tuto syntaxi se obvykle používá pro jednu z následujících případech:  
  
-   Cesta je určena v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , je v styl nebo šabloně, který nemá zadaný cílový typ. Použití kvalifikovaný obecně není platný pro případy, než to, a protože v případech jiný styl, bez šablony existuje v instanci, není typu vlastnost.  
  
-   Vlastnost je přidružená vlastnost.  
  
-   Vytváříte vazbu s pomocí statické vlastnosti.  
  
 Pro použití jako cíl storyboard, tato vlastnost zadaná jako `propertyName` musí být <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Zdroj Traversal (vytvoření vazby na hierarchie kolekce)  
  
```xml  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 / V této syntaxe je použít pro účely navigace v rámci objekt zdroje dat hierarchické a několika kroky do hierarchie s následných / znaky jsou podporovány. Účty traversal zdroj pro aktuální pozici záznamů ukazatele, který je určen podle synchronizaci dat s uživatelským rozhraním jeho zobrazení. Informace o vazba s objekty zdroje dat hierarchické a konceptu ukazatel aktuální záznam v datové vazby v [použití vzoru seznam-podrobnosti s hierarchické Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) nebo [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  Na první pohled, se podobá této syntaxe [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)]. Skutečného [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] výraz vazba [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroj dat není používána jako <xref:System.Windows.Data.Binding.Path%2A> hodnota a má být použit místo pro vzájemně vylučují <xref:System.Windows.Data.Binding.XPath%2A> vlastnost.  
  
### <a name="collection-views"></a>Zobrazení kolekce  
 Chcete-li zobrazení s názvem kolekce, zadejte před název zobrazení kolekce znak hash (`#`).  
  
### <a name="current-record-pointer"></a>Aktuální záznam ukazatele  
 Chcete-li aktuální ukazatele záznamů pro zobrazení kolekce nebo scénář vazby dat hlavní podrobností, spustit řetězec cesty s lomítkem (`/`). Jakoukoli cestu po dopředné lomítko je provázán od aktuální záznam ukazatele.  
  
### <a name="multiple-indexers"></a>Několik indexerů  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Pokud daný objekt podporuje několik indexerů, lze tyto indexery v pořadí, podobně jako pole odkazující na syntaxi. Aktuální kontext nebo hodnotu vlastnosti, která obsahuje objekt více index, může být u daného objektu.  
  
 Ve výchozím nastavení jsou hodnoty indexer typu pomocí vlastnosti podkladového objektu. Typ indexu můžete zadat, pokud je to nutné. Podrobnosti na zadáním indexery, které najdete v tématu <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.  
  
<a name="mixing"></a>   
### <a name="mixing-syntaxes"></a>Kombinování syntaxe  
 Může být spolu každý syntaxe uvedené výše. Například následující je příklad, který vytvoří vlastnost cestu k barvu v konkrétní x, y `ColorGrid` vlastnost, která obsahuje pole pixelů mřížky <xref:System.Windows.Media.SolidColorBrush> objekty:  
  
```xml  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### <a name="escapes-for-property-path-strings"></a>Řídicí sekvence pro vlastnost Cesta řetězce  
 Pro určité objekty firmy může dojít k případu, kde řetězec cesty vlastnost vyžaduje řídicí sekvence, aby bylo možné správně analyzovat. Potřeba, abyste se vyhnuli by měl být taková situace vzácná, protože mnoho z těchto znaků mají podobné pojmenování interakce problémy v jazycích, které by obvykle používá k definování obchodního objektu.  
  
-   Uvnitř indexery ([]) nastavení řídicí sekvence znaků pomocí kurzoru (^) další znak.  
  
-   Musíte použít řídící (s použitím entity XML) určitých znaků, které jsou speciální k definici jazyka XML. Použití `&` řídicí znak "&". Použití `>` abyste se vyhnuli koncová značka ">".  
  
-   Musí vyhnuli (pomocí zpětné lomítko `\`) znaků, které jsou zvláštní chování analyzátor WPF XAML pro zpracování rozšíření značek.  
  
    -   Zpětné lomítko (`\`) je vlastní řídicí znak.  
  
    -   Znaménkem rovnosti (`=`) odděluje název vlastnosti z hodnoty vlastnosti.  
  
    -   Čárkami (`,`) odděluje vlastnosti.  
  
    -   Pravé složené závorky (`}`) je konci rozšíření značek.  
  
> [!NOTE]
>  Technicky tyto řídicí sekvence fungovat pro cestu k storyboard vlastnost taky, ale jsou obvykle procházení objektové modely pro existující objekty grafického subsystému WPF a uvozovací znaky by měl být zbytečné.  
  
<a name="databinding_sa"></a>   
## <a name="propertypath-for-animation-targets"></a>PropertyPath pro cíle animace  
 Vlastnost target tohoto animace musí být vlastnost závislosti, která přebírá buď <xref:System.Windows.Freezable> nebo primitivního typu. Ale cílové vlastnosti na typ a vlastnost případné animovaný může existovat v různých objektů. Pro animace cestu vlastnost se používá k definování připojení mezi vlastnost cílový objekt s názvem animace a vlastnost animace zamýšleného cílového pomocí procházení vlastnost objektu relace v hodnotách vlastnosti.  
  
<a name="general"></a>   
### <a name="general-object-property-considerations-for-animations"></a>Obecné – vlastnosti objektu aspekty animace  
 Další informace o animace koncepty obecně platí, najdete v části [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md) a [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Typ hodnoty nebo vlastnosti se animovaný musí být buď <xref:System.Windows.Freezable> typ nebo primitivní. Vlastnost, která spustí cesta se musí přeložit název vlastnosti závislost, která existuje v zadané <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 Kvůli podpoře klonování animace <xref:System.Windows.Freezable> , je již pozastaveny, objektu určeného <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> musí být <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozené třídy.  
  
<a name="singlestepanim"></a>   
### <a name="single-property-on-the-target-object"></a>Jedinou vlastností v cílovém objektu  
  
```xml  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` musí být název vlastnosti závislost, která existuje v zadané vyřešit <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
<a name="indirectanim"></a>   
### <a name="indirect-property-targeting"></a>Cílení na nepřímých vlastnost  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` musí být vlastnost, která je buď <xref:System.Windows.Freezable> hodnotu typ nebo primitivní, která již existuje v zadané <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.  
  
 `propertyName2` musí být název vlastnosti závislost, která existuje v objektu, která je hodnota `propertyName`. Jinými slovy `propertyName2` musí existovat jako vlastnost závislosti na typu, který je `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Nepřímý cílení animací je nutné kvůli použité styly a šablony. Aby bylo možné zacílit animace, musíte <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> na cílový objekt a zda je název zřízena [x: Name](../../../../docs/framework/xaml-services/x-name-directive.md) nebo <xref:System.Windows.FrameworkElement.Name%2A>. I když šablony a stylu elementy také může mít názvy, jsou platné v rámci namescope stylu a šablony pouze tyto názvy. (Pokud šablony a styly namescopes sdílet s aplikací značek, názvy nemohl být jedinečné. Styly a šablony oznámena sdílejí mezi instancemi a by perpetuate duplicitní názvy.) Proto pokud jednotlivé vlastnosti elementu, který chcete animace pochází styl nebo šablony, budete muset spustit s instancí s názvem elementu, který není ze šablony stylů a pak cíle do styl nebo šablony vizuálním stromu přijaty ve vlastnosti Chcete animace.  
  
 Například <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Panel> je úplná <xref:System.Windows.Media.Brush> (ve skutečnosti a <xref:System.Windows.Media.SolidColorBrush>), pocházejí ze šablony motiv. Pro animaci <xref:System.Windows.Media.Brush> úplně, došlo by musí být BrushAnimation (pravděpodobně jeden pro každou <xref:System.Windows.Media.Brush> typu) a neexistuje žádný takový typ. Pro animaci štětce, můžete místo toho použije animaci vlastnosti konkrétní <xref:System.Windows.Media.Brush> typu. Potřebujete získat z <xref:System.Windows.Media.SolidColorBrush> k jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pro použití <xref:System.Windows.Media.Animation.ColorAnimation> existuje. Cesta k vlastnosti v tomto příkladu by `Background.Color`.  
  
<a name="attachedanim"></a>   
### <a name="attached-properties"></a>Přidružené vlastnosti  
  
```xml  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Závorkách označuje, že v této vlastnosti <xref:System.Windows.PropertyPath> by měl být vytvářeny pomocí částečné kvalifikaci. Obor názvů XML může použít k vyhledání typu. `ownerType` Hledání typy, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor má přístup, až <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklarací v každé sestavení. Většina aplikací mít výchozí obor názvů XML namapované na [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] obor názvů, takže předponu je obvykle nezbytné pro vlastní typy nebo typy jinak mimo tento obor názvů. `propertyName` být název vlastnosti stávajících se musí přeložit `ownerType`. Vlastnost zadaná jako `propertyName` musí být <xref:System.Windows.DependencyProperty>. (Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružené vlastnosti jsou implementované jako vlastností závislostí, takže tento problém je pouze z hlediska vlastní přidružené vlastnosti.)  
  
<a name="indexanim"></a>   
### <a name="indexers"></a>Indexery  
  
```xml  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 Většinu vlastností závislostí nebo <xref:System.Windows.Freezable> typů nepodporují indexer. Pouze použití indexer v umístění animace je proto zprostředkující pozice mezi vlastnost, která spustí řetězu v pojmenované cíli a případné animovaný vlastnost. V zadané syntaxi, která je `propertyName2`. Například může být nutné v případě, že vlastnost zprostředkující, jako je kolekce použití indexeru <xref:System.Windows.Media.TransformGroup>, vlastnost cesty, jako `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## <a name="propertypath-in-code"></a>PropertyPath v kódu  
 Kód využití <xref:System.Windows.PropertyPath>, včetně toho, jak vytvořit <xref:System.Windows.PropertyPath>, jsou uvedené v tématu o <xref:System.Windows.PropertyPath>.  
  
 Obecně platí <xref:System.Windows.PropertyPath> slouží k použití dvou různých konstruktory, jeden pro použití vazby a nejjednodušší použití animace a jeden pro použití komplexní animace. Použití <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpis pro použití vazby, kde je objekt na řetězec. Použití <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> podpis pro jednoduchý animace cesty, kde je objekt <xref:System.Windows.DependencyProperty>. Použití <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> podpis pro komplexní animace. Tento konstruktor druhé používá řetězec tokenu pro první parametr a pole objektů, které vyplnění pozice v tokenu řetězec, který má definovat vztah vlastnost cesty.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.PropertyPath>  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
