---
title: PropertyPath – syntaxe v jazyce XAML
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 817ce750cdad58e504eef5144cfb8a2813bca596
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141293"
---
# <a name="propertypath-xaml-syntax"></a>PropertyPath – syntaxe v jazyce XAML

<xref:System.Windows.PropertyPath> Objekt podporuje složitou vloženou [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi pro nastavení různých vlastností, které přijímají <xref:System.Windows.PropertyPath> typ jako jejich hodnotu. Toto téma popisuje syntaxi <xref:System.Windows.PropertyPath> , která je aplikována na syntaxe vazeb a animací.

<a name="where"></a>

## <a name="where-propertypath-is-used"></a>Kde se používá PropertyPath

<xref:System.Windows.PropertyPath>je běžný objekt, který se používá v několika [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcích. Navzdory použití společné <xref:System.Windows.PropertyPath> k předávání informací o cestě k vlastnostem se použití pro každou oblast funkce, <xref:System.Windows.PropertyPath> kde se používá jako typ, liší. Proto je více praktické zdokumentovat syntaxe na základě jednotlivých funkcí.

Primárně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá <xref:System.Windows.PropertyPath> k popisu cest objektů a modelů pro procházení vlastností zdroje dat objektu a popisuje cílovou cestu pro cílené animace.

Některé vlastnosti stylu a šablony, jako <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> je například převzetí kvalifikovaného názvu vlastnosti, který se <xref:System.Windows.PropertyPath>podobá. Nejedná se však o hodnotu <xref:System.Windows.PropertyPath>true; místo toho je to kvalifikovaný *vlastník.* použití formátu řetězce vlastnosti, který je povolený procesorem WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v kombinaci s konvertorem typu <xref:System.Windows.DependencyProperty>pro.

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a>PropertyPath pro objekty v datové vazbě

Vázání dat je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, která umožňuje vytvořit vazbu na cílovou hodnotu libovolné vlastnosti závislosti. Zdroj takové datové vazby ale nemusí být vlastností závislosti; může to být libovolný typ vlastnosti, který rozpozná příslušný zprostředkovatel dat. Cesty vlastností jsou zvláště používány pro <xref:System.Windows.Data.ObjectDataProvider>, který slouží k získání vazeb zdrojů z objektů CLR (Common Language Runtime) a jejich vlastností.

Všimněte si, že datová vazba na XML nepoužívá <xref:System.Windows.PropertyPath>, protože nepoužívá <xref:System.Windows.Data.Binding.Path%2A> v. <xref:System.Windows.Data.Binding> Místo toho použijete <xref:System.Windows.Data.Binding.XPath%2A> a zadáte platnou syntaxi XPath do XML model DOM (Document Object Model) (DOM) dat. <xref:System.Windows.Data.Binding.XPath%2A>je také zadáno jako řetězec, ale zde není dokumentována; viz [vazba na data XML pomocí dotazů XmlDataProvider a XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).

Klíč k porozumění cestám vlastností v datové vazbě je, že je možné cílit na vazbu na individuální hodnotu vlastnosti, nebo můžete vytvořit vazbu k cílovým vlastnostem, které přebírají seznamy nebo kolekce. Pokud vytváříte vazbu kolekcí, například vazba instance a <xref:System.Windows.Controls.ListBox> , která se rozbalí v závislosti na tom, kolik datových položek je v kolekci, měla by vaše cesta vlastnosti odkazovat na objekt kolekce, nikoli na jednotlivé položky kolekce. Modul datových vazeb se bude shodovat s kolekcí použitou jako zdroj dat pro typ cíle vazby automaticky, což vede k chování, jako je například naplnění a <xref:System.Windows.Controls.ListBox> s polem Items (položky).

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a>Jednoduchá vlastnost u okamžitého objektu jako datový kontext

```xml
<Binding Path="propertyName" ... />
```

vlastnost *PropertyName* musí být přeložena jako název vlastnosti, která je v aktuálním <xref:System.Windows.FrameworkElement.DataContext%2A> pro <xref:System.Windows.Data.Binding.Path%2A> použití. Pokud vaše vazba aktualizuje zdroj, musí být tato vlastnost pro čtení/zápis a zdrojový objekt musí být mutable.

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a>Jeden indexer na bezprostředním objektu jako datový kontext

```xml
<Binding Path="[key]" ... />
```

`key`musí být buď zadaný index do slovníku, nebo zatřiďovací tabulka, nebo celočíselný index pole. Také hodnota klíč musí být typ, který je přímo svázán s vlastností, kde se používá. Například zatřiďovací tabulka, která obsahuje klíče řetězce a řetězcové hodnoty, může být použita tímto způsobem pro vytvoření vazby na text pro <xref:System.Windows.Controls.TextBox>. Nebo, pokud klíč odkazuje na kolekci nebo podindex, můžete použít tuto syntaxi k vytvoření vazby na vlastnost cílové kolekce. V opačném případě je nutné odkazovat na konkrétní vlastnost prostřednictvím syntaxe, jako je `<Binding Path="[key].propertyName" .../>`například.

V případě potřeby můžete zadat typ indexu. Podrobnosti o tomto aspektu cesty k indexovaným vlastnostem naleznete <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>v tématu.

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a>Vícenásobná vlastnost (cílení na nepřímých vlastností)

```xml
<Binding Path="propertyName.propertyName2" ... />
```

`propertyName`musí se vyhodnotit jako název vlastnosti, která je aktuální <xref:System.Windows.FrameworkElement.DataContext%2A>. Vlastnosti `propertyName` cesty a `propertyName2` mohou být libovolné vlastnosti, které existují v relaci, kde `propertyName2` je vlastnost, která existuje v typu, který je hodnotou. `propertyName`

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a>Jedna vlastnost, připojená nebo jinak kvalifikovaný typ

```xml
<object property="(ownerType.propertyName)" ... />
```

Kulaté závorky označují, že <xref:System.Windows.PropertyPath> by tato vlastnost měla být vytvořená pomocí částečné kvalifikace. Může použít obor názvů XML k nalezení typu s odpovídajícím mapováním. Typy `ownerType` prohledávání, ke kterým [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má procesor přístup, prostřednictvím <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklarací v jednotlivých sestaveních. Většina aplikací má výchozí obor názvů XML mapovaný na `http://schemas.microsoft.com/winfx/2006/xaml/presentation` obor názvů, takže předpona je obvykle pouze pro vlastní typy nebo typy mimo tento obor názvů.  `propertyName`musí se vyhodnotit jako název vlastnosti existující v `ownerType`. Tato syntaxe se obecně používá v jednom z následujících případů:

- Cesta je určena v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , který je ve stylu nebo šabloně, která nemá zadaný cílový typ. Kvalifikované použití není obecně platné pro jiné případy než to, protože v nestylových případech nezpůsobuje, že vlastnost existuje v instanci, nikoli v typu.

- Vlastnost je připojená vlastnost.

- Vytváříte vazbu na statickou vlastnost.

Pro použití jako cíle scénáře, vlastnost zadaná jako `propertyName` musí být. <xref:System.Windows.DependencyProperty>

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a>Zdrojový průchod (vazba na hierarchie kolekcí)

```xml
<object Path="propertyName/propertyNameX" ... />
```

V této syntaxi je použit k navigaci v rámci objektu hierarchického zdroje dat a je podporováno více kroků do hierarchie s následnými/znaky. Zdrojové účty pro procházení pro aktuální pozici ukazatele záznamu, která je určena synchronizací dat s uživatelským rozhraním jeho zobrazení. Podrobnosti o vazbě s objekty hierarchických zdrojů dat a koncept aktuálního ukazatele záznamu v datové vazbě najdete v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) nebo [přehledem datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

> [!NOTE]
> Tato syntaxe je napodobná XPath. Skutečný výraz XPath pro vazbu na zdroj dat XML se nepoužívá jako <xref:System.Windows.Data.Binding.Path%2A> hodnota a místo toho by se měl použít pro vzájemně exkluzivní <xref:System.Windows.Data.Binding.XPath%2A> vlastnost.

### <a name="collection-views"></a>Zobrazení kolekcí

Chcete-li odkazovat na pojmenované zobrazení kolekce, předponu názvu zobrazení kolekce nahraďte znakem hash (`#`).

### <a name="current-record-pointer"></a>Ukazatel aktuálního záznamu

Chcete-li odkazovat na ukazatel aktuálního záznamu pro scénář zobrazení kolekce nebo hlavní datové vazby, spusťte řetězec cesty s lomítkem (`/`). Libovolná cesta po lomítku je proprocházena od aktuálního ukazatele záznamu.

### <a name="multiple-indexers"></a>Více indexerů

```xaml
<object Path="[index1,index2...]" ... />
```

– nebo –

```xaml
<object Path="propertyName[index,index2...]" ... />
```

Pokud daný objekt podporuje více indexerů, mohou být tyto indexery zadány v pořadí, podobně jako syntaxe odkazující na pole. Daný objekt může být buď aktuální kontext, nebo hodnotou vlastnosti, která obsahuje více objektů indexu.

Ve výchozím nastavení jsou hodnoty indexeru zadány pomocí charakteristik podkladového objektu. V případě potřeby můžete zadat typ indexu. Podrobnosti o zadávání indexerů najdete v tématu <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a>Kombinování syntaxí

Každá z výše uvedených syntaxí se dá proložit. Například Následuje příklad, který vytvoří cestu vlastnosti k barvě v konkrétní ose x, y `ColorGrid` vlastnosti, která obsahuje pole s mřížkou pixelů <xref:System.Windows.Media.SolidColorBrush> objektů:

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" ... />
```

### <a name="escapes-for-property-path-strings"></a>Řídicí znaky pro řetězce cest vlastností

U určitých obchodních objektů se můžete setkat s případem, kdy řetězec cesty vlastnosti vyžaduje řídicí sekvenci, aby bylo možné správně analyzovat. Nutnost Escape by měla být vzácná, protože mnohé z těchto znaků mají podobné problémy s interakcemi pojmenování v jazycích, které by obvykle byly použity k definování obchodního objektu.

- Uvnitř indexerů ([]) znak stříšky (^) řídí další znak.

- Je nutné řídicí znaky (pomocí entit XML), které jsou speciální pro definici jazyka XML. Použijte `&` k Escape znaku "&". Použijte `>` k ukončení ukončovací značky ">".

- Je nutné řídicí znaky (pomocí zpětného lomítka `\`), které jsou specifické pro chování analyzátoru XAML WPF pro zpracování rozšíření značek.

  - Zpětné lomítko`\`() je řídicí znak sám sebe.

  - Symbol rovná se (`=`) odděluje název vlastnosti z hodnoty vlastnosti.

  - Čárka`,`() odděluje vlastnosti.

  - Pravá složená závorka (`}`) je koncem rozšíření značek.

> [!NOTE]
> Technicky, tyto řídicí prvky fungují také pro cestu k vlastnostem scénáře, ale obvykle jste procházejí modely objektů pro existující objekty WPF a uvozovací znaky by měly být zbytečné.

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a>PropertyPath pro cíle animace

Vlastnost target animace musí být vlastnost závislosti, která přebírá buď <xref:System.Windows.Freezable> nebo primitivního typu. Nicméně cílová vlastnost typu a vlastnost závěrečné animace může existovat v různých objektech. V případě animací se k definování propojení mezi vlastností objektu cílového objektu animace a zamýšlenou cílovou vlastností animace používá cesta k vlastnosti, a to tak, že přecházejí mezi vztahy objektů a vlastností v hodnotách vlastností.

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a>Obecné požadavky na vlastnosti objektu pro animace

Další informace o konceptech animace obecně najdete v tématu [Přehled scénářů](../graphics-multimedia/storyboards-overview.md) a [Přehled animací](../graphics-multimedia/animation-overview.md).

Typ hodnoty nebo vlastnost Animated musí být buď <xref:System.Windows.Freezable> typ, nebo primitivní. Vlastnost, která spustí cestu, musí být přeložena jako název vlastnosti závislosti, která existuje na zadaném <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.

Aby bylo možné podporovat <xref:System.Windows.Freezable> klonování pro animaci již zmrazeného objektu, musí být objekt určený parametrem <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> odvozenou třídou.

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a>Jediná vlastnost cílového objektu

```xml
<animation Storyboard.TargetProperty="propertyName" ... />
```

`propertyName`musí se vyhodnotit jako název vlastnosti závislosti, která existuje na zadaném <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a>Cílení na nepřímou vlastnost

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" ... />
```

`propertyName`musí se jednat o vlastnost, která je <xref:System.Windows.Freezable> buď typ hodnoty, nebo primitivní, které existují na zadaném <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> typu.

`propertyName2`musí se jednat o název vlastnosti závislosti, která existuje na objektu, který je hodnotou `propertyName`. Jinými slovy, `propertyName2` musí existovat jako vlastnost závislosti na typu, který je `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.

Nepřímý cíl animací je nutný z důvodu použitých stylů a šablon. Aby bylo možné cílit na animaci, potřebujete objekt <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> v cílovém objektu a tento název je vytvořen pomocí [x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) nebo. <xref:System.Windows.FrameworkElement.Name%2A> I když prvky šablony a stylu také mohou mít názvy, jsou tyto názvy platné pouze v rámci namescope stylu a šablony. (Pokud se šablony a styly sdílí obory názvů WPF s označením aplikace, názvy nejdou být jedinečné. Styly a šablony jsou doslova sdílené mezi instancemi a by perpetuate duplicitní názvy.) Proto pokud jednotlivé vlastnosti prvku, který chcete animovat, pochází ze stylu nebo šablony, je nutné začít s pojmenovanou instancí elementu, která není ze šablony stylu, a poté cílit do vizuálního stromu Style nebo Template, který chcete přijmout do vlastnosti, kterou chcete animovat.

Například <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Panel> je kompletní <xref:System.Windows.Media.Brush> (ve skutečnosti a <xref:System.Windows.Media.SolidColorBrush>), která pochází ze šablony motiv. Pro animaci <xref:System.Windows.Media.Brush> zcela musí být BrushAnimation (pravděpodobně jeden pro každý <xref:System.Windows.Media.Brush> typ) a neexistuje žádný takový typ. Pro animaci štětce můžete místo toho animovat vlastnosti určitého <xref:System.Windows.Media.Brush> typu. Musíte získat přístup ze služby <xref:System.Windows.Media.SolidColorBrush> k jejímu <xref:System.Windows.Media.SolidColorBrush.Color%2A> použití <xref:System.Windows.Media.Animation.ColorAnimation> . Cesta k vlastnosti v tomto příkladu bude `Background.Color`.

<a name="attachedanim"></a>

### <a name="attached-properties"></a>Přidružené vlastnosti

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" ... />
```

Kulaté závorky označují, že <xref:System.Windows.PropertyPath> by tato vlastnost měla být vytvořená pomocí částečné kvalifikace. K nalezení typu může použít obor názvů XML. Typy `ownerType` prohledávání, ke kterým [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] má procesor přístup, prostřednictvím <xref:System.Windows.Markup.XmlnsDefinitionAttribute> deklarací v jednotlivých sestaveních. Většina aplikací má výchozí obor názvů XML mapovaný na `http://schemas.microsoft.com/winfx/2006/xaml/presentation` obor názvů, takže předpona je obvykle pouze pro vlastní typy nebo typy mimo tento obor názvů. `propertyName`musí se vyhodnotit jako název vlastnosti existující v `ownerType`. Vlastnost zadaná jako `propertyName` musí být <xref:System.Windows.DependencyProperty>. (Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] připojené vlastnosti jsou implementovány jako vlastnosti závislosti, takže se tento problém týká pouze vlastních připojených vlastností.)

<a name="indexanim"></a>

### <a name="indexers"></a>Indexery

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" ... />
```

Většina vlastností nebo <xref:System.Windows.Freezable> typů závislosti nepodporuje indexer. Proto je jediné použití pro indexer v cestě animace na mezilehlém místě mezi vlastností, která spouští řetěz v pojmenovaném cíli a závěrečné vlastnosti animace. V zadané syntaxi je `propertyName2`to. Například použití indexeru může být nezbytné <xref:System.Windows.Media.TransformGroup>, pokud je zprostředkující vlastnost kolekce, jako je například, v cestě vlastnosti, jako je například. `RenderTransform.Children[1].Angle`

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a>PropertyPath v kódu

Použití kódu pro <xref:System.Windows.PropertyPath>, včetně postupu konstrukce <xref:System.Windows.PropertyPath>, je dokumentováno v referenčním tématu pro. <xref:System.Windows.PropertyPath>

Obecně <xref:System.Windows.PropertyPath> je navrženo pro použití dvou různých konstruktorů, jeden pro použití vazby a nejjednodušší použití animací a jeden pro komplexní použití animací. Použijte <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signaturu pro použití vazby, kde je objekt řetězec. Použijte <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signaturu pro cesty animací s jedním krokem, kde je objekt <xref:System.Windows.DependencyProperty>. Použijte <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> signaturu pro složité animace. Tento druhý konstruktor používá řetězec tokenu pro první parametr a pole objektů, které vyplňují pozice v řetězci tokenu pro definování vztahu cesty vlastností.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.PropertyPath>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled scénářů](../graphics-multimedia/storyboards-overview.md)
