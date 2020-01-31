---
title: Úvod do WPF
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: ecdd3b3c24b71917efb0d982d1f23737673622f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744719"
---
# <a name="wpf-overview"></a><span data-ttu-id="65aac-102">Přehled grafického subsystému WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="65aac-102">WPF overview</span></span>

<span data-ttu-id="65aac-103">Windows Presentation Foundation (WPF) umožňuje vytváření klientských aplikací pro Windows s vizuálně poutavými uživatelskými prostředími.</span><span class="sxs-lookup"><span data-stu-id="65aac-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Ukázka uživatelského rozhraní pro zdravotní péče společnosti Contoso](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="65aac-105">Jádrem WPF je modul vykreslování založený na rozlišení a vektorový vykreslovací modul, který je sestaven tak, aby využíval výhody moderního grafického hardwaru.</span><span class="sxs-lookup"><span data-stu-id="65aac-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="65aac-106">WPF rozšiřuje jádro o komplexní sadu funkcí pro vývoj aplikací, které zahrnují jazyk Extensible Application Markup Language (XAML) (XAML), ovládací prvky, datové vazby, rozložení, 2D a 3D grafiku, animace, styly, šablony, dokumenty, multimédia, text a Typografie.</span><span class="sxs-lookup"><span data-stu-id="65aac-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="65aac-107">WPF je součástí .NET, takže můžete sestavovat aplikace, které zahrnují další prvky rozhraní .NET API.</span><span class="sxs-lookup"><span data-stu-id="65aac-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="65aac-108">Tento přehled je určený pro Newcomers a pokrývá klíčové funkce a koncepty WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="65aac-109">Program s WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-109">Program with WPF</span></span>

<span data-ttu-id="65aac-110">WPF existuje jako podmnožina typů .NET, které jsou (ve většině částí) nacházející se v oboru názvů <xref:System.Windows>.</span><span class="sxs-lookup"><span data-stu-id="65aac-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="65aac-111">Pokud jste už dříve vytvořili aplikace s .NET pomocí spravovaných technologií, jako je ASP.NET a model Windows Forms, měli byste znát základní programovací prostředí WPF. můžete vytvářet instance tříd, nastavovat vlastnosti, volat metody a zpracovávat události pomocí oblíbeného programovacího jazyka .NET, například C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="65aac-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="65aac-112">WPF obsahuje další programovací konstrukce, které vylepšují vlastnosti a události: [vlastnosti závislosti](advanced/dependency-properties-overview.md) a [směrované události](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="65aac-113">Značky a kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="65aac-113">Markup and code-behind</span></span>

<span data-ttu-id="65aac-114">WPF umožňuje vyvíjet aplikace pomocí *značek* i *kódu na pozadí*, což je prostředí, se kterým by ASP.NET vývojáři měli znát.</span><span class="sxs-lookup"><span data-stu-id="65aac-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="65aac-115">Obecně se používá kód XAML k implementaci vzhledu aplikace při použití spravovaných programovacích jazyků (kódu na pozadí) k implementaci jeho chování.</span><span class="sxs-lookup"><span data-stu-id="65aac-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="65aac-116">Toto oddělení vzhledu a chování přináší následující výhody:</span><span class="sxs-lookup"><span data-stu-id="65aac-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="65aac-117">Náklady na vývoj a údržbu jsou sníženy, protože označení specifické pro vzhled není pevně spojeno s kódem specifickým pro chování.</span><span class="sxs-lookup"><span data-stu-id="65aac-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="65aac-118">Vývoj je efektivnější, protože návrháři můžou implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="65aac-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="65aac-119">[Globalizace a lokalizace](advanced/wpf-globalization-and-localization-overview.md) pro aplikace WPF je zjednodušená.</span><span class="sxs-lookup"><span data-stu-id="65aac-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="65aac-120">Revize</span><span class="sxs-lookup"><span data-stu-id="65aac-120">Markup</span></span>

<span data-ttu-id="65aac-121">XAML je značkovací jazyk založený na jazyce XML, který deklarativně implementuje vzhled aplikace.</span><span class="sxs-lookup"><span data-stu-id="65aac-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="65aac-122">Obvykle ho používáte k vytváření oken, dialogových oken, stránek a uživatelských ovládacích prvků a k jejich vyplnění ovládacími prvky, tvary a grafikou.</span><span class="sxs-lookup"><span data-stu-id="65aac-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="65aac-123">Následující příklad používá XAML k implementaci vzhledu okna, které obsahuje jediné tlačítko:</span><span class="sxs-lookup"><span data-stu-id="65aac-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="65aac-124">Konkrétně tento kód XAML definuje okno a tlačítko pomocí prvků `Window` a `Button` v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="65aac-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="65aac-125">Každý element je nakonfigurován s atributy, jako je `Title` atribut `Window` elementu pro určení textu záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="65aac-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="65aac-126">V době běhu převede WPF prvky a atributy, které jsou definovány v označení, na instance tříd WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="65aac-127">Například `Window` element je převeden na instanci <xref:System.Windows.Window> třídy, jejíž vlastnost <xref:System.Windows.Window.Title%2A> je hodnota atributu `Title`.</span><span class="sxs-lookup"><span data-stu-id="65aac-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="65aac-128">Následující obrázek ukazuje uživatelské rozhraní (UI), které je definováno XAML v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="65aac-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Okno obsahující tlačítko](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="65aac-130">Vzhledem k tomu, že XAML je založen na formátu XML, uživatelské rozhraní, které v něm vytvoříte, je sestaveno v hierarchii vnořených elementů, které jsou označovány jako [strom elementu](advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="65aac-131">Strom elementů poskytuje logický a intuitivní způsob, jak vytvořit a spravovat uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65aac-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="65aac-132">Kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="65aac-132">Code-behind</span></span>

<span data-ttu-id="65aac-133">Hlavním chováním aplikace je implementovat funkcionalitu, která reaguje na interakce uživatele, včetně zpracování událostí (například kliknutí na nabídku, panel nástrojů nebo tlačítko) a volání obchodní logiky a logiky přístupu k datům v reakci.</span><span class="sxs-lookup"><span data-stu-id="65aac-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="65aac-134">V jazyce WPF je toto chování implementováno v kódu, který je spojen s označením.</span><span class="sxs-lookup"><span data-stu-id="65aac-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="65aac-135">Tento typ kódu je známý jako kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="65aac-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="65aac-136">Následující příklad ukazuje aktualizovaný kód z předchozího příkladu a kód na pozadí:</span><span class="sxs-lookup"><span data-stu-id="65aac-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox 

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI 
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

<span data-ttu-id="65aac-137">V tomto příkladu kód na pozadí implementuje třídu, která je odvozena od třídy <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="65aac-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="65aac-138">Atribut `x:Class` slouží k přidružení značky ke třídě s kódem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="65aac-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="65aac-139">`InitializeComponent` je volána z konstruktoru třídy kódu na pozadí pro sloučení uživatelského rozhraní, které je definováno v označení pomocí třídy kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="65aac-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="65aac-140">(`InitializeComponent` se vygeneruje při sestavení vaší aplikace, což znamená, že je nemusíte implementovat ručně.) Kombinace `x:Class` a `InitializeComponent` zajistí, že se vaše implementace správně inicializuje při každém vytvoření.</span><span class="sxs-lookup"><span data-stu-id="65aac-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="65aac-141">Třída kódu na pozadí implementuje také obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítka.</span><span class="sxs-lookup"><span data-stu-id="65aac-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="65aac-142">Po kliknutí na tlačítko, obslužná rutina události zobrazí okno se zprávou voláním metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="65aac-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="65aac-143">Následující obrázek ukazuje výsledek při kliknutí na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="65aac-143">The following figure shows the result when the button is clicked:</span></span>

![MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="65aac-145">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="65aac-145">Controls</span></span>

<span data-ttu-id="65aac-146">Uživatelské prostředí, které jsou dodávány aplikačním modelem, jsou konstruovány ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="65aac-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="65aac-147">V rámci WPF je *ovládací prvek* výrazem zastřešující, který se vztahuje na kategorii tříd WPF, které jsou hostovány buď v okně, nebo na stránce, mají uživatelské rozhraní a implementují určité chování.</span><span class="sxs-lookup"><span data-stu-id="65aac-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="65aac-148">Další informace najdete v tématu [ovládací prvky](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="65aac-149">Ovládací prvky WPF podle funkcí</span><span class="sxs-lookup"><span data-stu-id="65aac-149">WPF controls by function</span></span>

<span data-ttu-id="65aac-150">Tady jsou uvedené předdefinované ovládací prvky WPF:</span><span class="sxs-lookup"><span data-stu-id="65aac-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="65aac-151">**Buttons**: <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="65aac-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="65aac-152">**Zobrazení dat**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>a <xref:System.Windows.Controls.TreeView>.</span><span class="sxs-lookup"><span data-stu-id="65aac-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="65aac-153">**Zobrazení data a výběr**: <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="65aac-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="65aac-154">**Dialogová okna**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>a <xref:Microsoft.Win32.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="65aac-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="65aac-155">**Digitální inkoust**: <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter>.</span><span class="sxs-lookup"><span data-stu-id="65aac-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="65aac-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>a <xref:System.Windows.Controls.StickyNoteControl>.</span><span class="sxs-lookup"><span data-stu-id="65aac-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="65aac-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>a <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="65aac-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="65aac-158">**Rozložení**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>a <xref:System.Windows.Controls.WrapPanel>.</span><span class="sxs-lookup"><span data-stu-id="65aac-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="65aac-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>a <xref:System.Windows.Controls.SoundPlayerAction>.</span><span class="sxs-lookup"><span data-stu-id="65aac-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="65aac-160">**Nabídky**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>a <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="65aac-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="65aac-161">**Navigace**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>a <xref:System.Windows.Controls.TabControl>.</span><span class="sxs-lookup"><span data-stu-id="65aac-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="65aac-162">**Výběr**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>a <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="65aac-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="65aac-163">**Informace o uživateli**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>a <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="65aac-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="65aac-164">Vstupní příkazy a</span><span class="sxs-lookup"><span data-stu-id="65aac-164">Input and commands</span></span>

<span data-ttu-id="65aac-165">Ovládací prvky nejčastěji zjišťují a reagují na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="65aac-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="65aac-166">[Vstupní systém WPF](advanced/input-overview.md) používá přímé i směrované události pro podporu zadávání textu, správy fokusu a umístění myši.</span><span class="sxs-lookup"><span data-stu-id="65aac-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="65aac-167">Aplikace často mají komplexní požadavky na vstupy.</span><span class="sxs-lookup"><span data-stu-id="65aac-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="65aac-168">WPF poskytuje [systém příkazů](advanced/commanding-overview.md) , který odděluje akce vstupu uživatele od kódu, který reaguje na tyto akce.</span><span class="sxs-lookup"><span data-stu-id="65aac-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="65aac-169">Rozložení</span><span class="sxs-lookup"><span data-stu-id="65aac-169">Layout</span></span>

<span data-ttu-id="65aac-170">Když vytváříte uživatelské rozhraní, uspořádáte ovládací prvky podle umístění a velikosti pro vytvoření rozložení.</span><span class="sxs-lookup"><span data-stu-id="65aac-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="65aac-171">Klíčovým požadavkem pro jakékoli rozložení je přizpůsobení změn velikosti okna a nastavení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="65aac-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="65aac-172">Namísto vynucení psaní kódu za účelem přizpůsobení rozložení za těchto okolností nabízí WPF pro vás špičkové rozšiřitelné systémové rozložení.</span><span class="sxs-lookup"><span data-stu-id="65aac-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="65aac-173">Základem systému rozložení je relativní umístění, které zvyšuje schopnost přizpůsobit se změnám oken a zobrazení podmínek.</span><span class="sxs-lookup"><span data-stu-id="65aac-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="65aac-174">Kromě toho systém rozložení spravuje vyjednávání mezi ovládacími prvky pro určení rozložení.</span><span class="sxs-lookup"><span data-stu-id="65aac-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="65aac-175">Vyjednávání je dvoustupňový proces: nejprve ovládací prvek oznamuje své nadřazené umístění a velikost, které vyžaduje. za druhé nadřazená položka oznamuje ovládacím prvkům, kolik místa může mít.</span><span class="sxs-lookup"><span data-stu-id="65aac-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="65aac-176">Systém rozložení je vystaven podřízeným ovládacím prvkům prostřednictvím základních tříd WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="65aac-177">Pro společná rozložení, jako jsou mřížky, skládání a ukotvení, WPF obsahuje několik ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="65aac-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="65aac-178"><xref:System.Windows.Controls.Canvas>: podřízené ovládací prvky poskytují své vlastní rozložení.</span><span class="sxs-lookup"><span data-stu-id="65aac-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="65aac-179"><xref:System.Windows.Controls.DockPanel>: podřízené ovládací prvky jsou zarovnány k okrajům panelu.</span><span class="sxs-lookup"><span data-stu-id="65aac-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="65aac-180"><xref:System.Windows.Controls.Grid>: podřízené ovládací prvky jsou umístěny podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="65aac-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="65aac-181"><xref:System.Windows.Controls.StackPanel>: podřízené ovládací prvky jsou skládané buď svisle nebo vodorovně.</span><span class="sxs-lookup"><span data-stu-id="65aac-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="65aac-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: podřízené ovládací prvky jsou virtualizované a uspořádány na jednom řádku, který je buď vodorovně, nebo svisle orientovaný.</span><span class="sxs-lookup"><span data-stu-id="65aac-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="65aac-183"><xref:System.Windows.Controls.WrapPanel>: podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zabaleny na další řádek, pokud existuje více ovládacích prvků na aktuálním řádku, než umožňuje prostor.</span><span class="sxs-lookup"><span data-stu-id="65aac-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="65aac-184">Následující příklad používá <xref:System.Windows.Controls.DockPanel> k rozložení několika <xref:System.Windows.Controls.TextBox> ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="65aac-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="65aac-185"><xref:System.Windows.Controls.DockPanel> umožňuje podřízeným ovládacím prvkům <xref:System.Windows.Controls.TextBox> sdělit, jak se mají uspořádat.</span><span class="sxs-lookup"><span data-stu-id="65aac-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="65aac-186">K tomu <xref:System.Windows.Controls.DockPanel> implementuje `Dock` připojenou vlastnost, která je vystavena podřízeným ovládacím prvkům, aby každému z nich bylo možné zadat styl ukotvení.</span><span class="sxs-lookup"><span data-stu-id="65aac-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="65aac-187">Vlastnost, která je implementována nadřazeným ovládacím prvkem pro použití podřízenými ovládacími prvky, je konstrukce WPF nazývaná [připojená vlastnost](advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="65aac-188">Následující obrázek ukazuje výsledek kódu XAML v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="65aac-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Stránka DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="65aac-190">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="65aac-190">Data binding</span></span>

<span data-ttu-id="65aac-191">Většina aplikací je vytvořená tak, aby uživatelům poskytovala prostředky k zobrazení a úpravám dat.</span><span class="sxs-lookup"><span data-stu-id="65aac-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="65aac-192">V případě aplikací WPF je pro technologie, jako je SQL Server a ADO .NET, k dispozici práce s daty, která jsou již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="65aac-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="65aac-193">Po otevření dat a jejich načtení do spravovaných objektů aplikace je zahájena pevná práce pro aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="65aac-194">V podstatě to zahrnuje dvě věci:</span><span class="sxs-lookup"><span data-stu-id="65aac-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="65aac-195">Kopírování dat ze spravovaných objektů do ovládacích prvků, kde lze data zobrazit a upravit.</span><span class="sxs-lookup"><span data-stu-id="65aac-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="65aac-196">Zajištění, že se změny provedené u dat pomocí ovládacích prvků zkopírují zpátky do spravovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="65aac-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="65aac-197">Pro zjednodušení vývoje aplikací poskytuje WPF modul datových vazeb k automatickému provedení těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="65aac-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="65aac-198">Základní jednotkou modulu datové vazby je třída <xref:System.Windows.Data.Binding>, jejíž úkolem je vytvořit vazbu ovládacího prvku (cíl vazby) k datovému objektu (zdroj vazby).</span><span class="sxs-lookup"><span data-stu-id="65aac-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="65aac-199">Tento vztah je znázorněný na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="65aac-199">This relationship is illustrated by the following figure:</span></span>

![Základní diagram datových vazeb](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="65aac-201">Další příklad ukazuje, jak vytvořit vazby <xref:System.Windows.Controls.TextBox> k instanci vlastního objektu `Person`.</span><span class="sxs-lookup"><span data-stu-id="65aac-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="65aac-202">`Person` implementace je zobrazená v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="65aac-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="65aac-203">Následující kód váže <xref:System.Windows.Controls.TextBox> k instanci vlastního objektu `Person`:</span><span class="sxs-lookup"><span data-stu-id="65aac-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

<span data-ttu-id="65aac-204">V tomto příkladu je vytvořena instance `Person` třídy v kódu na pozadí a je nastavena jako datový kontext pro `DataBindingWindow`.</span><span class="sxs-lookup"><span data-stu-id="65aac-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="65aac-205">V kódu je vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> svázána s vlastností `Person.Name` (pomocí syntaxe XAML "`{Binding ... }`").</span><span class="sxs-lookup"><span data-stu-id="65aac-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="65aac-206">Tento kód XAML oznamuje, že má WPF navazovat ovládací prvek <xref:System.Windows.Controls.TextBox> na objekt `Person`, který je uložený v vlastnosti <xref:System.Windows.FrameworkElement.DataContext%2A> okna.</span><span class="sxs-lookup"><span data-stu-id="65aac-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="65aac-207">Modul datových vazeb WPF poskytuje další podporu, která zahrnuje ověřování, řazení, filtrování a seskupování.</span><span class="sxs-lookup"><span data-stu-id="65aac-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="65aac-208">Kromě toho datová vazba podporuje použití datových šablon k vytvoření vlastního uživatelského rozhraní pro vázaná data v případě, že uživatelské rozhraní zobrazené standardními ovládacími prvky WPF není vhodné.</span><span class="sxs-lookup"><span data-stu-id="65aac-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="65aac-209">Další informace najdete v tématu [Přehled datových vazeb](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="65aac-210">Grafika</span><span class="sxs-lookup"><span data-stu-id="65aac-210">Graphics</span></span>

<span data-ttu-id="65aac-211">WPF přináší rozsáhlou, škálovatelnou a flexibilní sadu grafických funkcí, které mají následující výhody:</span><span class="sxs-lookup"><span data-stu-id="65aac-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="65aac-212">Grafika nezávislá na **rozlišení a zařízení**.</span><span class="sxs-lookup"><span data-stu-id="65aac-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="65aac-213">Základní jednotkou v grafickém systému WPF je pixel nezávislý na zařízení, který je 1/1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávisle na rozlišení a na zařízení.</span><span class="sxs-lookup"><span data-stu-id="65aac-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="65aac-214">Každé pixely nezávislé na zařízení se automaticky škáluje tak, aby se shodovalo s nastavením bodů na palec (dpi) systému, na kterém se vykreslí.</span><span class="sxs-lookup"><span data-stu-id="65aac-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="65aac-215">**Vylepšená přesnost**.</span><span class="sxs-lookup"><span data-stu-id="65aac-215">**Improved precision**.</span></span> <span data-ttu-id="65aac-216">Systém souřadnic WPF se měří s čísly s plovoucí desetinnou čárkou s dvojitou přesností, nikoli s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="65aac-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="65aac-217">Transformace a hodnoty neprůhlednosti se také vyjadřují jako dvojitá přesnost.</span><span class="sxs-lookup"><span data-stu-id="65aac-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="65aac-218">WPF také podporuje šířku barevné škály (scRGB) a poskytuje integrovanou podporu pro správu vstupů z různých barevných prostorů.</span><span class="sxs-lookup"><span data-stu-id="65aac-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="65aac-219">**Pokročilá podpora grafiky a animací**</span><span class="sxs-lookup"><span data-stu-id="65aac-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="65aac-220">WPF zjednodušuje programování grafiky tím, že vám umožní spravovat animace na pozadí. Nemusíte se starat o zpracování scény, vykreslování smyček a varianty interpolaci.</span><span class="sxs-lookup"><span data-stu-id="65aac-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="65aac-221">Kromě toho WPF poskytuje podporu testování testů a úplnou podporu pro skládání v alfa.</span><span class="sxs-lookup"><span data-stu-id="65aac-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="65aac-222">**Hardwarová akcelerace**.</span><span class="sxs-lookup"><span data-stu-id="65aac-222">**Hardware acceleration**.</span></span> <span data-ttu-id="65aac-223">Grafický systém WPF využívá grafický hardware k minimalizaci využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="65aac-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="65aac-224">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="65aac-224">2D shapes</span></span>

<span data-ttu-id="65aac-225">WPF poskytuje knihovnu běžných 2D nakreslených 2D tvarů, jako jsou obdélníky a tři tečky, které jsou zobrazeny na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="65aac-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Elipsy a obdélníky](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="65aac-227">Zajímavou schopností tvarů je, že nejsou jenom pro zobrazení; obrazce implementují mnoho funkcí, které očekáváte od ovládacích prvků, včetně vstupu klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="65aac-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="65aac-228">Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> událost <xref:System.Windows.Shapes.Ellipse> zpracovávána:</span><span class="sxs-lookup"><span data-stu-id="65aac-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="65aac-229">Následující obrázek ukazuje, co je vyrobeno v předchozím kódu:</span><span class="sxs-lookup"><span data-stu-id="65aac-229">The following figure shows what is produced by the preceding code:</span></span>

![Okno s textem "kliknuli jste na elipsu&#33;"](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="65aac-231">Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="65aac-232">2D geometrií</span><span class="sxs-lookup"><span data-stu-id="65aac-232">2D geometries</span></span>

<span data-ttu-id="65aac-233">2D obrazce, které poskytuje WPF, se týkají standardní sady základních tvarů.</span><span class="sxs-lookup"><span data-stu-id="65aac-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="65aac-234">Je však možné, že budete muset vytvořit vlastní tvary, aby bylo usnadněno navrhování přizpůsobeného uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65aac-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="65aac-235">Pro účely tohoto účelu WPF poskytuje geometrií.</span><span class="sxs-lookup"><span data-stu-id="65aac-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="65aac-236">Následující obrázek ukazuje použití geometrií k vytvoření vlastního tvaru, který lze vykreslit přímo, použít jako štětec nebo použít k Vystřižení jiných tvarů a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="65aac-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="65aac-237">objekty <xref:System.Windows.Shapes.Path> lze použít k vykreslení uzavřených nebo otevřených tvarů, více tvarů a dokonce i zakřivených tvarů.</span><span class="sxs-lookup"><span data-stu-id="65aac-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="65aac-238"><xref:System.Windows.Media.Geometry> objekty lze použít pro oříznutí, testování přístupů a vykreslování 2D grafických dat.</span><span class="sxs-lookup"><span data-stu-id="65aac-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Různá použití cesty](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="65aac-240">Další informace najdete v tématu [geometrie Overview](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="65aac-241">2D efekty</span><span class="sxs-lookup"><span data-stu-id="65aac-241">2D effects</span></span>

<span data-ttu-id="65aac-242">Podmnožina možností WPF 2D zahrnuje vizuální efekty, jako jsou barevné přechody, bitmapy, kresby, Malování s videi, otočení, škálování a zkosení.</span><span class="sxs-lookup"><span data-stu-id="65aac-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="65aac-243">Všechny jsou dosaženy pomocí štětců; Následující obrázek ukazuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="65aac-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Ilustrace různých štětců](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="65aac-245">Další informace najdete v tématu [Přehled štětců WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="65aac-246">Prostorové vykreslování</span><span class="sxs-lookup"><span data-stu-id="65aac-246">3D rendering</span></span>

<span data-ttu-id="65aac-247">WPF také zahrnuje možnosti prostorového vykreslování, které se integrují s 2D grafikou, aby bylo možné vytvářet zajímavější a zajímavá uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65aac-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="65aac-248">Například následující obrázek znázorňuje 2D obrázky vykreslené do 3D tvarů:</span><span class="sxs-lookup"><span data-stu-id="65aac-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Snímek obrazovky ukázka Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="65aac-250">Další informace najdete v tématu [Přehled 3D grafiky](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="65aac-251">Animace</span><span class="sxs-lookup"><span data-stu-id="65aac-251">Animation</span></span>

<span data-ttu-id="65aac-252">Podpora animace WPF umožňuje řídit, protřepání, otočení a zmizení ovládacích prvků, aby bylo možné vytvářet zajímavé přechody stránky a další.</span><span class="sxs-lookup"><span data-stu-id="65aac-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="65aac-253">Můžete animovat většinu tříd WPF, dokonce i vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="65aac-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="65aac-254">Na následujícím obrázku je znázorněna jednoduchá animace v akci:</span><span class="sxs-lookup"><span data-stu-id="65aac-254">The following figure shows a simple animation in action:</span></span>

![Obrázky animované datové krychle](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="65aac-256">Další informace najdete v tématu [Přehled animací](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="65aac-257">Médium</span><span class="sxs-lookup"><span data-stu-id="65aac-257">Media</span></span>

<span data-ttu-id="65aac-258">Jedním ze způsobů, jak vyjádřit bohatou část obsahu, je použití audiovizuálních médií.</span><span class="sxs-lookup"><span data-stu-id="65aac-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="65aac-259">WPF poskytuje speciální podporu pro obrázky, video a zvuk.</span><span class="sxs-lookup"><span data-stu-id="65aac-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="65aac-260">Obrázky</span><span class="sxs-lookup"><span data-stu-id="65aac-260">Images</span></span>

<span data-ttu-id="65aac-261">Obrázky jsou společné pro většinu aplikací a WPF nabízí několik způsobů jejich použití.</span><span class="sxs-lookup"><span data-stu-id="65aac-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="65aac-262">Následující obrázek ukazuje uživatelské rozhraní se seznamem, které obsahuje miniatury obrázků.</span><span class="sxs-lookup"><span data-stu-id="65aac-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="65aac-263">Když je vybraná Miniatura, zobrazí se obrázek v plné velikosti.</span><span class="sxs-lookup"><span data-stu-id="65aac-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Obrázky miniatur a obrázek plné&#45;velikosti](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="65aac-265">Další informace najdete v tématu [Přehled imagí](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="65aac-266">Video a zvuk</span><span class="sxs-lookup"><span data-stu-id="65aac-266">Video and audio</span></span>

<span data-ttu-id="65aac-267">Ovládací prvek <xref:System.Windows.Controls.MediaElement> může přehrávat video i zvuk a je dostatečně flexibilní, aby byl základem pro vlastní přehrávač médií.</span><span class="sxs-lookup"><span data-stu-id="65aac-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="65aac-268">Následující kód XAML implementuje přehrávač médií:</span><span class="sxs-lookup"><span data-stu-id="65aac-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="65aac-269">Okno na následujícím obrázku ukazuje <xref:System.Windows.Controls.MediaElement> ovládací prvek v akci:</span><span class="sxs-lookup"><span data-stu-id="65aac-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Ovládací prvek MediaElement se zvukem a videem](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="65aac-271">Další informace najdete v tématu [grafika a multimédia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="65aac-272">Text a typografie</span><span class="sxs-lookup"><span data-stu-id="65aac-272">Text and typography</span></span>

<span data-ttu-id="65aac-273">Pro usnadnění vysoce kvalitního vykreslování textu nabízí WPF tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="65aac-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="65aac-274">Podpora písma OpenType.</span><span class="sxs-lookup"><span data-stu-id="65aac-274">OpenType font support.</span></span>

- <span data-ttu-id="65aac-275">Vylepšení technologie ClearType.</span><span class="sxs-lookup"><span data-stu-id="65aac-275">ClearType enhancements.</span></span>

- <span data-ttu-id="65aac-276">Vysoký výkon, který využívá hardwarovou akceleraci.</span><span class="sxs-lookup"><span data-stu-id="65aac-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="65aac-277">Integrace textu s médii, grafikou a animací</span><span class="sxs-lookup"><span data-stu-id="65aac-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="65aac-278">Mezinárodní podpora písem a nouzové mechanismy.</span><span class="sxs-lookup"><span data-stu-id="65aac-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="65aac-279">Jako ukázku integrace textu s grafikou ukazuje následující obrázek použití dekorace textu:</span><span class="sxs-lookup"><span data-stu-id="65aac-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Text s různými dekoracemi textu](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="65aac-281">Další informace najdete v tématu [Typografie v Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="65aac-282">Přizpůsobení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-282">Customize WPF apps</span></span>

<span data-ttu-id="65aac-283">Až do tohoto okamžiku jste viděli základní stavební bloky WPF pro vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="65aac-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="65aac-284">Model aplikace použijete k hostování a dodávání obsahu aplikace, který se skládá hlavně z ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="65aac-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="65aac-285">Chcete-li zjednodušit uspořádání ovládacích prvků v uživatelském rozhraní a zajistit, aby bylo uspořádání udržováno v tvář změny velikosti okna a nastavení zobrazení, použijte systém rozložení WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="65aac-286">Vzhledem k tomu, že většina aplikací umožňuje uživatelům pracovat s daty, můžete použít datovou vazbu k omezení práce v rámci integrace uživatelského rozhraní s daty.</span><span class="sxs-lookup"><span data-stu-id="65aac-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="65aac-287">Chcete-li zlepšit vizuální vzhled aplikace, použijte komplexní škálu grafiky, animace a podpory médií, které poskytuje WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="65aac-288">Většinou ale nemusíte vytvářet a spravovat skutečně odlišná a vizuálně působivé uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="65aac-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="65aac-289">Standardní ovládací prvky WPF nemusí být integrovány s požadovaným vzhledem aplikace.</span><span class="sxs-lookup"><span data-stu-id="65aac-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="65aac-290">Data se nemusí zobrazovat v nejúčinnějším způsobu.</span><span class="sxs-lookup"><span data-stu-id="65aac-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="65aac-291">Celkové uživatelské prostředí vaší aplikace nemusí být vhodné pro výchozí vzhled a chování motivů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="65aac-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="65aac-292">V mnoha způsobech prezentace potřebuje vizuální rozšiřitelnost, a to podobně jako jakýkoli jiný typ rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="65aac-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="65aac-293">Z tohoto důvodu WPF poskytuje řadu mechanismů pro vytváření jedinečných uživatelských prostředí, včetně modelu bohatých obsahu pro ovládací prvky, triggery, ovládací prvky a šablony dat, styly, prostředky uživatelského rozhraní a motivy a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="65aac-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="65aac-294">Model obsahu</span><span class="sxs-lookup"><span data-stu-id="65aac-294">Content model</span></span>

<span data-ttu-id="65aac-295">Hlavním účelem většiny ovládacích prvků WPF je zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="65aac-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="65aac-296">V WPF je typ a počet položek, které mohou být obsahem ovládacího prvku, označovány jako *model obsahu*ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="65aac-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="65aac-297">Některé ovládací prvky mohou obsahovat jednu položku a typ obsahu; například obsah <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která je přiřazena vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="65aac-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="65aac-298">Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="65aac-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="65aac-299">Výsledek je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="65aac-299">The following figure shows the result:</span></span>

![Ovládací prvek TextBox, který obsahuje text](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="65aac-301">Jiné ovládací prvky však mohou obsahovat více položek různých typů obsahu; obsah <xref:System.Windows.Controls.Button>určený vlastností <xref:System.Windows.Controls.ContentControl.Content%2A> může obsahovat různé položky, včetně ovládacích prvků rozložení, textu, obrázků a tvarů.</span><span class="sxs-lookup"><span data-stu-id="65aac-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="65aac-302">Následující příklad ukazuje <xref:System.Windows.Controls.Button> s obsahem, který obsahuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a <xref:System.Windows.Controls.MediaElement>:</span><span class="sxs-lookup"><span data-stu-id="65aac-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

<span data-ttu-id="65aac-303">Následující obrázek ukazuje obsah tohoto tlačítka:</span><span class="sxs-lookup"><span data-stu-id="65aac-303">The following figure shows the content of this button:</span></span>

![Tlačítko, které obsahuje více typů obsahu](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="65aac-305">Další informace o typech obsahu, které jsou podporovány různými ovládacími prvky, naleznete v tématu [model obsahu WPF](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="65aac-306">Aktivační procedury</span><span class="sxs-lookup"><span data-stu-id="65aac-306">Triggers</span></span>

<span data-ttu-id="65aac-307">I když hlavní účel kódu XAML je implementovat vzhled aplikace, můžete také použít XAML k implementaci některých aspektů chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="65aac-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="65aac-308">Jedním z příkladů je použití triggerů ke změně vzhledu aplikace na základě interakcí uživatelů.</span><span class="sxs-lookup"><span data-stu-id="65aac-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="65aac-309">Další informace najdete v tématu [styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="65aac-310">Šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="65aac-310">Control templates</span></span>

<span data-ttu-id="65aac-311">Výchozí uživatelská rozhraní pro ovládací prvky WPF jsou obvykle vytvořena z jiných ovládacích prvků a tvarů.</span><span class="sxs-lookup"><span data-stu-id="65aac-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="65aac-312">Například <xref:System.Windows.Controls.Button> se skládá z ovládacích prvků <xref:Microsoft.Windows.Themes.ButtonChrome> a <xref:System.Windows.Controls.ContentPresenter>.</span><span class="sxs-lookup"><span data-stu-id="65aac-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="65aac-313"><xref:Microsoft.Windows.Themes.ButtonChrome> poskytuje standardní vzhled tlačítka, zatímco <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka, jak je určeno vlastností <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="65aac-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="65aac-314">Někdy se může stát, že výchozí vzhled ovládacího prvku bude incongruent s celkovým vzhledem aplikace.</span><span class="sxs-lookup"><span data-stu-id="65aac-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="65aac-315">V takovém případě můžete použít <xref:System.Windows.Controls.ControlTemplate> ke změně vzhledu uživatelského rozhraní ovládacího prvku, aniž byste museli měnit jeho obsah a chování.</span><span class="sxs-lookup"><span data-stu-id="65aac-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="65aac-316">Následující příklad ukazuje, jak změnit vzhled <xref:System.Windows.Controls.Button> pomocí <xref:System.Windows.Controls.ControlTemplate>:</span><span class="sxs-lookup"><span data-stu-id="65aac-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="65aac-317">V tomto příkladu bylo tlačítko výchozí uživatelské rozhraní nahrazeno <xref:System.Windows.Shapes.Ellipse>, které má tmavě modré ohraničení a je vyplněno pomocí <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="65aac-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="65aac-318">Ovládací prvek <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah <xref:System.Windows.Controls.Button>"klikněte na mě!".</span><span class="sxs-lookup"><span data-stu-id="65aac-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="65aac-319">Při kliknutí na <xref:System.Windows.Controls.Button> je událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> stále vyvolána jako součást výchozího chování ovládacího prvku <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="65aac-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="65aac-320">Výsledek je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="65aac-320">The result is shown in the following figure:</span></span>

![Eliptické tlačítko a druhé okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="65aac-322">Datové šablony</span><span class="sxs-lookup"><span data-stu-id="65aac-322">Data templates</span></span>

<span data-ttu-id="65aac-323">Zatímco šablona ovládacího prvku umožňuje určit vzhled ovládacího prvku, šablona data umožňuje určit vzhled obsahu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="65aac-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="65aac-324">Šablony dat se často používají k vylepšení způsobu zobrazení vázaných dat.</span><span class="sxs-lookup"><span data-stu-id="65aac-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="65aac-325">Následující obrázek ukazuje výchozí vzhled pro <xref:System.Windows.Controls.ListBox>, která je svázána s kolekcí objektů `Task`, kde každá úloha má název, popis a prioritu:</span><span class="sxs-lookup"><span data-stu-id="65aac-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Rozevírací seznam s výchozím vzhledem](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="65aac-327">Výchozí vzhled je to, co byste očekávali od <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="65aac-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="65aac-328">Výchozí vzhled jednotlivých úloh však obsahuje pouze název úlohy.</span><span class="sxs-lookup"><span data-stu-id="65aac-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="65aac-329">Chcete-li zobrazit název, popis a prioritu úkolu, musí být výchozí vzhled položek vázaného seznamu ovládacího prvku <xref:System.Windows.Controls.ListBox> změněn pomocí <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="65aac-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="65aac-330">Následující kód XAML definuje takový <xref:System.Windows.DataTemplate>, který je použit pro každý úkol pomocí atributu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>:</span><span class="sxs-lookup"><span data-stu-id="65aac-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

<span data-ttu-id="65aac-331">Následující obrázek ukazuje účinek tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="65aac-331">The following figure shows the effect of this code:</span></span>

![Seznam, který používá šablonu dat](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="65aac-333">Všimněte si, že <xref:System.Windows.Controls.ListBox> zachovala chování a celkový vzhled; změnil se pouze vzhled obsahu zobrazeného v poli se seznamem.</span><span class="sxs-lookup"><span data-stu-id="65aac-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="65aac-334">Další informace najdete v tématu [Přehled šablonování dat](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="65aac-335">Styly</span><span class="sxs-lookup"><span data-stu-id="65aac-335">Styles</span></span>

<span data-ttu-id="65aac-336">Styly umožňují vývojářům a návrhářům standardizovat konkrétní vzhled pro svůj produkt.</span><span class="sxs-lookup"><span data-stu-id="65aac-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="65aac-337">WPF poskytuje model silného stylu, který je základem prvku <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="65aac-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="65aac-338">Následující příklad vytvoří styl, který nastaví barvu pozadí pro každé <xref:System.Windows.Controls.Button> okna na `Orange`:</span><span class="sxs-lookup"><span data-stu-id="65aac-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

<span data-ttu-id="65aac-339">Vzhledem k tomu, že tento styl cílí na všechny <xref:System.Windows.Controls.Button> ovládací prvky, styl je automaticky použit pro všechna tlačítka v okně, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="65aac-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Dvě oranžová tlačítka](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="65aac-341">Další informace najdete v tématu [styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="65aac-342">Prostředky</span><span class="sxs-lookup"><span data-stu-id="65aac-342">Resources</span></span>

<span data-ttu-id="65aac-343">Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může obsahovat cokoli z písma a barev pozadí pro řízení šablon, šablon dat a stylů.</span><span class="sxs-lookup"><span data-stu-id="65aac-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="65aac-344">Můžete použít podporu WPF pro prostředky uživatelského rozhraní k zapouzdření těchto prostředků v jednom umístění pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="65aac-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="65aac-345">Následující příklad definuje společnou barvu pozadí, která je sdílena <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Label>:</span><span class="sxs-lookup"><span data-stu-id="65aac-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

<span data-ttu-id="65aac-346">Tento příklad implementuje zdroj barvy pozadí pomocí elementu vlastnosti `Window.Resources`.</span><span class="sxs-lookup"><span data-stu-id="65aac-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="65aac-347">Tento prostředek je k dispozici všem podřízeným objektům <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="65aac-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="65aac-348">Existují různé obory prostředků, včetně následujících, v pořadí, ve kterém jsou vyřešeny:</span><span class="sxs-lookup"><span data-stu-id="65aac-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="65aac-349">Individuální ovládací prvek (pomocí zděděné vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="65aac-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="65aac-350"><xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> (používá se také zděděná vlastnost <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="65aac-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="65aac-351"><xref:System.Windows.Application> (pomocí vlastnosti <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="65aac-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="65aac-352">Různé obory vám umožňují flexibilitu v závislosti na způsobu, jakým definujete a sdílíte své prostředky.</span><span class="sxs-lookup"><span data-stu-id="65aac-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="65aac-353">Jako alternativu k přímému přidružení prostředků k určitému oboru můžete jeden nebo víc prostředků zabalit pomocí samostatné <xref:System.Windows.ResourceDictionary>, na kterou se dá odkazovat v jiných částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="65aac-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="65aac-354">Například následující příklad definuje výchozí barvu pozadí ve slovníku prostředků:</span><span class="sxs-lookup"><span data-stu-id="65aac-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="65aac-355">Následující příklad odkazuje na slovník prostředků definovaný v předchozím příkladu tak, aby byl sdílen napříč aplikací:</span><span class="sxs-lookup"><span data-stu-id="65aac-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

<span data-ttu-id="65aac-356">Prostředky a slovníky prostředků jsou základem podpory WPF pro motivy a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="65aac-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="65aac-357">Další informace najdete v tématu [prostředky](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="65aac-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="65aac-358">Vlastní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="65aac-358">Custom controls</span></span>

<span data-ttu-id="65aac-359">I když WPF poskytuje hostitele podpory přizpůsobení, může dojít k situacím, kdy existující ovládací prvky WPF nesplňují požadavky vaší aplikace nebo jejích uživatelů.</span><span class="sxs-lookup"><span data-stu-id="65aac-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="65aac-360">K tomu může dojít v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="65aac-360">This can occur when:</span></span>

- <span data-ttu-id="65aac-361">Uživatelské rozhraní, které požadujete, nelze vytvořit přizpůsobením vzhledu a chování stávajících implementací WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="65aac-362">Požadované chování není podporováno (nebo není podporováno) stávajícími implementacemi WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="65aac-363">V tuto chvíli ale můžete využít jeden ze tří modelů WPF pro vytvoření nového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="65aac-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="65aac-364">Každý model cílí na konkrétní scénář a vyžaduje, aby váš vlastní ovládací prvek byl odvozen z konkrétní základní třídy WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="65aac-365">Tady jsou uvedené tři modely:</span><span class="sxs-lookup"><span data-stu-id="65aac-365">The three models are listed here:</span></span>

- <span data-ttu-id="65aac-366">**Model uživatelského ovládacího prvku**.</span><span class="sxs-lookup"><span data-stu-id="65aac-366">**User Control Model**.</span></span> <span data-ttu-id="65aac-367">Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.UserControl> a skládá se z jednoho nebo více dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="65aac-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="65aac-368">**Model ovládacího prvku**.</span><span class="sxs-lookup"><span data-stu-id="65aac-368">**Control Model**.</span></span> <span data-ttu-id="65aac-369">Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.Control> a slouží k sestavování implementací, které oddělují své chování od jejich vzhledu pomocí šablon, podobně jako většina ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="65aac-370">Odvození z <xref:System.Windows.Controls.Control> vám umožňuje větší volnost při vytváření vlastního uživatelského rozhraní než uživatelských ovládacích prvků, ale může to vyžadovat více úsilí.</span><span class="sxs-lookup"><span data-stu-id="65aac-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="65aac-371">**Model elementu rozhraní**.</span><span class="sxs-lookup"><span data-stu-id="65aac-371">**Framework Element Model**.</span></span> <span data-ttu-id="65aac-372">Vlastní ovládací prvek je odvozen z <xref:System.Windows.FrameworkElement>, pokud je jeho vzhled definován pomocí vlastní logiky vykreslování (nikoli šablon).</span><span class="sxs-lookup"><span data-stu-id="65aac-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="65aac-373">Následující příklad ukazuje vlastní číselnou kontrolu nahoru/dolů, která je odvozena z <xref:System.Windows.Controls.UserControl>:</span><span class="sxs-lookup"><span data-stu-id="65aac-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="65aac-374">Následující příklad ilustruje XAML, který je požadován pro zahrnutí uživatelského ovládacího prvku do <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="65aac-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="65aac-375">Následující obrázek znázorňuje ovládací prvek `NumericUpDown` hostovaný v <xref:System.Windows.Window>:</span><span class="sxs-lookup"><span data-stu-id="65aac-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Vlastní UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="65aac-377">Další informace o vlastních ovládacích prvcích najdete v tématu [Přehled vytváření ovládacích](controls/control-authoring-overview.md)prvků.</span><span class="sxs-lookup"><span data-stu-id="65aac-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="65aac-378">Osvědčené postupy pro WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-378">WPF best practices</span></span>

<span data-ttu-id="65aac-379">Stejně jako u jakékoli vývojové platformy je možné WPF použít různými způsoby, abyste dosáhli požadovaného výsledku.</span><span class="sxs-lookup"><span data-stu-id="65aac-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="65aac-380">Jako způsob, jak zajistit, aby vaše aplikace WPF poskytovaly požadované uživatelské prostředí a splňovaly požadavky cílové skupiny obecně, existují Doporučené osvědčené postupy pro přístupnost, globalizaci a lokalizaci a výkon.</span><span class="sxs-lookup"><span data-stu-id="65aac-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="65aac-381">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="65aac-381">For more information, see:</span></span>

- [<span data-ttu-id="65aac-382">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="65aac-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="65aac-383">Globalizace a lokalizace WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="65aac-384">Výkon aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="65aac-385">Zabezpečení WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="65aac-386">Další kroky</span><span class="sxs-lookup"><span data-stu-id="65aac-386">Next steps</span></span>

<span data-ttu-id="65aac-387">Prohlédli jsme si klíčové funkce WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="65aac-388">Nyní je čas vytvořit svou první aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="65aac-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="65aac-389">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="65aac-390">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65aac-390">See also</span></span>

- [<span data-ttu-id="65aac-391">Začínáme s WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="65aac-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="65aac-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="65aac-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="65aac-393">Komunitní materiály pro WPF</span><span class="sxs-lookup"><span data-stu-id="65aac-393">WPF community resources</span></span>](getting-started/community-feedback.md)
