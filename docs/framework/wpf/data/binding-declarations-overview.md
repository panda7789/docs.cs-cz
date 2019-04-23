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
ms.openlocfilehash: c0fcbc8054272356c39ba7925041ecef05a0322c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165266"
---
# <a name="binding-declarations-overview"></a>Přehled deklarací připojení
Toto téma popisuje různé způsoby, jak je možné deklarovat vazbu.  

<a name="Prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 Před čtením tohoto tématu, je důležité, že máte zkušenosti s koncept a používání rozšíření značek. Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).  
  
 Toto téma nepopisuje koncepty vazeb data. Diskuzi o koncepty vazeb dat, naleznete v tématu [Data Binding Overview](data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>Deklarování vazbu v XAML  
 Tato část popisuje, jak deklarovat vazbu v XAML.  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>Použití rozšíření značky  
 <xref:System.Windows.Data.Binding> je rozšíření značek. Při použití rozšíření vazby k deklaraci vazby deklarace se skládá z řady klauzule následující `Binding` – klíčové slovo a oddělených čárkami (,). Klauzule v deklaraci vazby může být v libovolném pořadí a existuje mnoho možných kombinací. Klauzule jsou *název*=*hodnotu* dvojice where *název* je název <xref:System.Windows.Data.Binding> vlastnost a *hodnotu* je hodnota, kterou chcete nastavit pro vlastnost.  
  
 Při vytváření vazby deklarace řetězců v kódu, musí být připojené k vlastnosti konkrétní závislost cílového objektu. Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost pomocí rozšíření vazby, určení <xref:System.Windows.Data.Binding.Source%2A> a <xref:System.Windows.Data.Binding.Path%2A> vlastnosti.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 Můžete zadat maximálně vlastnosti <xref:System.Windows.Data.Binding> třídy tímto způsobem. Další informace o rozšíření vazby stejně jako u seznamu <xref:System.Windows.Data.Binding> zobrazit vlastnosti, které nelze nastavit pomocí rozšíření vazby [Binding Markup Extension](../advanced/binding-markup-extension.md) Přehled.  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>Syntaxe elementu objektu  
 Syntaxe elementu objektu se o alternativu k vytvoření vazby deklarace. Ve většině případů není žádnou konkrétní výhodu pomocí rozšíření značek nebo syntaxe elementu objektu. Ale v případech, kdy rozšíření značek nepodporuje váš scénář, například když je hodnota vlastnosti jiné než řetězec typu, pro kterou žádný typ existuje převod, budete muset použít syntaxi elementu objektu.  
  
 Následuje příklad syntaxe elementu objektu a použití rozšíření značky:  
  
 [!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 V příkladu vytvoří vazbu <xref:System.Windows.Controls.TextBlock.Foreground%2A> vlastnost deklarováním vazby pomocí rozšíření syntaxe. Deklarace vazby <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost používá syntaxi elementu objektu.  
  
 Další informace o různých podmínkách, najdete v části [syntaxe XAML v podrobnosti o](../advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding a rozhraní PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují rozšíření syntaxe XAML. Proto musíte použít syntaxi elementu objektu, pokud deklarujete <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v XAML.  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>Vytvoření vazby v kódu  
 Dalším způsobem určení vazby je můžete nastavit vlastnosti přímo <xref:System.Windows.Data.Binding> objekt v kódu. Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Data.Binding> a určení vlastností v kódu.  V tomto příkladu `TheConverter` je objekt, který implementuje <xref:System.Windows.Data.IValueConverter> rozhraní.  
  
 [!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 Pokud je objekt, jsou vazby <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> můžete volat `SetBinding` metodu na objekt přímo namísto použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Příklad najdete v tématu [vytvoření vazby v kódu](how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>Syntaxe cesty vazby  
 Použití <xref:System.Windows.Data.Binding.Path%2A> vlastnosti k určení zdroje hodnotu, kterou chcete vytvořit vazbu na:  
  
-   V nejjednodušším případě <xref:System.Windows.Data.Binding.Path%2A> hodnota vlastnosti je názvem vlastnosti zdrojového objektu má použít pro vazbu, například `Path=PropertyName`.  
  
-   Objektu třídy SubProperties vlastnosti je možné zadat tak podobná syntaxe jako v C#. Například v klauzuli `Path=ShoppingCart.Order` nastaví vazbu pro dílčí vlastnosti `Order` objekt nebo vlastnost `ShoppingCart`.  
  
-   K vytvoření vazby připojené vlastnosti umístit závorky kolem připojená vlastnost. Například pro připojení k připojené vlastnosti <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, syntaxe je `Path=(DockPanel.Dock)`.  
  
-   Indexery vlastností je možné zadat do hranatých závorek za název vlastnosti, kde se indexer použije. Například v klauzuli `Path=ShoppingCart[0]` nastaví vazbu na index, který odpovídá vaší vlastnost interní indexování způsob, jakým zpracovává řetězcový literál "0". Vnořené indexery jsou také podporovány.  
  
-   Indexery a podvlastností lze kombinovat `Path` klauzuli, například `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   Uvnitř indexerů může mít více parametrů indexer oddělených čárkami (,). Každý parametr typu se dá nastavit pomocí závorek. Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"`, kde `sys` je namapována na `System` oboru názvů.  
  
-   Pokud je zdroj zobrazení kolekcí, aktuální položky je možné zadat při lomítka (/). Například v klauzuli `Path=/` nastaví vazbu na aktuální položku v zobrazení. Pokud je zdroj kolekce, určuje tato syntaxe aktuální položky výchozí zobrazení kolekce.  
  
-   Názvy vlastností a lomítka, mohou být kombinovány k procházení vlastnosti, které jsou kolekce. Například `Path=/Offices/ManagerName` Určuje aktuální položku zdrojové kolekce, která obsahuje `Offices` vlastnost, která je také kolekce. Jeho aktuální položka je objekt, který obsahuje `ManagerName` vlastnost.  
  
-   Volitelně cesta tečka (.) je možné vytvořit vazbu na aktuálním zdroji. Například `Text="{Binding}"` je ekvivalentní `Text="{Binding Path=.}"`.  
  
### <a name="escaping-mechanism"></a>Útěku mechanismus  
  
-   Uvnitř indexery ([]) řídící znak stříšky (^) další znak.  
  
-   Pokud nastavíte <xref:System.Windows.Data.Binding.Path%2A> v XAML, budete potřebovat k uvození (s použitím entity XML) určitých znaků, které jsou pro definice jazyka XML:  
  
    -   Použití `&` znaku "&".  
  
    -   Použití `>` řídicí koncová značka ">".  
  
-   Kromě toho pokud popíšete celé vazby v atributu pomocí syntaxe rozšíření značek, budete muset řídicí (pomocí zpětného lomítka \\) znaky, které jsou pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analyzátor, který rozšíření:  
  
    -   Zpětné lomítko (\\) je řídicí znak samotný.  
  
    -   Název vlastnosti rovnítko (=) odděluje od hodnoty vlastnosti.  
  
    -   Vlastnosti je oddělen čárkou (,).  
  
    -   Pravá složená závorka (}) je koncem rozšíření značek.  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>Výchozí chování  
 Výchozí chování následujícím způsobem je, pokud není zadaný v deklaraci.  
  
-   Výchozí převaděč se vytvoří, který se pokusí provést převod typu mezi zdrojovou hodnotou vazby a cílovou hodnotu vazby. Pokud převod nelze provést, vrátí výchozí převaděč `null`.  
  
-   Pokud nenastavíte <xref:System.Windows.Data.Binding.ConverterCulture%2A>, používá modul vazby `Language` vlastnost cílového objektu vazby. V XAML výchozí hodnota je "en US" nebo dědí z kořenového elementu (nebo libovolný element) na stránce hodnotu, pokud byla explicitně nastavena.  
  
-   Pokud vazba již má kontext dat (například zděděné datového kontextu pocházející z nadřazeného elementu) a libovolné položky nebo kolekci se vrací v tomto kontextu je vhodná pro vazbu bez nutnosti dalších úprav cesty Vazba deklarace nechat bez klauzule vůbec: `{Binding}` To je často způsob, jakým vazbu je určená pro používání stylů data, kdy vazba postupuje podle kolekce. Další informace najdete v části "Celé objekty použít jako vazbu zdroji" v [Přehled zdrojů vazby](binding-sources-overview.md).  
  
-   Výchozí hodnota <xref:System.Windows.Data.Binding.Mode%2A> se pohybuje mezi jednosměrnou a obousměrnou v závislosti na vlastnosti závislosti svázaný. Vždy je možné deklarovat režimu vazby explicitně, aby se zajistilo, že vaše vazby má požadované chování. Ve vlastnostech ovládacího prvku Obecné, upravovat uživatele jako například <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, ve výchozím nastavení obousměrné vazby, zatímco většina jiných vlastností ve výchozím nastavení jednosměrné vazby.  
  
-   Výchozí hodnota <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota se liší mezi <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> a <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> v závislosti na vlastnost vázané závislosti. Výchozí hodnota pro většinu vlastností závislostí je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
- [Datová vazba](../advanced/optimizing-performance-data-binding.md)
- [PropertyPath – syntaxe v jazyce XAML](../advanced/propertypath-xaml-syntax.md)
