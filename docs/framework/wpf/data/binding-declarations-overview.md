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
ms.openlocfilehash: a8652648e1ac9da96a027f9aa56f0eee40cbaf09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557209"
---
# <a name="binding-declarations-overview"></a>Přehled deklarací připojení
Toto téma popisuje různé způsoby můžou deklarovat vazbu.  
  
 
  
<a name="Prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 Než si přečtete v tomto tématu, je důležité, že jste obeznámeni s koncept a používání rozšíření značek. Další informace o rozšíření značek najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Toto téma nepopisuje koncepty vazby data. Informace o konceptech vazby dat, najdete v části [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## <a name="declaring-a-binding-in-xaml"></a>Deklarování vazbu v jazyce XAML  
 Tato část popisuje, jak deklarovat vazbu v jazyce XAML.  
  
<a name="MarkupExtensionSyntax"></a>   
### <a name="markup-extension-usage"></a>Použití rozšíření značek  
 <xref:System.Windows.Data.Binding> je rozšíření značek. Pokud použijete rozšíření vazby deklarovat vazbu, deklaraci se skládá z řady klauzule následující `Binding` – klíčové slovo a oddělených čárkami (,). Klauzule v deklaraci vazba může být v libovolném pořadí a nejsou počet možných kombinací. Jsou klauzulích *název*=*hodnotu* páry kde *název* je název <xref:System.Windows.Data.Binding> vlastnost a *hodnota* je hodnota, kterou nastavíte pro vlastnost.  
  
 Při vytváření vazby deklarace řetězců v kódu, musí být připojené k konkrétní závislost vlastnosti cílového objektu. Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost pomocí rozšíření vazby, určení <xref:System.Windows.Data.Binding.Source%2A> a <xref:System.Windows.Data.Binding.Path%2A> vlastnosti.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]  
  
 Zadávat lze většinu vlastností <xref:System.Windows.Data.Binding> třída tímto způsobem. Další informace o rozšíření vazby také jako seznam <xref:System.Windows.Data.Binding> najdete v části vlastnosti, které se nedají nastavit pomocí rozšíření vazby [vazba – rozšíření značek](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) Přehled.  
  
<a name="ObjectElementSyntax"></a>   
### <a name="object-element-syntax"></a>Syntaxe objektu – Element  
 Syntaxe objektu element představuje alternativu k vytváření vazby deklaraci. Ve většině případů je pomocí rozšíření značek nebo syntaxe element objektu žádné konkrétní výhody. Však v případech, které rozšíření značek nepodporuje váš scénář, například pokud vaše hodnota vlastnosti je jiné než řetězec typu, pro které žádný typ převodu existuje, budete muset použít syntaxe element objektu.  
  
 Následuje příklad syntaxe element objektu a používání rozšíření značek:  
  
 [!code-xaml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 V příkladu váže <xref:System.Windows.Controls.TextBlock.Foreground%2A> vlastnost deklarováním vazbu pomocí syntaxe rozšíření. Vazba deklaraci pro <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost se používá syntaxe objekt elementu.  
  
 Další informace o různé podmínky najdete v tématu [XAML syntaxe v podrobností](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### <a name="multibinding-and-prioritybinding"></a>MultiBinding a PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují rozšíření syntaxe jazyka XAML. Proto musíte použít syntaxi element objektu, pokud jsou deklarace <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v jazyce XAML.  
  
<a name="BindinginCode"></a>   
## <a name="creating-a-binding-in-code"></a>Vytváření vazby v kódu  
 Jiný způsob zadání vazby je přímo na nastavit vlastnosti <xref:System.Windows.Data.Binding> objektu v kódu. Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Data.Binding> objektu a zadání vlastností v kódu.  V tomto příkladu `TheConverter` je objekt, který implementuje <xref:System.Windows.Data.IValueConverter> rozhraní.  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
  
 Pokud je objekt, jsou vazby <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> můžete volat `SetBinding` metodu objektu přímo místo použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>. Příklad, naleznete v části [vytvoření vazby v kódu](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## <a name="binding-path-syntax"></a>Syntaxe cesty vazby  
 Použití <xref:System.Windows.Data.Binding.Path%2A> vlastnosti k určení zdrojové hodnoty, kterou chcete vytvořit vazbu na:  
  
-   V nejjednodušším případě <xref:System.Windows.Data.Binding.Path%2A> hodnota vlastnosti je název vlastnosti Zdrojový objekt, který má používat pro vazbu, jako třeba `Path=PropertyName`.  
  
-   Podvlastnosti vlastnosti lze zadat syntaxí podobné jako v C#. Například v klauzuli `Path=ShoppingCart.Order` nastaví vazbu na dílčí vlastnosti `Order` objekt nebo vlastnost `ShoppingCart`.  
  
-   Pokud chcete vytvořit vazbu k přidružená vlastnost, umístěte připojená vlastnost v závorkách. Chcete-li například vytvořit vazbu na připojená vlastnost <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, syntaxe je `Path=(DockPanel.Dock)`.  
  
-   Indexery vlastnosti lze zadat v rámci hranaté závorky následující název vlastnosti v případě použití indexeru. Například v klauzuli `Path=ShoppingCart[0]` nastaví vazbu na index, který odpovídá vaší vlastnost interní indexování jak zpracovává řetězcového literálu "0". Vnořené indexery jsou také podporovány.  
  
-   Indexery a podvlastnosti můžete kombinované ve `Path` klauzule, např. `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   Uvnitř indexery může mít několik parametrů indexer oddělených čárkami (,). Typ každý parametr lze zadat v závorkách. Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"`, kde `sys` je namapována na `System` oboru názvů.  
  
-   Pokud je zdroj zobrazení kolekce, lze s aktuální položkou s lomítkem (/). Například v klauzuli `Path=/` nastaví vazby na aktuální položky v zobrazení. Pokud je zdroj kolekce, určuje tato syntaxe s aktuální položkou výchozí zobrazení kolekce.  
  
-   Názvy vlastností a lomítka lze spojovat procházení vlastnosti, které jsou kolekce. Například `Path=/Offices/ManagerName` určuje s aktuální položkou zdrojové kolekci, která obsahuje `Offices` vlastnost, která je také kolekce. Jeho aktuální položka je objekt, který obsahuje `ManagerName` vlastnost.  
  
-   Volitelně cestu tečka (.) slouží k vytvoření vazby na aktuální zdroj. Například `Text="{Binding}"` je ekvivalentní `Text="{Binding Path=.}"`.  
  
### <a name="escaping-mechanism"></a>Mechanismus uvozovací znaky  
  
-   Uvnitř indexery ([]) nastavení řídicí sekvence znaků pomocí kurzoru (^) další znak.  
  
-   Pokud nastavíte <xref:System.Windows.Data.Binding.Path%2A> v jazyce XAML, budete také muset vyhnuli (s použitím entity XML) určitých znaků, které jsou speciální k definici jazyka XML:  
  
    -   Použití `&` řídicí znak "&".  
  
    -   Použití `>` abyste se vyhnuli koncová značka ">".  
  
-   Kromě toho, pokud jste popisují celý vazby v atributu pomocí rozšíření syntaxe značek, budete muset vyhnuli (pomocí zpětné lomítko \\) znaků, které jsou speciální k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analyzátor značek rozšíření:  
  
    -   Zpětné lomítko (\\) je vlastní řídicí znak.  
  
    -   Rovná se (=) odděluje název vlastnosti z hodnoty vlastnosti.  
  
    -   Čárkou (,) odděluje vlastnosti.  
  
    -   Pravá složená závorka (}) je konci rozšíření značek.  
  
<a name="Default"></a>   
## <a name="default-behaviors"></a>Výchozí chování  
 Výchozí chování je následujícím způsobem, pokud není zadaný v deklaraci.  
  
-   Vytvoří se převaděč výchozí, který se pokouší provést převod typů mezi zdrojové hodnoty vazby a cílová hodnota vazby. Pokud převod nelze provést, vrátí výchozí převaděč `null`.  
  
-   Pokud není nastaveno <xref:System.Windows.Data.Binding.ConverterCulture%2A>, použije modul vazby `Language` vlastnost cílového objektu vazby. V jazyce XAML použije se výchozí hodnota "en US" nebo hodnota dědí z kořenového elementu (nebo libovolný element) na stránce, pokud byla explicitně nastavena.  
  
-   Stejně dlouho jako vazby již má kontext dat (například zděděné kontextu dat pocházejících z nadřazeného elementu) a libovolnou položku nebo kolekce vrácený tohoto kontextu je vhodný pro vazbu bez nutnosti další úpravy cestu, Vazba deklarace může mít žádná klauzule vůbec: `{Binding}` je často způsob vazba je zadán pro určení stylu dat, kde funguje vazbu na kolekce. Další informace najdete v části "Celý objekty použít jako vazby zdroji" v [vazby Přehled zdrojů](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
-   Výchozí hodnota <xref:System.Windows.Data.Binding.Mode%2A> liší jednosměrná a obousměrná v závislosti na vlastnost závislosti, který je právě vázaný. Vždy můžou deklarovat vazby režim explicitně zajistěte, aby vaše vazby toto chování žádoucí. Ve vlastnostech řízení Obecné, nelze upravit uživatele jako například <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, výchozí obousměrné vazby, zatímco většina jiných vlastností výchozí jednosměrné vazby.  
  
-   Výchozí hodnota <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota se liší mezi <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> a <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> v závislosti na vlastnost vázané závislostí. Výchozí hodnota pro většinu vlastností závislostí je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [PropertyPath – syntaxe v jazyce XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)
