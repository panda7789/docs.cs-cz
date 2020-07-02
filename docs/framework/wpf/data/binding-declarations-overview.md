---
title: Přehled deklarací připojení
description: Naučte se deklarovat vazbu v jazyce XAML pro vývoj aplikací v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- markup extensions [WPF]
- data binding [WPF], declarations
- object element syntax [WPF]
- binding data [WPF], declarations
- syntax [WPF], object elements
- binding declarations [WPF]
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
ms.openlocfilehash: 8d4943de0cacb5fe0b5a0c37a5a68f15243ad528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619634"
---
# <a name="binding-declarations-overview"></a>Přehled deklarací připojení

Toto téma popisuje různé způsoby, jak můžete deklarovat vazbu.

<a name="Prereq"></a>

## <a name="prerequisites"></a>Požadavky

Před čtením tohoto tématu je důležité, abyste obeznámeni s konceptem a používáním rozšíření značek. Další informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).

Toto téma nepokrývá koncepty datových vazeb. Diskuzi o konceptech datových vazeb najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a>Deklarace vazby v jazyce XAML

Tato část popisuje, jak deklarovat vazbu v jazyce XAML.

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a>Použití rozšíření značek

<xref:System.Windows.Data.Binding>je rozšíření značek. Použijete-li rozšíření vazby k deklaraci vazby, deklarace se skládá z řady klauzulí za `Binding` klíčovým slovem a oddělených čárkami (,). Klauzule v deklaraci vazby můžou být v libovolném pořadí a existuje mnoho možných kombinací. Klauzule jsou páry *název* = *hodnota* , kde *název* je název <xref:System.Windows.Data.Binding> vlastnosti a *hodnota* je hodnota, kterou nastavujete pro vlastnost.

Při vytváření řetězců deklarace vazby v kódu musí být připojeny ke konkrétní vlastnosti závislosti cílového objektu. Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnosti pomocí rozšíření vazby, zadáním <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.Data.Binding.Path%2A> vlastností a.

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

Tímto způsobem můžete zadat většinu vlastností <xref:System.Windows.Data.Binding> třídy. Další informace o rozšíření vazby a také o seznamu <xref:System.Windows.Data.Binding> vlastností, které nelze nastavit pomocí rozšíření vazby, naleznete v tématu Přehled [rozšíření vazby značek](../advanced/binding-markup-extension.md) .

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Syntaxe elementů objektu

Syntaxe elementu objektu je alternativou k vytvoření deklarace vazby. Ve většině případů neexistuje žádná zvláštní výhoda pro použití rozšíření značek nebo syntaxe elementu Object. V případech, kdy rozšíření značek nepodporuje váš scénář, například pokud je hodnota vlastnosti neřetězcového typu, pro který neexistuje žádný převod typu, je nutné použít syntaxi elementu Object.

Následuje příklad syntaxe prvku objektu a použití rozšíření značek:

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

Tento příklad váže <xref:System.Windows.Controls.TextBlock.Foreground%2A> vlastnost deklarováním vazby pomocí syntaxe rozšíření. Deklarace vazby pro <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost používá syntaxi elementu objektu.

Další informace o různých pojmech naleznete v tématu [syntaxe jazyka XAML podrobněji](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>Více vazeb a PriorityBinding

<xref:System.Windows.Data.MultiBinding>a <xref:System.Windows.Data.PriorityBinding> nepodporují syntaxi rozšíření XAML. Proto je nutné použít syntaxi elementu Object, pokud deklarujete <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v jazyce XAML.

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Vytvoření vazby v kódu

Dalším způsobem určení vazby je nastavení vlastností přímo na <xref:System.Windows.Data.Binding> objekt v kódu. Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Data.Binding> objekt a zadat vlastnosti v kódu.  V tomto příkladu `TheConverter` je objekt, který implementuje <xref:System.Windows.Data.IValueConverter> rozhraní.

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Pokud je objekt, který vytváříte, <xref:System.Windows.FrameworkElement> nebo, můžete <xref:System.Windows.FrameworkContentElement> zavolat `SetBinding` metodu přímo na objekt namísto použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> . Příklad naleznete [v tématu Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Syntaxe cesty vazby

Vlastnost použijte <xref:System.Windows.Data.Binding.Path%2A> k určení zdrojové hodnoty, ke které chcete vytvořit propojení:

- V nejjednodušším případě <xref:System.Windows.Data.Binding.Path%2A> hodnota vlastnosti je název vlastnosti zdrojového objektu, který má být použit pro vazbu, například `Path=PropertyName` .

- Podvlastnosti vlastnosti lze určit podobnou syntaxí jako v jazyce C#. Například klauzule `Path=ShoppingCart.Order` nastaví vazbu na podvlastnost `Order` objektu nebo vlastnosti `ShoppingCart` .

- Chcete-li vytvořit propojení s připojenou vlastností, umístěte kolem připojené vlastnosti závorky. Například pro vytvoření vazby k připojené vlastnosti <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je syntaxe `Path=(DockPanel.Dock)` .

- Indexery vlastnosti lze zadat v hranatých závorkách za názvem vlastnosti, kde je indexer použit. Například klauzule `Path=ShoppingCart[0]` nastaví vazbu na index, který odpovídá způsobu, jakým interní indexování vaší vlastnosti zpracovává řetězcový literál "0". Jsou podporovány také vnořené indexery.

- Indexery a podvlastnosti lze v klauzuli kombinovat `Path` , například`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- Uvnitř indexerů můžete mít více parametrů indexerů oddělených čárkami (,). Typ každého parametru lze zadat pomocí závorek. Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"` , kde `sys` je mapován na `System` obor názvů.

- Když je zdrojem zobrazení kolekce, lze aktuální položku zadat lomítkem (/). Například klauzule `Path=/` nastaví vazbu na aktuální položku v zobrazení. Pokud je zdrojem kolekce, tato syntaxe určuje aktuální položku výchozího zobrazení kolekce.

- Názvy vlastností a lomítka lze kombinovat pro procházení vlastností, které jsou kolekcemi. Například `Path=/Offices/ManagerName` Určuje aktuální položku zdrojové kolekce, která obsahuje `Offices` vlastnost, která je také kolekcí. Jeho aktuální položka je objekt, který obsahuje `ManagerName` vlastnost.

- Volitelně lze použít cestu tečky (.) k vytvoření vazby k aktuálnímu zdroji. Například `Text="{Binding}"` je ekvivalentem k `Text="{Binding Path=.}"` .

### <a name="escaping-mechanism"></a>Mechanismus uvozovacího uvozovacího mechanismu

- Uvnitř indexerů ([]) znak stříšky (^) řídí další znak.

- Pokud jste <xref:System.Windows.Data.Binding.Path%2A> v jazyce XAML nastavili, budete také muset řídicí (pomocí entit XML) určit určité znaky, které jsou speciální pro definici jazyka XML:

  - Použijte `&amp;` k Escape znaku "&".

  - Použijte `&gt;` k ukončení ukončovací značky ">".

- Kromě toho, pokud popíšete celou vazbu v atributu pomocí syntaxe rozšíření značek, je nutné řídicí znaky (pomocí zpětného lomítka \\ ), které jsou speciální pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analyzátor rozšíření značek:

  - Zpětné lomítko ( \\ ) je řídicí znak sám sebe.

  - Symbol rovná se (=) odděluje název vlastnosti od hodnoty vlastnosti.

  - Čárka (,) odděluje vlastnosti.

  - Pravá složená závorka (}) je koncem rozšíření značek.

<a name="Default"></a>

## <a name="default-behaviors"></a>Výchozí chování

Výchozí chování je následující, pokud není uvedeno v deklaraci.

- Vytvoří se výchozí převaděč, který se pokusí provést převod typu mezi zdrojovou a cílovou hodnotou vazby. Pokud převod nelze provést, výchozí převaděč vrátí hodnotu `null` .

- Pokud nenastavíte <xref:System.Windows.Data.Binding.ConverterCulture%2A> , použije modul vazby `Language` vlastnost cílového objektu vazby. V jazyce XAML je tato hodnota nastavena na "en-US" nebo dědí hodnotu z kořenového prvku (nebo libovolného elementu) stránky, pokud byla jedna explicitně nastavena.

- Dokud vazba již má kontext dat (například zděděný kontext dat z nadřazeného elementu) a jakákoliv položka nebo kolekce, kterou tento kontext vrací, je vhodná pro vazbu bez nutnosti úpravy cesty, deklarace vazby nemůže mít žádné klauzule vůbec: `{Binding}` to je často způsob, jakým je vazba určena pro stylování dat, kde vazba funguje na kolekci. Další informace naleznete v části "celé objekty používané jako zdroj vazby" v tématu [Přehled zdrojů vazby](binding-sources-overview.md).

- V <xref:System.Windows.Data.Binding.Mode%2A> závislosti na vlastnosti závislosti, která je vázána, se výchozí hodnota mění mezi jednosměrovým a obousměrným způsobem. Režim vazby můžete vždy deklarovat explicitně, aby bylo zajištěno, že vaše vazba bude mít požadované chování. Obecně platí, že uživatelsky upravitelné vlastnosti ovládacích prvků, jako jsou <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> , jako výchozí pro obousměrné vazby, zatímco většina ostatních vlastností je použita jako výchozí pro jednosměrné vazby.

- Výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota je mezi a v <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> závislosti na vlastnosti vázané závislosti taky odlišná. Výchozí hodnota pro většinu vlastností závislosti je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , zatímco <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> .

## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath – syntaxe v jazyce XAML](../advanced/propertypath-xaml-syntax.md)
