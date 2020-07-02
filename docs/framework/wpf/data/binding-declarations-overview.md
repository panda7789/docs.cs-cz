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
# <a name="binding-declarations-overview"></a><span data-ttu-id="c906c-103">Přehled deklarací připojení</span><span class="sxs-lookup"><span data-stu-id="c906c-103">Binding Declarations Overview</span></span>

<span data-ttu-id="c906c-104">Toto téma popisuje různé způsoby, jak můžete deklarovat vazbu.</span><span class="sxs-lookup"><span data-stu-id="c906c-104">This topic discusses the different ways you can declare a binding.</span></span>

<a name="Prereq"></a>

## <a name="prerequisites"></a><span data-ttu-id="c906c-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c906c-105">Prerequisites</span></span>

<span data-ttu-id="c906c-106">Před čtením tohoto tématu je důležité, abyste obeznámeni s konceptem a používáním rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="c906c-106">Before reading this topic, it is important that you are familiar with the concept and usage of markup extensions.</span></span> <span data-ttu-id="c906c-107">Další informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c906c-107">For more information about markup extensions, see [Markup Extensions and WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="c906c-108">Toto téma nepokrývá koncepty datových vazeb.</span><span class="sxs-lookup"><span data-stu-id="c906c-108">This topic does not cover data binding concepts.</span></span> <span data-ttu-id="c906c-109">Diskuzi o konceptech datových vazeb najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c906c-109">For a discussion of data binding concepts, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a><span data-ttu-id="c906c-110">Deklarace vazby v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="c906c-110">Declaring a Binding in XAML</span></span>

<span data-ttu-id="c906c-111">Tato část popisuje, jak deklarovat vazbu v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="c906c-111">This section discusses how to declare a binding in XAML.</span></span>

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a><span data-ttu-id="c906c-112">Použití rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="c906c-112">Markup Extension Usage</span></span>

<span data-ttu-id="c906c-113"><xref:System.Windows.Data.Binding>je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="c906c-113"><xref:System.Windows.Data.Binding> is a markup extension.</span></span> <span data-ttu-id="c906c-114">Použijete-li rozšíření vazby k deklaraci vazby, deklarace se skládá z řady klauzulí za `Binding` klíčovým slovem a oddělených čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="c906c-114">When you use the binding extension to declare a binding, the declaration consists of a series of clauses following the `Binding` keyword and separated by commas (,).</span></span> <span data-ttu-id="c906c-115">Klauzule v deklaraci vazby můžou být v libovolném pořadí a existuje mnoho možných kombinací.</span><span class="sxs-lookup"><span data-stu-id="c906c-115">The clauses in the binding declaration can be in any order and there are many possible combinations.</span></span> <span data-ttu-id="c906c-116">Klauzule jsou páry *název* = *hodnota* , kde *název* je název <xref:System.Windows.Data.Binding> vlastnosti a *hodnota* je hodnota, kterou nastavujete pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c906c-116">The clauses are *Name*=*Value* pairs where *Name* is the name of the <xref:System.Windows.Data.Binding> property and *Value* is the value you are setting for the property.</span></span>

<span data-ttu-id="c906c-117">Při vytváření řetězců deklarace vazby v kódu musí být připojeny ke konkrétní vlastnosti závislosti cílového objektu.</span><span class="sxs-lookup"><span data-stu-id="c906c-117">When creating binding declaration strings in markup, they must be attached to the specific dependency property of a target object.</span></span> <span data-ttu-id="c906c-118">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnosti pomocí rozšíření vazby, zadáním <xref:System.Windows.Data.Binding.Source%2A> <xref:System.Windows.Data.Binding.Path%2A> vlastností a.</span><span class="sxs-lookup"><span data-stu-id="c906c-118">The following example shows how to bind the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property using the binding extension, specifying the <xref:System.Windows.Data.Binding.Source%2A> and <xref:System.Windows.Data.Binding.Path%2A> properties.</span></span>

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

<span data-ttu-id="c906c-119">Tímto způsobem můžete zadat většinu vlastností <xref:System.Windows.Data.Binding> třídy.</span><span class="sxs-lookup"><span data-stu-id="c906c-119">You can specify most of the properties of the <xref:System.Windows.Data.Binding> class this way.</span></span> <span data-ttu-id="c906c-120">Další informace o rozšíření vazby a také o seznamu <xref:System.Windows.Data.Binding> vlastností, které nelze nastavit pomocí rozšíření vazby, naleznete v tématu Přehled [rozšíření vazby značek](../advanced/binding-markup-extension.md) .</span><span class="sxs-lookup"><span data-stu-id="c906c-120">For more information about the binding extension as well as for a list of <xref:System.Windows.Data.Binding> properties that cannot be set using the binding extension, see the [Binding Markup Extension](../advanced/binding-markup-extension.md) overview.</span></span>

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a><span data-ttu-id="c906c-121">Syntaxe elementů objektu</span><span class="sxs-lookup"><span data-stu-id="c906c-121">Object Element Syntax</span></span>

<span data-ttu-id="c906c-122">Syntaxe elementu objektu je alternativou k vytvoření deklarace vazby.</span><span class="sxs-lookup"><span data-stu-id="c906c-122">Object element syntax is an alternative to creating the binding declaration.</span></span> <span data-ttu-id="c906c-123">Ve většině případů neexistuje žádná zvláštní výhoda pro použití rozšíření značek nebo syntaxe elementu Object.</span><span class="sxs-lookup"><span data-stu-id="c906c-123">In most cases, there is no particular advantage to using either the markup extension or the object element syntax.</span></span> <span data-ttu-id="c906c-124">V případech, kdy rozšíření značek nepodporuje váš scénář, například pokud je hodnota vlastnosti neřetězcového typu, pro který neexistuje žádný převod typu, je nutné použít syntaxi elementu Object.</span><span class="sxs-lookup"><span data-stu-id="c906c-124">However, in cases which the markup extension does not support your scenario, such as when your property value is of a non-string type for which no type conversion exists, you need to use the object element syntax.</span></span>

<span data-ttu-id="c906c-125">Následuje příklad syntaxe prvku objektu a použití rozšíření značek:</span><span class="sxs-lookup"><span data-stu-id="c906c-125">The following is an example of both the object element syntax and the markup extension usage:</span></span>

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

<span data-ttu-id="c906c-126">Tento příklad váže <xref:System.Windows.Controls.TextBlock.Foreground%2A> vlastnost deklarováním vazby pomocí syntaxe rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c906c-126">The example binds the <xref:System.Windows.Controls.TextBlock.Foreground%2A> property by declaring a binding using the extension syntax.</span></span> <span data-ttu-id="c906c-127">Deklarace vazby pro <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost používá syntaxi elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="c906c-127">The binding declaration for the <xref:System.Windows.Controls.TextBlock.Text%2A> property uses the object element syntax.</span></span>

<span data-ttu-id="c906c-128">Další informace o různých pojmech naleznete v tématu [syntaxe jazyka XAML podrobněji](../advanced/xaml-syntax-in-detail.md).</span><span class="sxs-lookup"><span data-stu-id="c906c-128">For more information about the different terms, see [XAML Syntax In Detail](../advanced/xaml-syntax-in-detail.md).</span></span>

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a><span data-ttu-id="c906c-129">Více vazeb a PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="c906c-129">MultiBinding and PriorityBinding</span></span>

<span data-ttu-id="c906c-130"><xref:System.Windows.Data.MultiBinding>a <xref:System.Windows.Data.PriorityBinding> nepodporují syntaxi rozšíření XAML.</span><span class="sxs-lookup"><span data-stu-id="c906c-130"><xref:System.Windows.Data.MultiBinding> and <xref:System.Windows.Data.PriorityBinding> do not support the XAML extension syntax.</span></span> <span data-ttu-id="c906c-131">Proto je nutné použít syntaxi elementu Object, pokud deklarujete <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="c906c-131">Therefore, you must use the object element syntax if you are declaring a <xref:System.Windows.Data.MultiBinding> or a <xref:System.Windows.Data.PriorityBinding> in XAML.</span></span>

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a><span data-ttu-id="c906c-132">Vytvoření vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="c906c-132">Creating a Binding in Code</span></span>

<span data-ttu-id="c906c-133">Dalším způsobem určení vazby je nastavení vlastností přímo na <xref:System.Windows.Data.Binding> objekt v kódu.</span><span class="sxs-lookup"><span data-stu-id="c906c-133">Another way to specify a binding is to set properties directly on a <xref:System.Windows.Data.Binding> object in code.</span></span> <span data-ttu-id="c906c-134">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Data.Binding> objekt a zadat vlastnosti v kódu.</span><span class="sxs-lookup"><span data-stu-id="c906c-134">The following example shows how to create a <xref:System.Windows.Data.Binding> object and specify the properties in code.</span></span>  <span data-ttu-id="c906c-135">V tomto příkladu `TheConverter` je objekt, který implementuje <xref:System.Windows.Data.IValueConverter> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c906c-135">In this example, `TheConverter` is an object that implements the <xref:System.Windows.Data.IValueConverter> interface.</span></span>

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

<span data-ttu-id="c906c-136">Pokud je objekt, který vytváříte, <xref:System.Windows.FrameworkElement> nebo, můžete <xref:System.Windows.FrameworkContentElement> zavolat `SetBinding` metodu přímo na objekt namísto použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c906c-136">If the object you are binding is a <xref:System.Windows.FrameworkElement> or a <xref:System.Windows.FrameworkContentElement> you can call the `SetBinding` method on your object directly instead of using <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c906c-137">Příklad naleznete [v tématu Vytvoření vazby v kódu](how-to-create-a-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="c906c-137">For an example, see [Create a Binding in Code](how-to-create-a-binding-in-code.md).</span></span>

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a><span data-ttu-id="c906c-138">Syntaxe cesty vazby</span><span class="sxs-lookup"><span data-stu-id="c906c-138">Binding Path Syntax</span></span>

<span data-ttu-id="c906c-139">Vlastnost použijte <xref:System.Windows.Data.Binding.Path%2A> k určení zdrojové hodnoty, ke které chcete vytvořit propojení:</span><span class="sxs-lookup"><span data-stu-id="c906c-139">Use the <xref:System.Windows.Data.Binding.Path%2A> property to specify the source value you want to bind to:</span></span>

- <span data-ttu-id="c906c-140">V nejjednodušším případě <xref:System.Windows.Data.Binding.Path%2A> hodnota vlastnosti je název vlastnosti zdrojového objektu, který má být použit pro vazbu, například `Path=PropertyName` .</span><span class="sxs-lookup"><span data-stu-id="c906c-140">In the simplest case, the <xref:System.Windows.Data.Binding.Path%2A> property value is the name of the property of the source object to use for the binding, such as `Path=PropertyName`.</span></span>

- <span data-ttu-id="c906c-141">Podvlastnosti vlastnosti lze určit podobnou syntaxí jako v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c906c-141">Subproperties of a property can be specified by a similar syntax as in C#.</span></span> <span data-ttu-id="c906c-142">Například klauzule `Path=ShoppingCart.Order` nastaví vazbu na podvlastnost `Order` objektu nebo vlastnosti `ShoppingCart` .</span><span class="sxs-lookup"><span data-stu-id="c906c-142">For instance, the clause `Path=ShoppingCart.Order` sets the binding to the subproperty `Order` of the object or property `ShoppingCart`.</span></span>

- <span data-ttu-id="c906c-143">Chcete-li vytvořit propojení s připojenou vlastností, umístěte kolem připojené vlastnosti závorky.</span><span class="sxs-lookup"><span data-stu-id="c906c-143">To bind to an attached property, place parentheses around the attached property.</span></span> <span data-ttu-id="c906c-144">Například pro vytvoření vazby k připojené vlastnosti <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> je syntaxe `Path=(DockPanel.Dock)` .</span><span class="sxs-lookup"><span data-stu-id="c906c-144">For example, to bind to the attached property <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, the syntax is `Path=(DockPanel.Dock)`.</span></span>

- <span data-ttu-id="c906c-145">Indexery vlastnosti lze zadat v hranatých závorkách za názvem vlastnosti, kde je indexer použit.</span><span class="sxs-lookup"><span data-stu-id="c906c-145">Indexers of a property can be specified within square brackets following the property name where the indexer is applied.</span></span> <span data-ttu-id="c906c-146">Například klauzule `Path=ShoppingCart[0]` nastaví vazbu na index, který odpovídá způsobu, jakým interní indexování vaší vlastnosti zpracovává řetězcový literál "0".</span><span class="sxs-lookup"><span data-stu-id="c906c-146">For instance, the clause `Path=ShoppingCart[0]` sets the binding to the index that corresponds to how your property's internal indexing handles the literal string "0".</span></span> <span data-ttu-id="c906c-147">Jsou podporovány také vnořené indexery.</span><span class="sxs-lookup"><span data-stu-id="c906c-147">Nested indexers are also supported.</span></span>

- <span data-ttu-id="c906c-148">Indexery a podvlastnosti lze v klauzuli kombinovat `Path` , například`Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span><span class="sxs-lookup"><span data-stu-id="c906c-148">Indexers and subproperties can be mixed in a `Path` clause; for example, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span></span>

- <span data-ttu-id="c906c-149">Uvnitř indexerů můžete mít více parametrů indexerů oddělených čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="c906c-149">Inside indexers you can have multiple indexer parameters separated by commas (,).</span></span> <span data-ttu-id="c906c-150">Typ každého parametru lze zadat pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="c906c-150">The type of each parameter can be specified with parentheses.</span></span> <span data-ttu-id="c906c-151">Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"` , kde `sys` je mapován na `System` obor názvů.</span><span class="sxs-lookup"><span data-stu-id="c906c-151">For example, you can have `Path="[(sys:Int32)42,(sys:Int32)24]"`, where `sys` is mapped to the `System` namespace.</span></span>

- <span data-ttu-id="c906c-152">Když je zdrojem zobrazení kolekce, lze aktuální položku zadat lomítkem (/).</span><span class="sxs-lookup"><span data-stu-id="c906c-152">When the source is a collection view, the current item can be specified with a slash (/).</span></span> <span data-ttu-id="c906c-153">Například klauzule `Path=/` nastaví vazbu na aktuální položku v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c906c-153">For example, the clause `Path=/` sets the binding to the current item in the view.</span></span> <span data-ttu-id="c906c-154">Pokud je zdrojem kolekce, tato syntaxe určuje aktuální položku výchozího zobrazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="c906c-154">When the source is a collection, this syntax specifies the current item of the default collection view.</span></span>

- <span data-ttu-id="c906c-155">Názvy vlastností a lomítka lze kombinovat pro procházení vlastností, které jsou kolekcemi.</span><span class="sxs-lookup"><span data-stu-id="c906c-155">Property names and slashes can be combined to traverse properties that are collections.</span></span> <span data-ttu-id="c906c-156">Například `Path=/Offices/ManagerName` Určuje aktuální položku zdrojové kolekce, která obsahuje `Offices` vlastnost, která je také kolekcí.</span><span class="sxs-lookup"><span data-stu-id="c906c-156">For example, `Path=/Offices/ManagerName` specifies the current item of the source collection, which contains an `Offices` property that is also a collection.</span></span> <span data-ttu-id="c906c-157">Jeho aktuální položka je objekt, který obsahuje `ManagerName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c906c-157">Its current item is an object that contains a `ManagerName` property.</span></span>

- <span data-ttu-id="c906c-158">Volitelně lze použít cestu tečky (.) k vytvoření vazby k aktuálnímu zdroji.</span><span class="sxs-lookup"><span data-stu-id="c906c-158">Optionally, a period (.) path can be used to bind to the current source.</span></span> <span data-ttu-id="c906c-159">Například `Text="{Binding}"` je ekvivalentem k `Text="{Binding Path=.}"` .</span><span class="sxs-lookup"><span data-stu-id="c906c-159">For example, `Text="{Binding}"` is equivalent to `Text="{Binding Path=.}"`.</span></span>

### <a name="escaping-mechanism"></a><span data-ttu-id="c906c-160">Mechanismus uvozovacího uvozovacího mechanismu</span><span class="sxs-lookup"><span data-stu-id="c906c-160">Escaping Mechanism</span></span>

- <span data-ttu-id="c906c-161">Uvnitř indexerů ([]) znak stříšky (^) řídí další znak.</span><span class="sxs-lookup"><span data-stu-id="c906c-161">Inside indexers ([ ]), the caret character (^) escapes the next character.</span></span>

- <span data-ttu-id="c906c-162">Pokud jste <xref:System.Windows.Data.Binding.Path%2A> v jazyce XAML nastavili, budete také muset řídicí (pomocí entit XML) určit určité znaky, které jsou speciální pro definici jazyka XML:</span><span class="sxs-lookup"><span data-stu-id="c906c-162">If you set <xref:System.Windows.Data.Binding.Path%2A> in XAML, you also need to escape (using XML entities) certain characters that are special to the XML language definition:</span></span>

  - <span data-ttu-id="c906c-163">Použijte `&amp;` k Escape znaku "&".</span><span class="sxs-lookup"><span data-stu-id="c906c-163">Use `&amp;` to escape the character "&".</span></span>

  - <span data-ttu-id="c906c-164">Použijte `&gt;` k ukončení ukončovací značky ">".</span><span class="sxs-lookup"><span data-stu-id="c906c-164">Use `&gt;` to escape the end tag ">".</span></span>

- <span data-ttu-id="c906c-165">Kromě toho, pokud popíšete celou vazbu v atributu pomocí syntaxe rozšíření značek, je nutné řídicí znaky (pomocí zpětného lomítka \\ ), které jsou speciální pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analyzátor rozšíření značek:</span><span class="sxs-lookup"><span data-stu-id="c906c-165">Additionally, if you describe the entire binding in an attribute using the markup extension syntax, you need to escape (using backslash \\) characters that are special to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] markup extension parser:</span></span>

  - <span data-ttu-id="c906c-166">Zpětné lomítko ( \\ ) je řídicí znak sám sebe.</span><span class="sxs-lookup"><span data-stu-id="c906c-166">Backslash (\\) is the escape character itself.</span></span>

  - <span data-ttu-id="c906c-167">Symbol rovná se (=) odděluje název vlastnosti od hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c906c-167">The equal sign (=) separates property name from property value.</span></span>

  - <span data-ttu-id="c906c-168">Čárka (,) odděluje vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c906c-168">Comma (,) separates properties.</span></span>

  - <span data-ttu-id="c906c-169">Pravá složená závorka (}) je koncem rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="c906c-169">The right curly brace (}) is the end of a markup extension.</span></span>

<a name="Default"></a>

## <a name="default-behaviors"></a><span data-ttu-id="c906c-170">Výchozí chování</span><span class="sxs-lookup"><span data-stu-id="c906c-170">Default Behaviors</span></span>

<span data-ttu-id="c906c-171">Výchozí chování je následující, pokud není uvedeno v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c906c-171">The default behavior is as follows if not specified in the declaration.</span></span>

- <span data-ttu-id="c906c-172">Vytvoří se výchozí převaděč, který se pokusí provést převod typu mezi zdrojovou a cílovou hodnotou vazby.</span><span class="sxs-lookup"><span data-stu-id="c906c-172">A default converter is created that tries to do a type conversion between the binding source value and the binding target value.</span></span> <span data-ttu-id="c906c-173">Pokud převod nelze provést, výchozí převaděč vrátí hodnotu `null` .</span><span class="sxs-lookup"><span data-stu-id="c906c-173">If a conversion cannot be made, the default converter returns `null`.</span></span>

- <span data-ttu-id="c906c-174">Pokud nenastavíte <xref:System.Windows.Data.Binding.ConverterCulture%2A> , použije modul vazby `Language` vlastnost cílového objektu vazby.</span><span class="sxs-lookup"><span data-stu-id="c906c-174">If you do not set <xref:System.Windows.Data.Binding.ConverterCulture%2A>, the binding engine uses the `Language` property of the binding target object.</span></span> <span data-ttu-id="c906c-175">V jazyce XAML je tato hodnota nastavena na "en-US" nebo dědí hodnotu z kořenového prvku (nebo libovolného elementu) stránky, pokud byla jedna explicitně nastavena.</span><span class="sxs-lookup"><span data-stu-id="c906c-175">In XAML, this defaults to "en-US" or inherits the value from the root element (or any element) of the page, if one has been explicitly set.</span></span>

- <span data-ttu-id="c906c-176">Dokud vazba již má kontext dat (například zděděný kontext dat z nadřazeného elementu) a jakákoliv položka nebo kolekce, kterou tento kontext vrací, je vhodná pro vazbu bez nutnosti úpravy cesty, deklarace vazby nemůže mít žádné klauzule vůbec: `{Binding}` to je často způsob, jakým je vazba určena pro stylování dat, kde vazba funguje na kolekci.</span><span class="sxs-lookup"><span data-stu-id="c906c-176">As long as the binding already has a data context (for instance, the inherited data context coming from a parent element), and whatever item or collection being returned by that context is appropriate for binding without requiring further path modification, a binding declaration can have no clauses at all: `{Binding}` This is often the way a binding is specified for data styling, where the binding acts upon a collection.</span></span> <span data-ttu-id="c906c-177">Další informace naleznete v části "celé objekty používané jako zdroj vazby" v tématu [Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c906c-177">For more information, see the "Entire Objects Used as a Binding Source" section in the [Binding Sources Overview](binding-sources-overview.md).</span></span>

- <span data-ttu-id="c906c-178">V <xref:System.Windows.Data.Binding.Mode%2A> závislosti na vlastnosti závislosti, která je vázána, se výchozí hodnota mění mezi jednosměrovým a obousměrným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c906c-178">The default <xref:System.Windows.Data.Binding.Mode%2A> varies between one-way and two-way depending on the dependency property that is being bound.</span></span> <span data-ttu-id="c906c-179">Režim vazby můžete vždy deklarovat explicitně, aby bylo zajištěno, že vaše vazba bude mít požadované chování.</span><span class="sxs-lookup"><span data-stu-id="c906c-179">You can always declare the binding mode explicitly to ensure that your binding has the desired behavior.</span></span> <span data-ttu-id="c906c-180">Obecně platí, že uživatelsky upravitelné vlastnosti ovládacích prvků, jako jsou <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType> , jako výchozí pro obousměrné vazby, zatímco většina ostatních vlastností je použita jako výchozí pro jednosměrné vazby.</span><span class="sxs-lookup"><span data-stu-id="c906c-180">In general, user-editable control properties, such as <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, default to two-way bindings, whereas most other properties default to one-way bindings.</span></span>

- <span data-ttu-id="c906c-181">Výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota je mezi a v <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> závislosti na vlastnosti vázané závislosti taky odlišná.</span><span class="sxs-lookup"><span data-stu-id="c906c-181">The default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value varies between <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> and <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> depending on the bound dependency property as well.</span></span> <span data-ttu-id="c906c-182">Výchozí hodnota pro většinu vlastností závislosti je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> , zatímco <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> .</span><span class="sxs-lookup"><span data-stu-id="c906c-182">The default value for most dependency properties is <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, while the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property has a default value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c906c-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c906c-183">See also</span></span>

- [<span data-ttu-id="c906c-184">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="c906c-184">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="c906c-185">– postupy</span><span class="sxs-lookup"><span data-stu-id="c906c-185">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="c906c-186">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="c906c-186">Data Binding</span></span>](../advanced/optimizing-performance-data-binding.md)
- [<span data-ttu-id="c906c-187">PropertyPath – syntaxe v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="c906c-187">PropertyPath XAML Syntax</span></span>](../advanced/propertypath-xaml-syntax.md)
