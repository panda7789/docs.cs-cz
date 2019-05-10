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
ms.openlocfilehash: 3cf128a8d05dbc089f2b481da6b51865b419e25c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754456"
---
# <a name="binding-declarations-overview"></a><span data-ttu-id="3ac64-102">Přehled deklarací připojení</span><span class="sxs-lookup"><span data-stu-id="3ac64-102">Binding Declarations Overview</span></span>

<span data-ttu-id="3ac64-103">Toto téma popisuje různé způsoby, jak je možné deklarovat vazbu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-103">This topic discusses the different ways you can declare a binding.</span></span>

<a name="Prereq"></a>

## <a name="prerequisites"></a><span data-ttu-id="3ac64-104">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ac64-104">Prerequisites</span></span>

<span data-ttu-id="3ac64-105">Před čtením tohoto tématu, je důležité, že máte zkušenosti s koncept a používání rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3ac64-105">Before reading this topic, it is important that you are familiar with the concept and usage of markup extensions.</span></span> <span data-ttu-id="3ac64-106">Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="3ac64-106">For more information about markup extensions, see [Markup Extensions and WPF XAML](../advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="3ac64-107">Toto téma nepopisuje koncepty vazeb data.</span><span class="sxs-lookup"><span data-stu-id="3ac64-107">This topic does not cover data binding concepts.</span></span> <span data-ttu-id="3ac64-108">Diskuzi o koncepty vazeb dat, naleznete v tématu [Data Binding Overview](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3ac64-108">For a discussion of data binding concepts, see [Data Binding Overview](data-binding-overview.md).</span></span>

<a name="BindinginXAML"></a>

## <a name="declaring-a-binding-in-xaml"></a><span data-ttu-id="3ac64-109">Deklarování vazbu v XAML</span><span class="sxs-lookup"><span data-stu-id="3ac64-109">Declaring a Binding in XAML</span></span>

<span data-ttu-id="3ac64-110">Tato část popisuje, jak deklarovat vazbu v XAML.</span><span class="sxs-lookup"><span data-stu-id="3ac64-110">This section discusses how to declare a binding in XAML.</span></span>

<a name="MarkupExtensionSyntax"></a>

### <a name="markup-extension-usage"></a><span data-ttu-id="3ac64-111">Použití rozšíření značky</span><span class="sxs-lookup"><span data-stu-id="3ac64-111">Markup Extension Usage</span></span>

<span data-ttu-id="3ac64-112"><xref:System.Windows.Data.Binding> je rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3ac64-112"><xref:System.Windows.Data.Binding> is a markup extension.</span></span> <span data-ttu-id="3ac64-113">Při použití rozšíření vazby k deklaraci vazby deklarace se skládá z řady klauzule následující `Binding` – klíčové slovo a oddělených čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="3ac64-113">When you use the binding extension to declare a binding, the declaration consists of a series of clauses following the `Binding` keyword and separated by commas (,).</span></span> <span data-ttu-id="3ac64-114">Klauzule v deklaraci vazby může být v libovolném pořadí a existuje mnoho možných kombinací.</span><span class="sxs-lookup"><span data-stu-id="3ac64-114">The clauses in the binding declaration can be in any order and there are many possible combinations.</span></span> <span data-ttu-id="3ac64-115">Klauzule jsou *název*=*hodnotu* dvojice where *název* je název <xref:System.Windows.Data.Binding> vlastnost a *hodnotu* je hodnota, kterou chcete nastavit pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3ac64-115">The clauses are *Name*=*Value* pairs where *Name* is the name of the <xref:System.Windows.Data.Binding> property and *Value* is the value you are setting for the property.</span></span>

<span data-ttu-id="3ac64-116">Při vytváření vazby deklarace řetězců v kódu, musí být připojené k vlastnosti konkrétní závislost cílového objektu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-116">When creating binding declaration strings in markup, they must be attached to the specific dependency property of a target object.</span></span> <span data-ttu-id="3ac64-117">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost pomocí rozšíření vazby, určení <xref:System.Windows.Data.Binding.Source%2A> a <xref:System.Windows.Data.Binding.Path%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3ac64-117">The following example shows how to bind the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property using the binding extension, specifying the <xref:System.Windows.Data.Binding.Source%2A> and <xref:System.Windows.Data.Binding.Path%2A> properties.</span></span>

[!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#L37-L37)]

<span data-ttu-id="3ac64-118">Můžete zadat maximálně vlastnosti <xref:System.Windows.Data.Binding> třídy tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="3ac64-118">You can specify most of the properties of the <xref:System.Windows.Data.Binding> class this way.</span></span> <span data-ttu-id="3ac64-119">Další informace o rozšíření vazby stejně jako u seznamu <xref:System.Windows.Data.Binding> zobrazit vlastnosti, které nelze nastavit pomocí rozšíření vazby [Binding Markup Extension](../advanced/binding-markup-extension.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="3ac64-119">For more information about the binding extension as well as for a list of <xref:System.Windows.Data.Binding> properties that cannot be set using the binding extension, see the [Binding Markup Extension](../advanced/binding-markup-extension.md) overview.</span></span>

<a name="ObjectElementSyntax"></a>

### <a name="object-element-syntax"></a><span data-ttu-id="3ac64-120">Syntaxe elementu objektu</span><span class="sxs-lookup"><span data-stu-id="3ac64-120">Object Element Syntax</span></span>

<span data-ttu-id="3ac64-121">Syntaxe elementu objektu se o alternativu k vytvoření vazby deklarace.</span><span class="sxs-lookup"><span data-stu-id="3ac64-121">Object element syntax is an alternative to creating the binding declaration.</span></span> <span data-ttu-id="3ac64-122">Ve většině případů není žádnou konkrétní výhodu pomocí rozšíření značek nebo syntaxe elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-122">In most cases, there is no particular advantage to using either the markup extension or the object element syntax.</span></span> <span data-ttu-id="3ac64-123">Ale v případech, kdy rozšíření značek nepodporuje váš scénář, například když je hodnota vlastnosti jiné než řetězec typu, pro kterou žádný typ existuje převod, budete muset použít syntaxi elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-123">However, in cases which the markup extension does not support your scenario, such as when your property value is of a non-string type for which no type conversion exists, you need to use the object element syntax.</span></span>

<span data-ttu-id="3ac64-124">Následuje příklad syntaxe elementu objektu a použití rozšíření značky:</span><span class="sxs-lookup"><span data-stu-id="3ac64-124">The following is an example of both the object element syntax and the markup extension usage:</span></span>

[!code-xaml[BindConversionMarkup#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]

<span data-ttu-id="3ac64-125">V příkladu vytvoří vazbu <xref:System.Windows.Controls.TextBlock.Foreground%2A> vlastnost deklarováním vazby pomocí rozšíření syntaxe.</span><span class="sxs-lookup"><span data-stu-id="3ac64-125">The example binds the <xref:System.Windows.Controls.TextBlock.Foreground%2A> property by declaring a binding using the extension syntax.</span></span> <span data-ttu-id="3ac64-126">Deklarace vazby <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost používá syntaxi elementu objektu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-126">The binding declaration for the <xref:System.Windows.Controls.TextBlock.Text%2A> property uses the object element syntax.</span></span>

<span data-ttu-id="3ac64-127">Další informace o různých podmínkách, najdete v části [syntaxe XAML v podrobnosti o](../advanced/xaml-syntax-in-detail.md).</span><span class="sxs-lookup"><span data-stu-id="3ac64-127">For more information about the different terms, see [XAML Syntax In Detail](../advanced/xaml-syntax-in-detail.md).</span></span>

<a name="MBandPB"></a>

### <a name="multibinding-and-prioritybinding"></a><span data-ttu-id="3ac64-128">MultiBinding a rozhraní PriorityBinding</span><span class="sxs-lookup"><span data-stu-id="3ac64-128">MultiBinding and PriorityBinding</span></span>

<span data-ttu-id="3ac64-129"><xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují rozšíření syntaxe XAML.</span><span class="sxs-lookup"><span data-stu-id="3ac64-129"><xref:System.Windows.Data.MultiBinding> and <xref:System.Windows.Data.PriorityBinding> do not support the XAML extension syntax.</span></span> <span data-ttu-id="3ac64-130">Proto musíte použít syntaxi elementu objektu, pokud deklarujete <xref:System.Windows.Data.MultiBinding> nebo <xref:System.Windows.Data.PriorityBinding> v XAML.</span><span class="sxs-lookup"><span data-stu-id="3ac64-130">Therefore, you must use the object element syntax if you are declaring a <xref:System.Windows.Data.MultiBinding> or a <xref:System.Windows.Data.PriorityBinding> in XAML.</span></span>

<a name="BindinginCode"></a>

## <a name="creating-a-binding-in-code"></a><span data-ttu-id="3ac64-131">Vytvoření vazby v kódu</span><span class="sxs-lookup"><span data-stu-id="3ac64-131">Creating a Binding in Code</span></span>

<span data-ttu-id="3ac64-132">Dalším způsobem určení vazby je můžete nastavit vlastnosti přímo <xref:System.Windows.Data.Binding> objekt v kódu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-132">Another way to specify a binding is to set properties directly on a <xref:System.Windows.Data.Binding> object in code.</span></span> <span data-ttu-id="3ac64-133">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Data.Binding> a určení vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="3ac64-133">The following example shows how to create a <xref:System.Windows.Data.Binding> object and specify the properties in code.</span></span>  <span data-ttu-id="3ac64-134">V tomto příkladu `TheConverter` je objekt, který implementuje <xref:System.Windows.Data.IValueConverter> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3ac64-134">In this example, `TheConverter` is an object that implements the <xref:System.Windows.Data.IValueConverter> interface.</span></span>

[!code-csharp[BindConversion#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
[!code-vb[BindConversion#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]

<span data-ttu-id="3ac64-135">Pokud je objekt, jsou vazby <xref:System.Windows.FrameworkElement> nebo <xref:System.Windows.FrameworkContentElement> můžete volat `SetBinding` metodu na objekt přímo namísto použití <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ac64-135">If the object you are binding is a <xref:System.Windows.FrameworkElement> or a <xref:System.Windows.FrameworkContentElement> you can call the `SetBinding` method on your object directly instead of using <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ac64-136">Příklad najdete v tématu [vytvoření vazby v kódu](how-to-create-a-binding-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="3ac64-136">For an example, see [Create a Binding in Code](how-to-create-a-binding-in-code.md).</span></span>

<a name="Path_Syntax"></a>

## <a name="binding-path-syntax"></a><span data-ttu-id="3ac64-137">Syntaxe cesty vazby</span><span class="sxs-lookup"><span data-stu-id="3ac64-137">Binding Path Syntax</span></span>

<span data-ttu-id="3ac64-138">Použití <xref:System.Windows.Data.Binding.Path%2A> vlastnosti k určení zdroje hodnotu, kterou chcete vytvořit vazbu na:</span><span class="sxs-lookup"><span data-stu-id="3ac64-138">Use the <xref:System.Windows.Data.Binding.Path%2A> property to specify the source value you want to bind to:</span></span>

- <span data-ttu-id="3ac64-139">V nejjednodušším případě <xref:System.Windows.Data.Binding.Path%2A> hodnota vlastnosti je názvem vlastnosti zdrojového objektu má použít pro vazbu, například `Path=PropertyName`.</span><span class="sxs-lookup"><span data-stu-id="3ac64-139">In the simplest case, the <xref:System.Windows.Data.Binding.Path%2A> property value is the name of the property of the source object to use for the binding, such as `Path=PropertyName`.</span></span>

- <span data-ttu-id="3ac64-140">Objektu třídy SubProperties vlastnosti je možné zadat tak podobná syntaxe jako v C#.</span><span class="sxs-lookup"><span data-stu-id="3ac64-140">Subproperties of a property can be specified by a similar syntax as in C#.</span></span> <span data-ttu-id="3ac64-141">Například v klauzuli `Path=ShoppingCart.Order` nastaví vazbu pro dílčí vlastnosti `Order` objekt nebo vlastnost `ShoppingCart`.</span><span class="sxs-lookup"><span data-stu-id="3ac64-141">For instance, the clause `Path=ShoppingCart.Order` sets the binding to the subproperty `Order` of the object or property `ShoppingCart`.</span></span>

- <span data-ttu-id="3ac64-142">K vytvoření vazby připojené vlastnosti umístit závorky kolem připojená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3ac64-142">To bind to an attached property, place parentheses around the attached property.</span></span> <span data-ttu-id="3ac64-143">Například pro připojení k připojené vlastnosti <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, syntaxe je `Path=(DockPanel.Dock)`.</span><span class="sxs-lookup"><span data-stu-id="3ac64-143">For example, to bind to the attached property <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, the syntax is `Path=(DockPanel.Dock)`.</span></span>

- <span data-ttu-id="3ac64-144">Indexery vlastností je možné zadat do hranatých závorek za název vlastnosti, kde se indexer použije.</span><span class="sxs-lookup"><span data-stu-id="3ac64-144">Indexers of a property can be specified within square brackets following the property name where the indexer is applied.</span></span> <span data-ttu-id="3ac64-145">Například v klauzuli `Path=ShoppingCart[0]` nastaví vazbu na index, který odpovídá vaší vlastnost interní indexování způsob, jakým zpracovává řetězcový literál "0".</span><span class="sxs-lookup"><span data-stu-id="3ac64-145">For instance, the clause `Path=ShoppingCart[0]` sets the binding to the index that corresponds to how your property's internal indexing handles the literal string "0".</span></span> <span data-ttu-id="3ac64-146">Vnořené indexery jsou také podporovány.</span><span class="sxs-lookup"><span data-stu-id="3ac64-146">Nested indexers are also supported.</span></span>

- <span data-ttu-id="3ac64-147">Indexery a podvlastností lze kombinovat `Path` klauzuli, například `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span><span class="sxs-lookup"><span data-stu-id="3ac64-147">Indexers and subproperties can be mixed in a `Path` clause; for example, `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`</span></span>

- <span data-ttu-id="3ac64-148">Uvnitř indexerů může mít více parametrů indexer oddělených čárkami (,).</span><span class="sxs-lookup"><span data-stu-id="3ac64-148">Inside indexers you can have multiple indexer parameters separated by commas (,).</span></span> <span data-ttu-id="3ac64-149">Každý parametr typu se dá nastavit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="3ac64-149">The type of each parameter can be specified with parentheses.</span></span> <span data-ttu-id="3ac64-150">Například můžete mít `Path="[(sys:Int32)42,(sys:Int32)24]"`, kde `sys` je namapována na `System` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3ac64-150">For example, you can have `Path="[(sys:Int32)42,(sys:Int32)24]"`, where `sys` is mapped to the `System` namespace.</span></span>

- <span data-ttu-id="3ac64-151">Pokud je zdroj zobrazení kolekcí, aktuální položky je možné zadat při lomítka (/).</span><span class="sxs-lookup"><span data-stu-id="3ac64-151">When the source is a collection view, the current item can be specified with a slash (/).</span></span> <span data-ttu-id="3ac64-152">Například v klauzuli `Path=/` nastaví vazbu na aktuální položku v zobrazení.</span><span class="sxs-lookup"><span data-stu-id="3ac64-152">For example, the clause `Path=/` sets the binding to the current item in the view.</span></span> <span data-ttu-id="3ac64-153">Pokud je zdroj kolekce, určuje tato syntaxe aktuální položky výchozí zobrazení kolekce.</span><span class="sxs-lookup"><span data-stu-id="3ac64-153">When the source is a collection, this syntax specifies the current item of the default collection view.</span></span>

- <span data-ttu-id="3ac64-154">Názvy vlastností a lomítka, mohou být kombinovány k procházení vlastnosti, které jsou kolekce.</span><span class="sxs-lookup"><span data-stu-id="3ac64-154">Property names and slashes can be combined to traverse properties that are collections.</span></span> <span data-ttu-id="3ac64-155">Například `Path=/Offices/ManagerName` Určuje aktuální položku zdrojové kolekce, která obsahuje `Offices` vlastnost, která je také kolekce.</span><span class="sxs-lookup"><span data-stu-id="3ac64-155">For example, `Path=/Offices/ManagerName` specifies the current item of the source collection, which contains an `Offices` property that is also a collection.</span></span> <span data-ttu-id="3ac64-156">Jeho aktuální položka je objekt, který obsahuje `ManagerName` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3ac64-156">Its current item is an object that contains a `ManagerName` property.</span></span>

- <span data-ttu-id="3ac64-157">Volitelně cesta tečka (.) je možné vytvořit vazbu na aktuálním zdroji.</span><span class="sxs-lookup"><span data-stu-id="3ac64-157">Optionally, a period (.) path can be used to bind to the current source.</span></span> <span data-ttu-id="3ac64-158">Například `Text="{Binding}"` je ekvivalentní `Text="{Binding Path=.}"`.</span><span class="sxs-lookup"><span data-stu-id="3ac64-158">For example, `Text="{Binding}"` is equivalent to `Text="{Binding Path=.}"`.</span></span>

### <a name="escaping-mechanism"></a><span data-ttu-id="3ac64-159">Útěku mechanismus</span><span class="sxs-lookup"><span data-stu-id="3ac64-159">Escaping Mechanism</span></span>

- <span data-ttu-id="3ac64-160">Uvnitř indexery ([]) řídící znak stříšky (^) další znak.</span><span class="sxs-lookup"><span data-stu-id="3ac64-160">Inside indexers ([ ]), the caret character (^) escapes the next character.</span></span>

- <span data-ttu-id="3ac64-161">Pokud nastavíte <xref:System.Windows.Data.Binding.Path%2A> v XAML, budete potřebovat k uvození (s použitím entity XML) určitých znaků, které jsou pro definice jazyka XML:</span><span class="sxs-lookup"><span data-stu-id="3ac64-161">If you set <xref:System.Windows.Data.Binding.Path%2A> in XAML, you also need to escape (using XML entities) certain characters that are special to the XML language definition:</span></span>

  - <span data-ttu-id="3ac64-162">Použití `&` znaku "&".</span><span class="sxs-lookup"><span data-stu-id="3ac64-162">Use `&` to escape the character "&".</span></span>

  - <span data-ttu-id="3ac64-163">Použití `>` řídicí koncová značka ">".</span><span class="sxs-lookup"><span data-stu-id="3ac64-163">Use `>` to escape the end tag ">".</span></span>

- <span data-ttu-id="3ac64-164">Kromě toho pokud popíšete celé vazby v atributu pomocí syntaxe rozšíření značek, budete muset řídicí (pomocí zpětného lomítka \\) znaky, které jsou pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] analyzátor, který rozšíření:</span><span class="sxs-lookup"><span data-stu-id="3ac64-164">Additionally, if you describe the entire binding in an attribute using the markup extension syntax, you need to escape (using backslash \\) characters that are special to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] markup extension parser:</span></span>

  - <span data-ttu-id="3ac64-165">Zpětné lomítko (\\) je řídicí znak samotný.</span><span class="sxs-lookup"><span data-stu-id="3ac64-165">Backslash (\\) is the escape character itself.</span></span>

  - <span data-ttu-id="3ac64-166">Název vlastnosti rovnítko (=) odděluje od hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3ac64-166">The equal sign (=) separates property name from property value.</span></span>

  - <span data-ttu-id="3ac64-167">Vlastnosti je oddělen čárkou (,).</span><span class="sxs-lookup"><span data-stu-id="3ac64-167">Comma (,) separates properties.</span></span>

  - <span data-ttu-id="3ac64-168">Pravá složená závorka (}) je koncem rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="3ac64-168">The right curly brace (}) is the end of a markup extension.</span></span>

<a name="Default"></a>

## <a name="default-behaviors"></a><span data-ttu-id="3ac64-169">Výchozí chování</span><span class="sxs-lookup"><span data-stu-id="3ac64-169">Default Behaviors</span></span>

<span data-ttu-id="3ac64-170">Výchozí chování následujícím způsobem je, pokud není zadaný v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="3ac64-170">The default behavior is as follows if not specified in the declaration.</span></span>

- <span data-ttu-id="3ac64-171">Výchozí převaděč se vytvoří, který se pokusí provést převod typu mezi zdrojovou hodnotou vazby a cílovou hodnotu vazby.</span><span class="sxs-lookup"><span data-stu-id="3ac64-171">A default converter is created that tries to do a type conversion between the binding source value and the binding target value.</span></span> <span data-ttu-id="3ac64-172">Pokud převod nelze provést, vrátí výchozí převaděč `null`.</span><span class="sxs-lookup"><span data-stu-id="3ac64-172">If a conversion cannot be made, the default converter returns `null`.</span></span>

- <span data-ttu-id="3ac64-173">Pokud nenastavíte <xref:System.Windows.Data.Binding.ConverterCulture%2A>, používá modul vazby `Language` vlastnost cílového objektu vazby.</span><span class="sxs-lookup"><span data-stu-id="3ac64-173">If you do not set <xref:System.Windows.Data.Binding.ConverterCulture%2A>, the binding engine uses the `Language` property of the binding target object.</span></span> <span data-ttu-id="3ac64-174">V XAML výchozí hodnota je "en US" nebo dědí z kořenového elementu (nebo libovolný element) na stránce hodnotu, pokud byla explicitně nastavena.</span><span class="sxs-lookup"><span data-stu-id="3ac64-174">In XAML, this defaults to "en-US" or inherits the value from the root element (or any element) of the page, if one has been explicitly set.</span></span>

- <span data-ttu-id="3ac64-175">Pokud vazba již má kontext dat (například zděděné datového kontextu pocházející z nadřazeného elementu) a libovolné položky nebo kolekci se vrací v tomto kontextu je vhodná pro vazbu bez nutnosti dalších úprav cesty Vazba deklarace nechat bez klauzule vůbec: `{Binding}` To je často způsob, jakým vazbu je určená pro používání stylů data, kdy vazba postupuje podle kolekce.</span><span class="sxs-lookup"><span data-stu-id="3ac64-175">As long as the binding already has a data context (for instance, the inherited data context coming from a parent element), and whatever item or collection being returned by that context is appropriate for binding without requiring further path modification, a binding declaration can have no clauses at all: `{Binding}` This is often the way a binding is specified for data styling, where the binding acts upon a collection.</span></span> <span data-ttu-id="3ac64-176">Další informace najdete v části "Celé objekty použít jako vazbu zdroji" v [Přehled zdrojů vazby](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3ac64-176">For more information, see the "Entire Objects Used as a Binding Source" section in the [Binding Sources Overview](binding-sources-overview.md).</span></span>

- <span data-ttu-id="3ac64-177">Výchozí hodnota <xref:System.Windows.Data.Binding.Mode%2A> se pohybuje mezi jednosměrnou a obousměrnou v závislosti na vlastnosti závislosti svázaný.</span><span class="sxs-lookup"><span data-stu-id="3ac64-177">The default <xref:System.Windows.Data.Binding.Mode%2A> varies between one-way and two-way depending on the dependency property that is being bound.</span></span> <span data-ttu-id="3ac64-178">Vždy je možné deklarovat režimu vazby explicitně, aby se zajistilo, že vaše vazby má požadované chování.</span><span class="sxs-lookup"><span data-stu-id="3ac64-178">You can always declare the binding mode explicitly to ensure that your binding has the desired behavior.</span></span> <span data-ttu-id="3ac64-179">Ve vlastnostech ovládacího prvku Obecné, upravovat uživatele jako například <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, ve výchozím nastavení obousměrné vazby, zatímco většina jiných vlastností ve výchozím nastavení jednosměrné vazby.</span><span class="sxs-lookup"><span data-stu-id="3ac64-179">In general, user-editable control properties, such as <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=nameWithType>, default to two-way bindings, whereas most other properties default to one-way bindings.</span></span>

- <span data-ttu-id="3ac64-180">Výchozí hodnota <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnota se liší mezi <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> a <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> v závislosti na vlastnost vázané závislosti.</span><span class="sxs-lookup"><span data-stu-id="3ac64-180">The default <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> value varies between <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged> and <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> depending on the bound dependency property as well.</span></span> <span data-ttu-id="3ac64-181">Výchozí hodnota pro většinu vlastností závislostí je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span><span class="sxs-lookup"><span data-stu-id="3ac64-181">The default value for most dependency properties is <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, while the <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType> property has a default value of <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>.</span></span>

## <a name="see-also"></a><span data-ttu-id="3ac64-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ac64-182">See also</span></span>

- [<span data-ttu-id="3ac64-183">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="3ac64-183">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="3ac64-184">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="3ac64-184">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="3ac64-185">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="3ac64-185">Data Binding</span></span>](../advanced/optimizing-performance-data-binding.md)
- [<span data-ttu-id="3ac64-186">PropertyPath – syntaxe v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="3ac64-186">PropertyPath XAML Syntax</span></span>](../advanced/propertypath-xaml-syntax.md)
