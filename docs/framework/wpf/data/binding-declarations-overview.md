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
ms.openlocfilehash: 8fea61c463928ee69ef5dd0dfbf107f89c5384ff
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/29/2019
ms.locfileid: "75544464"
---
# <a name="binding-declarations-overview"></a><span data-ttu-id="65b59-102">Přehled deklarací připojení</span><span class="sxs-lookup"><span data-stu-id="65b59-102">Binding Declarations Overview</span></span>

<span data-ttu-id="65b59-103">Toto téma popisuje různé způsoby, jak můžete deklarovat vazbu.</span><span class="sxs-lookup"><span data-stu-id="65b59-103">This topic discusses the different ways you can declare a binding.</span></span>

<a name="Prereq"></a>

## <a name="prerequisites"></a><span data-ttu-id="65b59-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65b59-104">Prerequisites</span></span>

<span data-ttu-id="65b59-105">Před čtením tohoto tématu je důležité, abyste obeznámeni s konceptem a používáním rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="65b59-105">Before reading this topic, it is important that you are familiar with the concept and usage of markup extensions.</span></span> <span data-ttu-id="65b59-106">Další informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="65b59-106">For more information about markup extensions, see [Markup Extensions and WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="65b59-107">Toto téma nepokrývá koncepty datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="65b59-107">This topic does not cover data binding concepts.</span></span> <span data-ttu-id="65b59-108">Diskuzi o konceptech datových vazeb najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65b59-108">For a discussion of data binding concepts, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a><span data-ttu-id="65b59-109">Deklarace vazby v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="65b59-109">Declaring a Binding in XAML</span></span>

<span data-ttu-id="65b59-110">Tato část popisuje, jak deklarovat vazbu v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="65b59-110">This section discusses how to declare a binding in XAML.</span></span>

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a><span data-ttu-id="65b59-111">Použití rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="65b59-111">Markup Extension Usage</span></span>

<span data-ttu-id="65b59-112"><xref:System.Windows.Data.Binding> je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="65b59-112"><xref:System.Windows.Data.Binding> is a markup extension.</span></span> <span data-ttu-id="65b59-113">Použijete-li rozšíření vazby k deklaraci vazby, deklarace se skládá z řady klauzulí za klíčovým slovem `Binding` a oddělené čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="65b59-113">When you use the binding extension to declare a binding, the declaration consists of a series of clauses following the `Binding` keyword and separated by commas (,).</span></span> <span data-ttu-id="65b59-114">Klauzule v deklaraci vazby můžou být v libovolném pořadí a existuje mnoho možných kombinací.</span><span class="sxs-lookup"><span data-stu-id="65b59-114">The clauses in the binding declaration can be in any order and there are many possible combinations.</span></span> <span data-ttu-id="65b59-115">Klauzule jsou páry *název*=*hodnota* , kde *název* je název vlastnosti <xref:System.Windows.Data.Binding> a *hodnota* je hodnota, kterou nastavujete pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="65b59-115">The clauses are *Name*=*Value* pairs where *Name* is the name of the <xref:System.Windows.Data.Binding> property and *Value* is the value you are setting for the property.</span></span>

<span data-ttu-id="65b59-116">Při vytváření řetězců deklarace vazby v kódu musí být připojeny ke konkrétní vlastnosti závislosti cílového objektu.</span><span class="sxs-lookup"><span data-stu-id="65b59-116">When creating binding declaration strings in markup, they must be attached to the specific dependency property of a target object.</span></span> <span data-ttu-id="65b59-117">Následující příklad ukazuje, jak vytvořit vazbu vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> pomocí rozšíření vazby, zadáním vlastností <xref:System.Windows.Data.Binding.Source%2A> a <xref:System.Windows.Data.Binding.Path%2A>.</span><span class="sxs-lookup"><span data-stu-id="65b59-117">The following example shows how to bind the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property using the binding extension, specifying the <xref:System.Windows.Data.Binding.Source%2A> and <xref:System.Windows.Data.Binding.Path%2A> properties.</span></span>

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

<span data-ttu-id="65b59-118">Tímto způsobem můžete zadat většinu vlastností <xref:System.Windows.Data.Binding> třídy.</span><span class="sxs-lookup"><span data-stu-id="65b59-118">You can specify most of the properties of the <xref:System.Windows.Data.Binding> class this way.</span></span> <span data-ttu-id="65b59-119">Další informace o rozšíření vazby a také o seznamu <xref:System.Windows.Data.Binding> vlastností, které nelze nastavit pomocí rozšíření vazby, naleznete v tématu Přehled [rozšíření vazby značek](../advanced/binding-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="65b59-119">For more information about the binding extension as well as for a list of <xref:System.Windows.Data.Binding> properties that cannot be set using the binding extension, see the [Binding Markup Extension](../advanced/binding-markup-extension.md) overview.</span></span>

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a><span data-ttu-id="65b59-120">Syntaxe elementů objektu</span><span class="sxs-lookup"><span data-stu-id="65b59-120">Object Element Syntax</span></span>

<span data-ttu-id="65b59-121">Syntaxe elementu objektu je alternativou k vytvoření deklarace vazby.</span><span class="sxs-lookup"><span data-stu-id="65b59-121">Object element syntax is an alternative to creating the binding declaration.</span></span> <span data-ttu-id="65b59-122">Ve většině případů neexistuje žádná zvláštní výhoda pro použití rozšíření značek nebo syntaxe elementu Object.</span><span class="sxs-lookup"><span data-stu-id="65b59-122">In most cases, there is no particular advantage to using either the markup extension or the object element syntax.</span></span> <span data-ttu-id="65b59-123">V případech, kdy rozšíření značek nepodporuje váš scénář, například pokud je hodnota vlastnosti neřetězcového typu, pro který neexistuje žádný převod typu, je nutné použít syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="65b59-123">However, in cases which the markup extension does not support your scenario, such as when your property value is of a non-string type for which no type conversion exists, you need to use the object element syntax.</span></span>

<span data-ttu-id="65b59-124">Následuje příklad syntaxe prvku objektu a použití rozšíření značek:</span><span class="sxs-lookup"><span data-stu-id="65b59-124">The following is an example of both the object element syntax and the markup extension usage:</span></span>

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

<span data-ttu-id="65b59-125">Příklad váže vlastnost <xref:System.Windows.Controls.TextBlock.Foreground%2A> deklarováním vazby pomocí syntaxe rozšíření.</span><span class="sxs-lookup"><span data-stu-id="65b59-125">The example binds the <xref:System.Windows.Controls.TextBlock.Foreground%2A> property by declaring a binding using the extension syntax.</span></span> <span data-ttu-id="65b59-126">Deklarace vazby pro vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> používá syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="65b59-126">The binding declaration for the <xref:System.Windows.Controls.TextBlock.Text%2A> property uses the object element syntax.</span></span>

<span data-ttu-id="65b59-127">Další informace o různých pojmech naleznete v tématu [syntaxe jazyka XAML podrobněji](../advanced/xaml-syntax-in-detail.md).</span><span class="sxs-lookup"><span data-stu-id="65b59-127">For more information about the different terms, see [XAML Syntax In Detail](../advanced/xaml-syntax-in-detail.md).</span></span>

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a><span data-ttu-id="65b59-128">Více vazeb a PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="65b59-128">MultiBinding and PriorityBinding</span></span>

<span data-ttu-id="65b59-129"><xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují syntaxi rozšíření XAML.</span><span class="sxs-lookup"><span data-stu-id="65b59-129"><xref:System.Windows.Data.MultiBinding> and <xref:System.Windows.Data.PriorityBinding> do not support the XAML extension syntax.</span></span> <span data-ttu-id="65b59-130">Proto je nutné použít syntaxi elementu Object, pokud deklarujete <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="65b59-130">Therefore, you must use the object element syntax if you are declaring a <xref:System.Windows.Data.MultiBinding> or a <xref:System.Windows.Data.PriorityBinding> in XAML.</span></span>

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a><span data-ttu-id="65b59-131">Vytvoření vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="65b59-131">Creating a Binding in Code</span></span>

<span data-ttu-id="65b59-132">Dalším způsobem, jak zadat vazbu, je nastavit vlastnosti přímo na objekt <xref:System.Windows.Data.Binding> v kódu.</span><span class="sxs-lookup"><span data-stu-id="65b59-132">Another way to specify a binding is to set properties directly on a <xref:System.Windows.Data.Binding> object in code.</span></span> <span data-ttu-id="65b59-133">Následující příklad ukazuje, jak vytvořit objekt <xref:System.Windows.Data.Binding> a zadat vlastnosti v kódu.</span><span class="sxs-lookup"><span data-stu-id="65b59-133">The following example shows how to create a <xref:System.Windows.Data.Binding> object and specify the properties in code.</span></span>  <span data-ttu-id="65b59-134">V tomto příkladu je `TheConverter` objekt, který implementuje rozhraní <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="65b59-134">In this example, `TheConverter` is an object that implements the <xref:System.Windows.Data.IValueConverter> interface.</span></span>

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

<span data-ttu-id="65b59-135">Pokud objekt, který vytváříte, je <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> můžete volat metodu `SetBinding` přímo na svém objektu namísto použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65b59-135">If the object you are binding is a <xref:System.Windows.FrameworkElement> or a <xref:System.Windows.FrameworkContentElement> you can call the `SetBinding` method on your object directly instead of using <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="65b59-136">Příklad naleznete [v tématu Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="65b59-136">For an example, see [Create a Binding in Code](how-to-create-a-binding-in-code.md).</span></span>

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a><span data-ttu-id="65b59-137">Syntaxe cesty vazby</span><span class="sxs-lookup"><span data-stu-id="65b59-137">Binding Path Syntax</span></span>

<span data-ttu-id="65b59-138">Pomocí vlastnosti <xref:System.Windows.Data.Binding.Path%2A> určete zdrojovou hodnotu, se kterou chcete vytvořit propojení:</span><span class="sxs-lookup"><span data-stu-id="65b59-138">Use the <xref:System.Windows.Data.Binding.Path%2A> property to specify the source value you want to bind to:</span></span>

- <span data-ttu-id="65b59-139">V nejjednodušším případě je hodnota vlastnosti <xref:System.Windows.Data.Binding.Path%2A> název vlastnosti zdrojového objektu, který se má použít pro vazbu, jako je například `Path=PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="65b59-139">In the simplest case, the <xref:System.Windows.Data.Binding.Path%2A> property value is the name of the property of the source object to use for the binding, such as `Path=PropertyName`.</span></span>

- <span data-ttu-id="65b59-140">Podvlastnosti vlastnosti lze určit podobnou syntaxí jako v C#.</span><span class="sxs-lookup"><span data-stu-id="65b59-140">Subproperties of a property can be specified by a similar syntax as in C#.</span></span> <span data-ttu-id="65b59-141">Klauzule `Path=ShoppingCart.Order` například nastaví vazbu na podvlastnost `Order` objektu nebo vlastnosti `ShoppingCart`.</span><span class="sxs-lookup"><span data-stu-id="65b59-141">For instance, the clause `Path=ShoppingCart.Order` sets the binding to the subproperty `Order` of the object or property `ShoppingCart`.</span></span>

- <span data-ttu-id="65b59-142">Chcete-li vytvořit propojení s připojenou vlastností, umístěte kolem připojené vlastnosti závorky.</span><span class="sxs-lookup"><span data-stu-id="65b59-142">To bind to an attached property, place parentheses around the attached property.</span></span> <span data-ttu-id="65b59-143">Chcete-li například vytvořit připojení k <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>připojené vlastnosti, syntaxe je `Path=(DockPanel.Dock)`.</span><span class="sxs-lookup"><span data-stu-id="65b59-143">For example, to bind to the attached property <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, the syntax is `Path=(DockPanel.Dock)`.</span></span>

- <span data-ttu-id="65b59-144">Indexery vlastnosti lze zadat v hranatých závorkách za názvem vlastnosti, kde je indexer použit.</span><span class="sxs-lookup"><span data-stu-id="65b59-144">Indexers of a property can be specified within square brackets following the property name where the indexer is applied.</span></span> <span data-ttu-id="65b59-145">Klauzule `Path=ShoppingCart[0]` například nastaví vazbu na index, který odpovídá způsobu, jakým interní indexování vaší vlastnosti zpracovává řetězcový literál "0".</span><span class="sxs-lookup"><span data-stu-id="65b59-145">For instance, the clause `Path=ShoppingCart[0]` sets the binding to the index that corresponds to how your property's internal indexing handles the literal string "0".</span></span> <span data-ttu-id="65b59-146">Jsou podporovány také vnořené indexery.</span><span class="sxs-lookup"><span data-stu-id="65b59-146">Nested indexers are also supported.</span></span>

- <span data-ttu-id="65b59-147">Indexery a podvlastnosti lze kombinovat v klauzuli `Path`; například `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span><span class="sxs-lookup"><span data-stu-id="65b59-147">Indexers and subproperties can be mixed in a `Path` clause; for example, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span></span>

- <span data-ttu-id="65b59-148">Uvnitř indexerů můžete mít více parametrů indexerů oddělených čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="65b59-148">Inside indexers you can have multiple indexer parameters separated by commas (,).</span></span> <span data-ttu-id="65b59-149">Typ každého parametru lze zadat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="65b59-149">The type of each parameter can be specified with parentheses.</span></span> <span data-ttu-id="65b59-150">Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"`, kde `sys` je namapována na `System` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="65b59-150">For example, you can have `Path="[(sys:Int32)42,(sys:Int32)24]"`, where `sys` is mapped to the `System` namespace.</span></span>

- <span data-ttu-id="65b59-151">Když je zdrojem zobrazení kolekce, lze aktuální položku zadat lomítkem (/).</span><span class="sxs-lookup"><span data-stu-id="65b59-151">When the source is a collection view, the current item can be specified with a slash (/).</span></span> <span data-ttu-id="65b59-152">Klauzule `Path=/` například nastaví vazbu na aktuální položku v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="65b59-152">For example, the clause `Path=/` sets the binding to the current item in the view.</span></span> <span data-ttu-id="65b59-153">Pokud je zdrojem kolekce, tato syntaxe určuje aktuální položku výchozího zobrazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="65b59-153">When the source is a collection, this syntax specifies the current item of the default collection view.</span></span>

- <span data-ttu-id="65b59-154">Názvy vlastností a lomítka lze kombinovat pro procházení vlastností, které jsou kolekcemi.</span><span class="sxs-lookup"><span data-stu-id="65b59-154">Property names and slashes can be combined to traverse properties that are collections.</span></span> <span data-ttu-id="65b59-155">Například `Path=/Offices/ManagerName` určuje aktuální položku zdrojové kolekce, která obsahuje vlastnost `Offices`, která je také kolekcí.</span><span class="sxs-lookup"><span data-stu-id="65b59-155">For example, `Path=/Offices/ManagerName` specifies the current item of the source collection, which contains an `Offices` property that is also a collection.</span></span> <span data-ttu-id="65b59-156">Jeho aktuální položka je objekt, který obsahuje vlastnost `ManagerName`.</span><span class="sxs-lookup"><span data-stu-id="65b59-156">Its current item is an object that contains a `ManagerName` property.</span></span>

- <span data-ttu-id="65b59-157">Volitelně lze použít cestu tečky (.) k vytvoření vazby k aktuálnímu zdroji.</span><span class="sxs-lookup"><span data-stu-id="65b59-157">Optionally, a period (.) path can be used to bind to the current source.</span></span> <span data-ttu-id="65b59-158">Například `Text="{Binding}"` je ekvivalentem `Text="{Binding Path=.}"`.</span><span class="sxs-lookup"><span data-stu-id="65b59-158">For example, `Text="{Binding}"` is equivalent to `Text="{Binding Path=.}"`.</span></span>

### <a name="escaping-mechanism"></a><span data-ttu-id="65b59-159">Mechanismus uvozovacího uvozovacího mechanismu</span><span class="sxs-lookup"><span data-stu-id="65b59-159">Escaping Mechanism</span></span>

- <span data-ttu-id="65b59-160">Uvnitř indexerů ([]) znak stříšky (^) řídí další znak.</span><span class="sxs-lookup"><span data-stu-id="65b59-160">Inside indexers ([ ]), the caret character (^) escapes the next character.</span></span>

- <span data-ttu-id="65b59-161">Pokud nastavíte <xref:System.Windows.Data.Binding.Path%2A> v jazyce XAML, budete také muset řídicí (pomocí entit XML) určit určité znaky, které jsou speciální pro definici jazyka XML:</span><span class="sxs-lookup"><span data-stu-id="65b59-161">If you set <xref:System.Windows.Data.Binding.Path%2A> in XAML, you also need to escape (using XML entities) certain characters that are special to the XML language definition:</span></span>

  - <span data-ttu-id="65b59-162">Pomocí `&amp;` vydejte znak "&".</span><span class="sxs-lookup"><span data-stu-id="65b59-162">Use `&amp;` to escape the character "&".</span></span>

  - <span data-ttu-id="65b59-163">Pomocí `&gt;` zařídí koncovou značku ">".</span><span class="sxs-lookup"><span data-stu-id="65b59-163">Use `&gt;` to escape the end tag ">".</span></span>

- <span data-ttu-id="65b59-164">Pokud navíc popíšete celou vazbu v atributu pomocí syntaxe rozšíření značek, je nutné řídicí znaky (pomocí zpětného lomítka \\), které jsou speciální pro analyzátor rozšíření značek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="65b59-164">Additionally, if you describe the entire binding in an attribute using the markup extension syntax, you need to escape (using backslash \\) characters that are special to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] markup extension parser:</span></span>

  - <span data-ttu-id="65b59-165">Zpětné lomítko (\\) je řídicí znak samotný.</span><span class="sxs-lookup"><span data-stu-id="65b59-165">Backslash (\\) is the escape character itself.</span></span>

  - <span data-ttu-id="65b59-166">Symbol rovná se (=) odděluje název vlastnosti od hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="65b59-166">The equal sign (=) separates property name from property value.</span></span>

  - <span data-ttu-id="65b59-167">Čárka (,) odděluje vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="65b59-167">Comma (,) separates properties.</span></span>

  - <span data-ttu-id="65b59-168">Pravá složená závorka (}) je koncem rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="65b59-168">The right curly brace (}) is the end of a markup extension.</span></span>

<a name="Default"></a>

## <a name="default-behaviors"></a><span data-ttu-id="65b59-169">Výchozí chování</span><span class="sxs-lookup"><span data-stu-id="65b59-169">Default Behaviors</span></span>

<span data-ttu-id="65b59-170">Výchozí chování je následující, pokud není uvedeno v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="65b59-170">The default behavior is as follows if not specified in the declaration.</span></span>

- <span data-ttu-id="65b59-171">Vytvoří se výchozí převaděč, který se pokusí provést převod typu mezi zdrojovou a cílovou hodnotou vazby.</span><span class="sxs-lookup"><span data-stu-id="65b59-171">A default converter is created that tries to do a type conversion between the binding source value and the binding target value.</span></span> <span data-ttu-id="65b59-172">Pokud převod nelze provést, výchozí převaděč vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="65b59-172">If a conversion cannot be made, the default converter returns `null`.</span></span>

- <span data-ttu-id="65b59-173">Pokud nenastavíte <xref:System.Windows.Data.Binding.ConverterCulture%2A>, modul vazby používá vlastnost `Language` cílového objektu vazby.</span><span class="sxs-lookup"><span data-stu-id="65b59-173">If you do not set <xref:System.Windows.Data.Binding.ConverterCulture%2A>, the binding engine uses the `Language` property of the binding target object.</span></span> <span data-ttu-id="65b59-174">V jazyce XAML je tato hodnota nastavena na "en-US" nebo dědí hodnotu z kořenového prvku (nebo libovolného elementu) stránky, pokud byla jedna explicitně nastavena.</span><span class="sxs-lookup"><span data-stu-id="65b59-174">In XAML, this defaults to "en-US" or inherits the value from the root element (or any element) of the page, if one has been explicitly set.</span></span>

- <span data-ttu-id="65b59-175">Dokud vazba již má kontext dat (například zděděný datový kontext z nadřazeného elementu) a jakákoliv položka nebo kolekce vrácená tímto kontextem je vhodná pro vazbu bez nutnosti úpravy cesty, deklarace vazby nemůže mít žádné klauzule vůbec: `{Binding}` to je často způsob, jakým je vazba určena pro stylování dat, kde vazba funguje na kolekci.</span><span class="sxs-lookup"><span data-stu-id="65b59-175">As long as the binding already has a data context (for instance, the inherited data context coming from a parent element), and whatever item or collection being returned by that context is appropriate for binding without requiring further path modification, a binding declaration can have no clauses at all: `{Binding}` This is often the way a binding is specified for data styling, where the binding acts upon a collection.</span></span> <span data-ttu-id="65b59-176">Další informace naleznete v části "celé objekty používané jako zdroj vazby" v tématu [Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65b59-176">For more information, see the "Entire Objects Used as a Binding Source" section in the [Binding Sources Overview](binding-sources-overview.md).</span></span>

- <span data-ttu-id="65b59-177">Výchozí <xref:System.Windows.Data.Binding.Mode%2A> se v závislosti na vlastnosti závislosti, která je vázaná, liší.</span><span class="sxs-lookup"><span data-stu-id="65b59-177">The default <xref:System.Windows.Data.Binding.Mode%2A> varies between one-way and two-way depending on the dependency property that is being bound.</span></span> <span data-ttu-id="65b59-178">Režim vazby můžete vždy deklarovat explicitně, aby bylo zajištěno, že vaše vazba bude mít požadované chování.</span><span class="sxs-lookup"><span data-stu-id="65b59-178">You can always declare the binding mode explicitly to ensure that your binding has the desired behavior.</span></span> <span data-ttu-id="65b59-179">Obecně platí, že uživatelsky upravitelné vlastnosti ovládacího prvku, jako je například <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, jsou ve výchozím nastavení obousměrné vazby, zatímco většina ostatních vlastností je nastavena jako jednosměrná vazba.</span><span class="sxs-lookup"><span data-stu-id="65b59-179">In general, user-editable control properties, such as <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, default to two-way bindings, whereas most other properties default to one-way bindings.</span></span>

- <span data-ttu-id="65b59-180">Výchozí hodnota <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> se v závislosti na vlastnosti vázané závislosti taky liší od <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> a <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="65b59-180">The default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value varies between <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> and <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> depending on the bound dependency property as well.</span></span> <span data-ttu-id="65b59-181">Výchozí hodnota pro většinu vlastností závislosti je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco vlastnost <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="65b59-181">The default value for most dependency properties is <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, while the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property has a default value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span>

## <a name="see-also"></a><span data-ttu-id="65b59-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65b59-182">See also</span></span>

- [<span data-ttu-id="65b59-183">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="65b59-183">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="65b59-184">Postupy</span><span class="sxs-lookup"><span data-stu-id="65b59-184">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="65b59-185">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="65b59-185">Data Binding</span></span>](../advanced/optimizing-performance-data-binding.md)
- [<span data-ttu-id="65b59-186">PropertyPath – syntaxe v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="65b59-186">PropertyPath XAML Syntax</span></span>](../advanced/propertypath-xaml-syntax.md)
