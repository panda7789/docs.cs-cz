---
title: Přehled deklarací připojení
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
ms.openlocfilehash: bc3a139db80066c9cad5199c7734fe66a8639400
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460028"
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

<xref:System.Windows.Data.Binding> je rozšíření značek. Použijete-li rozšíření vazby k deklaraci vazby, deklarace se skládá z řady klauzulí za klíčovým slovem `Binding` a oddělené čárkami (,). Klauzule v deklaraci vazby můžou být v libovolném pořadí a existuje mnoho možných kombinací. Klauzule jsou páry *název*=*hodnota* , kde *název* je název vlastnosti <xref:System.Windows.Data.Binding> a *hodnota* je hodnota, kterou nastavujete pro vlastnost.

Při vytváření řetězců deklarace vazby v kódu musí být připojeny ke konkrétní vlastnosti závislosti cílového objektu. Následující příklad ukazuje, jak vytvořit vazbu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> pomocí rozšíření vazby, zadáním vlastností <xref:System.Windows.Data.Binding.Source%2A> a <xref:System.Windows.Data.Binding.Path%2A>.

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

Tímto způsobem můžete zadat většinu vlastností <xref:System.Windows.Data.Binding> třídy. Další informace o rozšíření vazby a také o seznamu <xref:System.Windows.Data.Binding> vlastností, které nelze nastavit pomocí rozšíření vazby, naleznete v tématu Přehled [rozšíření vazby značek](../advanced/binding-markup-extension.md) .

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a>Syntaxe elementů objektu

Syntaxe elementu objektu je alternativou k vytvoření deklarace vazby. Ve většině případů neexistuje žádná zvláštní výhoda pro použití rozšíření značek nebo syntaxe elementu Object. V případech, kdy rozšíření značek nepodporuje váš scénář, například pokud je hodnota vlastnosti neřetězcového typu, pro který neexistuje žádný převod typu, je nutné použít syntaxi elementu Object.

Následuje příklad syntaxe prvku objektu a použití rozšíření značek:

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

Příklad váže vlastnost <xref:System.Windows.Controls.TextBlock.Foreground%2A> deklarováním vazby pomocí syntaxe rozšíření. Deklarace vazby pro vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> používá syntaxi elementu Object.

Další informace o různých pojmech naleznete v tématu [syntaxe jazyka XAML podrobněji](../advanced/xaml-syntax-in-detail.md).

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a>Více vazeb a PriorityBinding

<xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují syntaxi rozšíření XAML. Proto je nutné použít syntaxi elementu Object, pokud deklarujete <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v jazyce XAML.

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a>Vytvoření vazby v kódu

Dalším způsobem, jak zadat vazbu, je nastavit vlastnosti přímo na objekt <xref:System.Windows.Data.Binding> v kódu. Následující příklad ukazuje, jak vytvořit objekt <xref:System.Windows.Data.Binding> a zadat vlastnosti v kódu.  V tomto příkladu je `TheConverter` objekt, který implementuje rozhraní <xref:System.Windows.Data.IValueConverter>.

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

Pokud objekt, který vytváříte, je <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> můžete volat metodu `SetBinding` přímo na svém objektu namísto použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Příklad naleznete [v tématu Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md).

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a>Syntaxe cesty vazby

Pomocí vlastnosti <xref:System.Windows.Data.Binding.Path%2A> určete zdrojovou hodnotu, se kterou chcete vytvořit propojení:

- V nejjednodušším případě je hodnota vlastnosti <xref:System.Windows.Data.Binding.Path%2A> název vlastnosti zdrojového objektu, který se má použít pro vazbu, jako je například `Path=PropertyName`.

- Podvlastnosti vlastnosti lze určit podobnou syntaxí jako v C#. Klauzule `Path=ShoppingCart.Order` například nastaví vazbu na podvlastnost `Order` objektu nebo vlastnosti `ShoppingCart`.

- Chcete-li vytvořit propojení s připojenou vlastností, umístěte kolem připojené vlastnosti závorky. Chcete-li například vytvořit připojení k <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>připojené vlastnosti, syntaxe je `Path=(DockPanel.Dock)`.

- Indexery vlastnosti lze zadat v hranatých závorkách za názvem vlastnosti, kde je indexer použit. Klauzule `Path=ShoppingCart[0]` například nastaví vazbu na index, který odpovídá způsobu, jakým interní indexování vaší vlastnosti zpracovává řetězcový literál "0". Jsou podporovány také vnořené indexery.

- Indexery a podvlastnosti lze kombinovat v klauzuli `Path`; například `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`

- Uvnitř indexerů můžete mít více parametrů indexerů oddělených čárkami (,). Typ každého parametru lze zadat pomocí závorek. Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"`, kde `sys` je namapována na `System` obor názvů.

- Když je zdrojem zobrazení kolekce, lze aktuální položku zadat lomítkem (/). Klauzule `Path=/` například nastaví vazbu na aktuální položku v zobrazení. Pokud je zdrojem kolekce, tato syntaxe určuje aktuální položku výchozího zobrazení kolekce.

- Názvy vlastností a lomítka lze kombinovat pro procházení vlastností, které jsou kolekcemi. Například `Path=/Offices/ManagerName` určuje aktuální položku zdrojové kolekce, která obsahuje vlastnost `Offices`, která je také kolekcí. Jeho aktuální položka je objekt, který obsahuje vlastnost `ManagerName`.

- Volitelně lze použít cestu tečky (.) k vytvoření vazby k aktuálnímu zdroji. Například `Text="{Binding}"` je ekvivalentem `Text="{Binding Path=.}"`.

### <a name="escaping-mechanism"></a>Mechanismus uvozovacího uvozovacího mechanismu

- Uvnitř indexerů ([]) znak stříšky (^) řídí další znak.

- Pokud nastavíte <xref:System.Windows.Data.Binding.Path%2A> v jazyce XAML, budete také muset řídicí (pomocí entit XML) určit určité znaky, které jsou speciální pro definici jazyka XML:

  - Pomocí `&` vydejte znak "&".

  - Pomocí `>` zařídí koncovou značku ">".

- Pokud navíc popíšete celou vazbu v atributu pomocí syntaxe rozšíření značek, je nutné řídicí znaky (pomocí zpětného lomítka \\), které jsou speciální pro analyzátor rozšíření značek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

  - Zpětné lomítko (\\) je řídicí znak samotný.

  - Symbol rovná se (=) odděluje název vlastnosti od hodnoty vlastnosti.

  - Čárka (,) odděluje vlastnosti.

  - Pravá složená závorka (}) je koncem rozšíření značek.

<a name="Default"></a>

## <a name="default-behaviors"></a>Výchozí chování

Výchozí chování je následující, pokud není uvedeno v deklaraci.

- Vytvoří se výchozí převaděč, který se pokusí provést převod typu mezi zdrojovou a cílovou hodnotou vazby. Pokud převod nelze provést, výchozí převaděč vrátí `null`.

- Pokud nenastavíte <xref:System.Windows.Data.Binding.ConverterCulture%2A>, modul vazby používá vlastnost `Language` cílového objektu vazby. V jazyce XAML je tato hodnota nastavena na "en-US" nebo dědí hodnotu z kořenového prvku (nebo libovolného elementu) stránky, pokud byla jedna explicitně nastavena.

- Pokud vazba již má kontext dat (například zděděný datový kontext z nadřazeného elementu) a jakákoliv položka nebo kolekce vracené kontextem je vhodná pro vazbu bez nutnosti úpravy cesty, deklarace vazby nemůže mít vůbec žádné klauzule: `{Binding}` to často způsob, jakým je vazba určena pro stylování dat, kde vazba funguje na kolekci. Další informace naleznete v části "celé objekty používané jako zdroj vazby" v tématu [Přehled zdrojů vazby](binding-sources-overview.md).

- Výchozí <xref:System.Windows.Data.Binding.Mode%2A> se v závislosti na vlastnosti závislosti, která je vázaná, liší. Režim vazby můžete vždy deklarovat explicitně, aby bylo zajištěno, že vaše vazba bude mít požadované chování. Obecně platí, že uživatelsky upravitelné vlastnosti ovládacího prvku, jako je například <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, jsou ve výchozím nastavení obousměrné vazby, zatímco většina ostatních vlastností je nastavena jako jednosměrná vazba.

- Výchozí hodnota <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> se v závislosti na vlastnosti vázané závislosti taky liší od <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> a <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. Výchozí hodnota pro většinu vlastností závislosti je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco vlastnost <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.

## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath – syntaxe v jazyce XAML](../advanced/propertypath-xaml-syntax.md)
