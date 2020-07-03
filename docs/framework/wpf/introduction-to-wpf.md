---
title: Úvod do WPF
titleSuffix: ''
description: Vytvářejte vizuálně působivé uživatelské prostředí ve Windows. Seznamte se s klíčovými funkcemi a koncepty Windows Presentation Foundation (WPF).
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7a79174f5f3aebe90190db45566b37bd5e9fbe3f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853573"
---
# <a name="wpf-overview"></a><span data-ttu-id="949c8-104">Přehled grafického subsystému WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="949c8-104">WPF overview</span></span>

<span data-ttu-id="949c8-105">Windows Presentation Foundation (WPF) umožňuje vytváření klientských aplikací pro Windows s vizuálně poutavými uživatelskými prostředími.</span><span class="sxs-lookup"><span data-stu-id="949c8-105">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Ukázka uživatelského rozhraní pro zdravotní péče společnosti Contoso](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="949c8-107">Jádrem WPF je modul vykreslování založený na rozlišení a vektorový vykreslovací modul, který je sestaven tak, aby využíval výhody moderního grafického hardwaru.</span><span class="sxs-lookup"><span data-stu-id="949c8-107">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="949c8-108">WPF rozšiřuje jádro o komplexní sadu funkcí pro vývoj aplikací, které zahrnují jazyk Extensible Application Markup Language (XAML) (XAML), ovládací prvky, datové vazby, rozložení, 2D a 3D grafiku, animace, styly, šablony, dokumenty, multimédia, text a typografie.</span><span class="sxs-lookup"><span data-stu-id="949c8-108">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="949c8-109">WPF je součástí .NET, takže můžete sestavovat aplikace, které zahrnují další prvky rozhraní .NET API.</span><span class="sxs-lookup"><span data-stu-id="949c8-109">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="949c8-110">Tento přehled je určený pro Newcomers a pokrývá klíčové funkce a koncepty WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-110">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="949c8-111">Program s WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-111">Program with WPF</span></span>

<span data-ttu-id="949c8-112">WPF existuje jako podmnožina typů .NET, které jsou (ve většině částí) umístěných v <xref:System.Windows> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="949c8-112">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="949c8-113">Pokud jste už dříve vytvořili aplikace s .NET pomocí spravovaných technologií, jako je ASP.NET a model Windows Forms, měli byste znát základní programovací prostředí WPF. můžete vytvářet instance tříd, nastavovat vlastnosti, volat metody a zpracovávat události pomocí oblíbeného programovacího jazyka .NET, jako je C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="949c8-113">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="949c8-114">WPF obsahuje další programovací konstrukce, které vylepšují vlastnosti a události: [vlastnosti závislosti](advanced/dependency-properties-overview.md) a [směrované události](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-114">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="949c8-115">Značky a kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="949c8-115">Markup and code-behind</span></span>

<span data-ttu-id="949c8-116">WPF umožňuje vyvíjet aplikace pomocí *značek* i *kódu na pozadí*, což je prostředí, se kterým by ASP.NET vývojáři měli znát.</span><span class="sxs-lookup"><span data-stu-id="949c8-116">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="949c8-117">Obecně se používá kód XAML k implementaci vzhledu aplikace při použití spravovaných programovacích jazyků (kódu na pozadí) k implementaci jeho chování.</span><span class="sxs-lookup"><span data-stu-id="949c8-117">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="949c8-118">Toto oddělení vzhledu a chování přináší následující výhody:</span><span class="sxs-lookup"><span data-stu-id="949c8-118">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="949c8-119">Náklady na vývoj a údržbu jsou sníženy, protože označení specifické pro vzhled není pevně spojeno s kódem specifickým pro chování.</span><span class="sxs-lookup"><span data-stu-id="949c8-119">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="949c8-120">Vývoj je efektivnější, protože návrháři můžou implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="949c8-120">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="949c8-121">[Globalizace a lokalizace](advanced/wpf-globalization-and-localization-overview.md) pro aplikace WPF je zjednodušená.</span><span class="sxs-lookup"><span data-stu-id="949c8-121">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="949c8-122">Kód</span><span class="sxs-lookup"><span data-stu-id="949c8-122">Markup</span></span>

<span data-ttu-id="949c8-123">XAML je značkovací jazyk založený na jazyce XML, který deklarativně implementuje vzhled aplikace.</span><span class="sxs-lookup"><span data-stu-id="949c8-123">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="949c8-124">Obvykle ho používáte k vytváření oken, dialogových oken, stránek a uživatelských ovládacích prvků a k jejich vyplnění ovládacími prvky, tvary a grafikou.</span><span class="sxs-lookup"><span data-stu-id="949c8-124">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="949c8-125">Následující příklad používá XAML k implementaci vzhledu okna, které obsahuje jediné tlačítko:</span><span class="sxs-lookup"><span data-stu-id="949c8-125">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="949c8-126">Konkrétně tento kód XAML definuje okno a tlačítko pomocí `Window` prvků a v `Button` uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="949c8-126">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="949c8-127">Každý element je nakonfigurován s atributy, jako je například `Window` atribut elementu `Title` pro určení textu záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="949c8-127">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="949c8-128">V době běhu převede WPF prvky a atributy, které jsou definovány v označení, na instance tříd WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-128">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="949c8-129">Například `Window` element je převeden na instanci <xref:System.Windows.Window> třídy, jejíž <xref:System.Windows.Window.Title%2A> vlastnost je hodnota `Title` atributu.</span><span class="sxs-lookup"><span data-stu-id="949c8-129">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="949c8-130">Následující obrázek ukazuje uživatelské rozhraní (UI), které je definováno XAML v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="949c8-130">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Okno obsahující tlačítko](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="949c8-132">Vzhledem k tomu, že XAML je založen na formátu XML, uživatelské rozhraní, které v něm vytvoříte, je sestaveno v hierarchii vnořených elementů, které jsou označovány jako [strom elementu](advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-132">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="949c8-133">Strom elementů poskytuje logický a intuitivní způsob, jak vytvořit a spravovat uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="949c8-133">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="949c8-134">Kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="949c8-134">Code-behind</span></span>

<span data-ttu-id="949c8-135">Hlavním chováním aplikace je implementovat funkcionalitu, která reaguje na interakce uživatele, včetně zpracování událostí (například kliknutí na nabídku, panel nástrojů nebo tlačítko) a volání obchodní logiky a logiky přístupu k datům v reakci.</span><span class="sxs-lookup"><span data-stu-id="949c8-135">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="949c8-136">V jazyce WPF je toto chování implementováno v kódu, který je spojen s označením.</span><span class="sxs-lookup"><span data-stu-id="949c8-136">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="949c8-137">Tento typ kódu je známý jako kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="949c8-137">This type of code is known as code-behind.</span></span> <span data-ttu-id="949c8-138">Následující příklad ukazuje aktualizovaný kód z předchozího příkladu a kód na pozadí:</span><span class="sxs-lookup"><span data-stu-id="949c8-138">The following example shows the updated markup from the previous example and the code-behind:</span></span>

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

<span data-ttu-id="949c8-139">V tomto příkladu kód na pozadí implementuje třídu, která je odvozena od <xref:System.Windows.Window> třídy.</span><span class="sxs-lookup"><span data-stu-id="949c8-139">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="949c8-140">`x:Class`Atribut slouží k přidružení značky ke třídě s kódem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="949c8-140">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="949c8-141">`InitializeComponent`je volána z konstruktoru třídy kódu na pozadí pro sloučení uživatelského rozhraní, které je definováno v označení pomocí třídy kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="949c8-141">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="949c8-142">( `InitializeComponent` je vygenerována za vás při sestavování aplikace, což je důvod, proč není nutné ji implementovat ručně.) Kombinace `x:Class` a ujistěte se `InitializeComponent` , že je vaše implementace správně inicializována při každém vytvoření.</span><span class="sxs-lookup"><span data-stu-id="949c8-142">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="949c8-143">Třída kódu na pozadí implementuje také obslužnou rutinu události pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="949c8-143">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="949c8-144">Po kliknutí na tlačítko, obslužná rutina události zobrazí okno se zprávou voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metody.</span><span class="sxs-lookup"><span data-stu-id="949c8-144">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="949c8-145">Následující obrázek ukazuje výsledek při kliknutí na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="949c8-145">The following figure shows the result when the button is clicked:</span></span>

![MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="949c8-147">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="949c8-147">Controls</span></span>

<span data-ttu-id="949c8-148">Uživatelské prostředí, které jsou dodávány aplikačním modelem, jsou konstruovány ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="949c8-148">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="949c8-149">V rámci WPF je *ovládací prvek* výrazem zastřešující, který se vztahuje na kategorii tříd WPF, které jsou hostovány buď v okně, nebo na stránce, mají uživatelské rozhraní a implementují určité chování.</span><span class="sxs-lookup"><span data-stu-id="949c8-149">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="949c8-150">Další informace najdete v tématu [ovládací prvky](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-150">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="949c8-151">Ovládací prvky WPF podle funkcí</span><span class="sxs-lookup"><span data-stu-id="949c8-151">WPF controls by function</span></span>

<span data-ttu-id="949c8-152">Tady jsou uvedené předdefinované ovládací prvky WPF:</span><span class="sxs-lookup"><span data-stu-id="949c8-152">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="949c8-153">**Tlačítka**: <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.RepeatButton> .</span><span class="sxs-lookup"><span data-stu-id="949c8-153">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="949c8-154">**Zobrazení dat**: <xref:System.Windows.Controls.DataGrid> , <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="949c8-154">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="949c8-155">**Zobrazení data a výběr**: <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker> .</span><span class="sxs-lookup"><span data-stu-id="949c8-155">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="949c8-156">**Dialogová okna**: <xref:Microsoft.Win32.OpenFileDialog> , a <xref:System.Windows.Controls.PrintDialog> <xref:Microsoft.Win32.SaveFileDialog> .</span><span class="sxs-lookup"><span data-stu-id="949c8-156">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="949c8-157">**Digitální inkoust**: <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter> .</span><span class="sxs-lookup"><span data-stu-id="949c8-157">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="949c8-158">**Dokumenty**: <xref:System.Windows.Controls.DocumentViewer> , <xref:System.Windows.Controls.FlowDocumentPageViewer> , <xref:System.Windows.Controls.FlowDocumentReader> , <xref:System.Windows.Controls.FlowDocumentScrollViewer> a <xref:System.Windows.Controls.StickyNoteControl> .</span><span class="sxs-lookup"><span data-stu-id="949c8-158">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="949c8-159">**Vstup**: <xref:System.Windows.Controls.TextBox> , <xref:System.Windows.Controls.RichTextBox> , a <xref:System.Windows.Controls.PasswordBox> .</span><span class="sxs-lookup"><span data-stu-id="949c8-159">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="949c8-160">**Rozložení**: <xref:System.Windows.Controls.Border> , <xref:System.Windows.Controls.Primitives.BulletDecorator> , <xref:System.Windows.Controls.Canvas> , <xref:System.Windows.Controls.DockPanel> , <xref:System.Windows.Controls.Expander> , <xref:System.Windows.Controls.Grid> , <xref:System.Windows.Controls.GridView> , <xref:System.Windows.Controls.GridSplitter> , <xref:System.Windows.Controls.GroupBox> , <xref:System.Windows.Controls.Panel> , <xref:System.Windows.Controls.Primitives.ResizeGrip> , <xref:System.Windows.Controls.Separator> , <xref:System.Windows.Controls.Primitives.ScrollBar> , <xref:System.Windows.Controls.ScrollViewer> , <xref:System.Windows.Controls.StackPanel> , <xref:System.Windows.Controls.Primitives.Thumb> , <xref:System.Windows.Controls.Viewbox> , <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window> <xref:System.Windows.Controls.WrapPanel> , a.</span><span class="sxs-lookup"><span data-stu-id="949c8-160">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="949c8-161">**Média**: <xref:System.Windows.Controls.Image> , <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Controls.SoundPlayerAction> .</span><span class="sxs-lookup"><span data-stu-id="949c8-161">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="949c8-162">**Nabídky**: <xref:System.Windows.Controls.ContextMenu> , <xref:System.Windows.Controls.Menu> a <xref:System.Windows.Controls.ToolBar> .</span><span class="sxs-lookup"><span data-stu-id="949c8-162">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="949c8-163">**Navigace**: <xref:System.Windows.Controls.Frame> , <xref:System.Windows.Documents.Hyperlink> , <xref:System.Windows.Controls.Page> , <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.TabControl> .</span><span class="sxs-lookup"><span data-stu-id="949c8-163">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="949c8-164">**Výběr**: <xref:System.Windows.Controls.CheckBox> , <xref:System.Windows.Controls.ComboBox> , <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.RadioButton> a <xref:System.Windows.Controls.Slider> .</span><span class="sxs-lookup"><span data-stu-id="949c8-164">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="949c8-165">**Informace o uživateli**: <xref:System.Windows.Controls.AccessText> , <xref:System.Windows.Controls.Label> , <xref:System.Windows.Controls.Primitives.Popup> ,,, a <xref:System.Windows.Controls.ProgressBar> <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.ToolTip> .</span><span class="sxs-lookup"><span data-stu-id="949c8-165">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="949c8-166">Vstupní příkazy a</span><span class="sxs-lookup"><span data-stu-id="949c8-166">Input and commands</span></span>

<span data-ttu-id="949c8-167">Ovládací prvky nejčastěji zjišťují a reagují na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="949c8-167">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="949c8-168">[Vstupní systém WPF](advanced/input-overview.md) používá přímé i směrované události pro podporu zadávání textu, správy fokusu a umístění myši.</span><span class="sxs-lookup"><span data-stu-id="949c8-168">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="949c8-169">Aplikace často mají komplexní požadavky na vstupy.</span><span class="sxs-lookup"><span data-stu-id="949c8-169">Applications often have complex input requirements.</span></span> <span data-ttu-id="949c8-170">WPF poskytuje [systém příkazů](advanced/commanding-overview.md) , který odděluje akce vstupu uživatele od kódu, který reaguje na tyto akce.</span><span class="sxs-lookup"><span data-stu-id="949c8-170">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="949c8-171">Layout</span><span class="sxs-lookup"><span data-stu-id="949c8-171">Layout</span></span>

<span data-ttu-id="949c8-172">Když vytváříte uživatelské rozhraní, uspořádáte ovládací prvky podle umístění a velikosti pro vytvoření rozložení.</span><span class="sxs-lookup"><span data-stu-id="949c8-172">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="949c8-173">Klíčovým požadavkem pro jakékoli rozložení je přizpůsobení změn velikosti okna a nastavení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="949c8-173">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="949c8-174">Namísto vynucení psaní kódu za účelem přizpůsobení rozložení za těchto okolností nabízí WPF pro vás špičkové rozšiřitelné systémové rozložení.</span><span class="sxs-lookup"><span data-stu-id="949c8-174">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="949c8-175">Základem systému rozložení je relativní umístění, které zvyšuje schopnost přizpůsobit se změnám oken a zobrazení podmínek.</span><span class="sxs-lookup"><span data-stu-id="949c8-175">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="949c8-176">Kromě toho systém rozložení spravuje vyjednávání mezi ovládacími prvky pro určení rozložení.</span><span class="sxs-lookup"><span data-stu-id="949c8-176">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="949c8-177">Vyjednávání je dvoustupňový proces: nejprve ovládací prvek oznamuje své nadřazené umístění a velikost, které vyžaduje. za druhé nadřazená položka oznamuje ovládacím prvkům, kolik místa může mít.</span><span class="sxs-lookup"><span data-stu-id="949c8-177">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="949c8-178">Systém rozložení je vystaven podřízeným ovládacím prvkům prostřednictvím základních tříd WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-178">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="949c8-179">Pro společná rozložení, jako jsou mřížky, skládání a ukotvení, WPF obsahuje několik ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="949c8-179">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="949c8-180"><xref:System.Windows.Controls.Canvas>: Podřízené ovládací prvky poskytují své vlastní rozložení.</span><span class="sxs-lookup"><span data-stu-id="949c8-180"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="949c8-181"><xref:System.Windows.Controls.DockPanel>: Podřízené ovládací prvky jsou zarovnány k okrajům panelu.</span><span class="sxs-lookup"><span data-stu-id="949c8-181"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="949c8-182"><xref:System.Windows.Controls.Grid>: Podřízené ovládací prvky jsou umístěny podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="949c8-182"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="949c8-183"><xref:System.Windows.Controls.StackPanel>: Podřízené ovládací prvky jsou skládané buď svisle, nebo vodorovně.</span><span class="sxs-lookup"><span data-stu-id="949c8-183"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="949c8-184"><xref:System.Windows.Controls.VirtualizingStackPanel>: Podřízené ovládací prvky jsou virtualizované a uspořádány na jednom řádku, který je buď vodorovně, nebo svisle orientovaný.</span><span class="sxs-lookup"><span data-stu-id="949c8-184"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="949c8-185"><xref:System.Windows.Controls.WrapPanel>: Podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zabaleny na další řádek, pokud existuje více ovládacích prvků na aktuálním řádku, než povoluje prostor.</span><span class="sxs-lookup"><span data-stu-id="949c8-185"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="949c8-186">Následující příklad používá <xref:System.Windows.Controls.DockPanel> k rozložení několika <xref:System.Windows.Controls.TextBox> ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="949c8-186">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="949c8-187"><xref:System.Windows.Controls.DockPanel>Umožňuje podřízeným <xref:System.Windows.Controls.TextBox> ovládacím prvkům sdělit, jak je uspořádat.</span><span class="sxs-lookup"><span data-stu-id="949c8-187">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="949c8-188">K tomu <xref:System.Windows.Controls.DockPanel> implementuje `Dock` připojenou vlastnost, která je vystavena podřízeným ovládacím prvkům, aby každému z nich bylo možné zadat styl ukotvení.</span><span class="sxs-lookup"><span data-stu-id="949c8-188">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="949c8-189">Vlastnost, která je implementována nadřazeným ovládacím prvkem pro použití podřízenými ovládacími prvky, je konstrukce WPF nazývaná [připojená vlastnost](advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-189">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="949c8-190">Následující obrázek ukazuje výsledek kódu XAML v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="949c8-190">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Stránka DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="949c8-192">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="949c8-192">Data binding</span></span>

<span data-ttu-id="949c8-193">Většina aplikací je vytvořená tak, aby uživatelům poskytovala prostředky k zobrazení a úpravám dat.</span><span class="sxs-lookup"><span data-stu-id="949c8-193">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="949c8-194">V případě aplikací WPF je pro technologie, jako je SQL Server a ADO .NET, k dispozici práce s daty, která jsou již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="949c8-194">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="949c8-195">Po otevření dat a jejich načtení do spravovaných objektů aplikace je zahájena pevná práce pro aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-195">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="949c8-196">V podstatě to zahrnuje dvě věci:</span><span class="sxs-lookup"><span data-stu-id="949c8-196">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="949c8-197">Kopírování dat ze spravovaných objektů do ovládacích prvků, kde lze data zobrazit a upravit.</span><span class="sxs-lookup"><span data-stu-id="949c8-197">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="949c8-198">Zajištění, že se změny provedené u dat pomocí ovládacích prvků zkopírují zpátky do spravovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="949c8-198">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="949c8-199">Pro zjednodušení vývoje aplikací poskytuje WPF modul datových vazeb k automatickému provedení těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="949c8-199">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="949c8-200">Základní jednotkou modulu datové vazby je <xref:System.Windows.Data.Binding> třída, jejíž úkolem je vytvořit vazbu ovládacího prvku (cíl vazby) k datovému objektu (zdroj vazby).</span><span class="sxs-lookup"><span data-stu-id="949c8-200">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="949c8-201">Tento vztah je znázorněný na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="949c8-201">This relationship is illustrated by the following figure:</span></span>

![Základní diagram datových vazeb](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="949c8-203">Další příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TextBox> instanci vlastního `Person` objektu.</span><span class="sxs-lookup"><span data-stu-id="949c8-203">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="949c8-204">`Person`Implementace je uvedena v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="949c8-204">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="949c8-205">Následující kód vytvoří vazby <xref:System.Windows.Controls.TextBox> na instanci vlastního `Person` objektu:</span><span class="sxs-lookup"><span data-stu-id="949c8-205">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

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

<span data-ttu-id="949c8-206">V tomto příkladu `Person` je vytvořena instance třídy v kódu na pozadí a je nastavena jako datový kontext pro `DataBindingWindow` .</span><span class="sxs-lookup"><span data-stu-id="949c8-206">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="949c8-207">V kódu <xref:System.Windows.Controls.TextBox.Text%2A> je vlastnost typu <xref:System.Windows.Controls.TextBox> svázána s `Person.Name` vlastností (pomocí `{Binding ... }` syntaxe jazyka XAML).</span><span class="sxs-lookup"><span data-stu-id="949c8-207">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="949c8-208">Tento kód XAML oznamuje ovládacímu prvku WPF, aby navázal <xref:System.Windows.Controls.TextBox> ovládací prvek na `Person` objekt, který je uložen v <xref:System.Windows.FrameworkElement.DataContext%2A> Vlastnosti okna.</span><span class="sxs-lookup"><span data-stu-id="949c8-208">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="949c8-209">Modul datových vazeb WPF poskytuje další podporu, která zahrnuje ověřování, řazení, filtrování a seskupování.</span><span class="sxs-lookup"><span data-stu-id="949c8-209">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="949c8-210">Kromě toho datová vazba podporuje použití datových šablon k vytvoření vlastního uživatelského rozhraní pro vázaná data v případě, že uživatelské rozhraní zobrazené standardními ovládacími prvky WPF není vhodné.</span><span class="sxs-lookup"><span data-stu-id="949c8-210">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="949c8-211">Další informace najdete v tématu [Přehled datových vazeb](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-211">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="949c8-212">Grafika</span><span class="sxs-lookup"><span data-stu-id="949c8-212">Graphics</span></span>

<span data-ttu-id="949c8-213">WPF přináší rozsáhlou, škálovatelnou a flexibilní sadu grafických funkcí, které mají následující výhody:</span><span class="sxs-lookup"><span data-stu-id="949c8-213">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="949c8-214">Grafika nezávislá na **rozlišení a zařízení**.</span><span class="sxs-lookup"><span data-stu-id="949c8-214">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="949c8-215">Základní jednotkou v grafickém systému WPF je pixel nezávislý na zařízení, který je 1/1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávisle na rozlišení a na zařízení.</span><span class="sxs-lookup"><span data-stu-id="949c8-215">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="949c8-216">Každé pixely nezávislé na zařízení se automaticky škáluje tak, aby se shodovalo s nastavením bodů na palec (dpi) systému, na kterém se vykreslí.</span><span class="sxs-lookup"><span data-stu-id="949c8-216">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="949c8-217">**Vylepšená přesnost**.</span><span class="sxs-lookup"><span data-stu-id="949c8-217">**Improved precision**.</span></span> <span data-ttu-id="949c8-218">Systém souřadnic WPF se měří s čísly s plovoucí desetinnou čárkou s dvojitou přesností, nikoli s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="949c8-218">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="949c8-219">Transformace a hodnoty neprůhlednosti se také vyjadřují jako dvojitá přesnost.</span><span class="sxs-lookup"><span data-stu-id="949c8-219">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="949c8-220">WPF také podporuje šířku barevné škály (scRGB) a poskytuje integrovanou podporu pro správu vstupů z různých barevných prostorů.</span><span class="sxs-lookup"><span data-stu-id="949c8-220">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="949c8-221">**Pokročilá podpora grafiky a animací**</span><span class="sxs-lookup"><span data-stu-id="949c8-221">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="949c8-222">WPF zjednodušuje programování grafiky tím, že vám umožní spravovat animace na pozadí. Nemusíte se starat o zpracování scény, vykreslování smyček a varianty interpolaci.</span><span class="sxs-lookup"><span data-stu-id="949c8-222">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="949c8-223">Kromě toho WPF poskytuje podporu testování testů a úplnou podporu pro skládání v alfa.</span><span class="sxs-lookup"><span data-stu-id="949c8-223">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="949c8-224">**Hardwarová akcelerace**.</span><span class="sxs-lookup"><span data-stu-id="949c8-224">**Hardware acceleration**.</span></span> <span data-ttu-id="949c8-225">Grafický systém WPF využívá grafický hardware k minimalizaci využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="949c8-225">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="949c8-226">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="949c8-226">2D shapes</span></span>

<span data-ttu-id="949c8-227">WPF poskytuje knihovnu běžných 2D nakreslených 2D tvarů, jako jsou obdélníky a tři tečky, které jsou zobrazeny na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="949c8-227">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Elipsy a obdélníky](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="949c8-229">Zajímavou schopností tvarů je, že nejsou jenom pro zobrazení; obrazce implementují mnoho funkcí, které očekáváte od ovládacích prvků, včetně vstupu klávesnice a myši.</span><span class="sxs-lookup"><span data-stu-id="949c8-229">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="949c8-230">Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> událost, která je <xref:System.Windows.Shapes.Ellipse> zpracovávána:</span><span class="sxs-lookup"><span data-stu-id="949c8-230">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="949c8-231">Následující obrázek ukazuje, co je vyrobeno v předchozím kódu:</span><span class="sxs-lookup"><span data-stu-id="949c8-231">The following figure shows what is produced by the preceding code:</span></span>

![Okno s textem, po kterém jste klikli na&#33; elipsa "](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="949c8-233">Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-233">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="949c8-234">2D geometrií</span><span class="sxs-lookup"><span data-stu-id="949c8-234">2D geometries</span></span>

<span data-ttu-id="949c8-235">2D obrazce, které poskytuje WPF, se týkají standardní sady základních tvarů.</span><span class="sxs-lookup"><span data-stu-id="949c8-235">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="949c8-236">Je však možné, že budete muset vytvořit vlastní tvary, aby bylo usnadněno navrhování přizpůsobeného uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="949c8-236">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="949c8-237">Pro účely tohoto účelu WPF poskytuje geometrií.</span><span class="sxs-lookup"><span data-stu-id="949c8-237">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="949c8-238">Následující obrázek ukazuje použití geometrií k vytvoření vlastního tvaru, který lze vykreslit přímo, použít jako štětec nebo použít k Vystřižení jiných tvarů a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="949c8-238">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="949c8-239"><xref:System.Windows.Shapes.Path>objekty lze použít k vykreslení uzavřených nebo otevřených tvarů, více tvarů a dokonce i zakřivených tvarů.</span><span class="sxs-lookup"><span data-stu-id="949c8-239"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="949c8-240"><xref:System.Windows.Media.Geometry>objekty lze použít pro oříznutí, testování přístupů a vykreslování 2D grafických dat.</span><span class="sxs-lookup"><span data-stu-id="949c8-240"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Různá použití cesty](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="949c8-242">Další informace najdete v tématu [geometrie Overview](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-242">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="949c8-243">2D efekty</span><span class="sxs-lookup"><span data-stu-id="949c8-243">2D effects</span></span>

<span data-ttu-id="949c8-244">Podmnožina možností WPF 2D zahrnuje vizuální efekty, jako jsou barevné přechody, bitmapy, kresby, Malování s videi, otočení, škálování a zkosení.</span><span class="sxs-lookup"><span data-stu-id="949c8-244">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="949c8-245">Všechny jsou dosaženy pomocí štětců; Následující obrázek ukazuje několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="949c8-245">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Ilustrace různých štětců](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="949c8-247">Další informace najdete v tématu [Přehled štětců WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-247">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="949c8-248">Prostorové vykreslování</span><span class="sxs-lookup"><span data-stu-id="949c8-248">3D rendering</span></span>

<span data-ttu-id="949c8-249">WPF také zahrnuje možnosti 3D vykreslování, které se integrují s 2D grafikami a umožňují vytváření zajímavějších a zajímavých uživatelských rozhraní.</span><span class="sxs-lookup"><span data-stu-id="949c8-249">WPF also includes 3D rendering capabilities that integrate with 2D graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="949c8-250">Například následující obrázek znázorňuje 2D obrázky vykreslené do 3D tvarů:</span><span class="sxs-lookup"><span data-stu-id="949c8-250">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Snímek obrazovky ukázka Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="949c8-252">Další informace najdete v tématu [Přehled 3D grafiky](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-252">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="949c8-253">Animace</span><span class="sxs-lookup"><span data-stu-id="949c8-253">Animation</span></span>

<span data-ttu-id="949c8-254">Podpora animace WPF umožňuje řídit, protřepání, otočení a zmizení ovládacích prvků, aby bylo možné vytvářet zajímavé přechody stránky a další.</span><span class="sxs-lookup"><span data-stu-id="949c8-254">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="949c8-255">Můžete animovat většinu tříd WPF, dokonce i vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="949c8-255">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="949c8-256">Na následujícím obrázku je znázorněna jednoduchá animace v akci:</span><span class="sxs-lookup"><span data-stu-id="949c8-256">The following figure shows a simple animation in action:</span></span>

![Obrázky animované datové krychle](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="949c8-258">Další informace najdete v tématu [Přehled animací](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-258">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="949c8-259">Média</span><span class="sxs-lookup"><span data-stu-id="949c8-259">Media</span></span>

<span data-ttu-id="949c8-260">Jedním ze způsobů, jak vyjádřit bohatou část obsahu, je použití audiovizuálních médií.</span><span class="sxs-lookup"><span data-stu-id="949c8-260">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="949c8-261">WPF poskytuje speciální podporu pro obrázky, video a zvuk.</span><span class="sxs-lookup"><span data-stu-id="949c8-261">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="949c8-262">Image</span><span class="sxs-lookup"><span data-stu-id="949c8-262">Images</span></span>

<span data-ttu-id="949c8-263">Obrázky jsou společné pro většinu aplikací a WPF nabízí několik způsobů jejich použití.</span><span class="sxs-lookup"><span data-stu-id="949c8-263">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="949c8-264">Následující obrázek ukazuje uživatelské rozhraní se seznamem, které obsahuje miniatury obrázků.</span><span class="sxs-lookup"><span data-stu-id="949c8-264">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="949c8-265">Když je vybraná Miniatura, zobrazí se obrázek v plné velikosti.</span><span class="sxs-lookup"><span data-stu-id="949c8-265">When a thumbnail is selected, the image is shown full-size.</span></span>

![Obrázky miniatur a obrázek plné velikosti&#45;](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="949c8-267">Další informace najdete v tématu [Přehled imagí](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-267">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="949c8-268">Video a zvuk</span><span class="sxs-lookup"><span data-stu-id="949c8-268">Video and audio</span></span>

<span data-ttu-id="949c8-269"><xref:System.Windows.Controls.MediaElement>Ovládací prvek je schopný přehrávat video i zvuk a je dostatečně flexibilní, aby byl základem pro vlastní přehrávač médií.</span><span class="sxs-lookup"><span data-stu-id="949c8-269">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="949c8-270">Následující kód XAML implementuje přehrávač médií:</span><span class="sxs-lookup"><span data-stu-id="949c8-270">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="949c8-271">Okno na následujícím obrázku znázorňuje <xref:System.Windows.Controls.MediaElement> ovládací prvek v akci:</span><span class="sxs-lookup"><span data-stu-id="949c8-271">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Ovládací prvek MediaElement se zvukem a videem](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="949c8-273">Další informace najdete v tématu [grafika a multimédia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-273">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="949c8-274">Text a typografie</span><span class="sxs-lookup"><span data-stu-id="949c8-274">Text and typography</span></span>

<span data-ttu-id="949c8-275">Pro usnadnění vysoce kvalitního vykreslování textu nabízí WPF tyto funkce:</span><span class="sxs-lookup"><span data-stu-id="949c8-275">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="949c8-276">Podpora písma OpenType.</span><span class="sxs-lookup"><span data-stu-id="949c8-276">OpenType font support.</span></span>

- <span data-ttu-id="949c8-277">Vylepšení technologie ClearType.</span><span class="sxs-lookup"><span data-stu-id="949c8-277">ClearType enhancements.</span></span>

- <span data-ttu-id="949c8-278">Vysoký výkon, který využívá hardwarovou akceleraci.</span><span class="sxs-lookup"><span data-stu-id="949c8-278">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="949c8-279">Integrace textu s médii, grafikou a animací</span><span class="sxs-lookup"><span data-stu-id="949c8-279">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="949c8-280">Mezinárodní podpora písem a nouzové mechanismy.</span><span class="sxs-lookup"><span data-stu-id="949c8-280">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="949c8-281">Jako ukázku integrace textu s grafikou ukazuje následující obrázek použití dekorace textu:</span><span class="sxs-lookup"><span data-stu-id="949c8-281">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Text s různými dekoracemi textu](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="949c8-283">Další informace najdete v tématu [Typografie v Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-283">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="949c8-284">Přizpůsobení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-284">Customize WPF apps</span></span>

<span data-ttu-id="949c8-285">Až do tohoto okamžiku jste viděli základní stavební bloky WPF pro vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="949c8-285">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="949c8-286">Model aplikace použijete k hostování a dodávání obsahu aplikace, který se skládá hlavně z ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="949c8-286">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="949c8-287">Chcete-li zjednodušit uspořádání ovládacích prvků v uživatelském rozhraní a zajistit, aby bylo uspořádání udržováno v tvář změny velikosti okna a nastavení zobrazení, použijte systém rozložení WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-287">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="949c8-288">Vzhledem k tomu, že většina aplikací umožňuje uživatelům pracovat s daty, můžete použít datovou vazbu k omezení práce v rámci integrace uživatelského rozhraní s daty.</span><span class="sxs-lookup"><span data-stu-id="949c8-288">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="949c8-289">Chcete-li zlepšit vizuální vzhled aplikace, použijte komplexní škálu grafiky, animace a podpory médií, které poskytuje WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-289">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="949c8-290">Většinou ale nemusíte vytvářet a spravovat skutečně odlišná a vizuálně působivé uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="949c8-290">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="949c8-291">Standardní ovládací prvky WPF nemusí být integrovány s požadovaným vzhledem aplikace.</span><span class="sxs-lookup"><span data-stu-id="949c8-291">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="949c8-292">Data se nemusí zobrazovat v nejúčinnějším způsobu.</span><span class="sxs-lookup"><span data-stu-id="949c8-292">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="949c8-293">Celkové uživatelské prostředí vaší aplikace nemusí být vhodné pro výchozí vzhled a chování motivů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="949c8-293">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="949c8-294">V mnoha způsobech prezentace potřebuje vizuální rozšiřitelnost, a to podobně jako jakýkoli jiný typ rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="949c8-294">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="949c8-295">Z tohoto důvodu WPF poskytuje řadu mechanismů pro vytváření jedinečných uživatelských prostředí, včetně modelu bohatých obsahu pro ovládací prvky, triggery, ovládací prvky a šablony dat, styly, prostředky uživatelského rozhraní a motivy a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="949c8-295">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="949c8-296">Model obsahu</span><span class="sxs-lookup"><span data-stu-id="949c8-296">Content model</span></span>

<span data-ttu-id="949c8-297">Hlavním účelem většiny ovládacích prvků WPF je zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="949c8-297">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="949c8-298">V WPF je typ a počet položek, které mohou být obsahem ovládacího prvku, označovány jako *model obsahu*ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="949c8-298">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="949c8-299">Některé ovládací prvky mohou obsahovat jednu položku a typ obsahu; například obsah třídy <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která je přiřazena <xref:System.Windows.Controls.TextBox.Text%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="949c8-299">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="949c8-300">Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox> :</span><span class="sxs-lookup"><span data-stu-id="949c8-300">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="949c8-301">Výsledek je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="949c8-301">The following figure shows the result:</span></span>

![Ovládací prvek TextBox, který obsahuje text](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="949c8-303">Jiné ovládací prvky však mohou obsahovat více položek různých typů obsahu; obsah, který je <xref:System.Windows.Controls.Button> určen <xref:System.Windows.Controls.ContentControl.Content%2A> vlastností, může obsahovat různé položky, včetně ovládacích prvků rozložení, textu, obrázků a tvarů.</span><span class="sxs-lookup"><span data-stu-id="949c8-303">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="949c8-304">Následující příklad ukazuje <xref:System.Windows.Controls.Button> s obsahem, který obsahuje, a, a <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.Border> a a <xref:System.Windows.Controls.MediaElement> :</span><span class="sxs-lookup"><span data-stu-id="949c8-304">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

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

<span data-ttu-id="949c8-305">Následující obrázek ukazuje obsah tohoto tlačítka:</span><span class="sxs-lookup"><span data-stu-id="949c8-305">The following figure shows the content of this button:</span></span>

![Tlačítko, které obsahuje více typů obsahu](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="949c8-307">Další informace o typech obsahu, které jsou podporovány různými ovládacími prvky, naleznete v tématu [model obsahu WPF](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-307">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="949c8-308">Aktivační události</span><span class="sxs-lookup"><span data-stu-id="949c8-308">Triggers</span></span>

<span data-ttu-id="949c8-309">I když hlavní účel kódu XAML je implementovat vzhled aplikace, můžete také použít XAML k implementaci některých aspektů chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="949c8-309">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="949c8-310">Jedním z příkladů je použití triggerů ke změně vzhledu aplikace na základě interakcí uživatelů.</span><span class="sxs-lookup"><span data-stu-id="949c8-310">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="949c8-311">Další informace najdete v tématu [styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-311">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="949c8-312">Šablony ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="949c8-312">Control templates</span></span>

<span data-ttu-id="949c8-313">Výchozí uživatelská rozhraní pro ovládací prvky WPF jsou obvykle vytvořena z jiných ovládacích prvků a tvarů.</span><span class="sxs-lookup"><span data-stu-id="949c8-313">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="949c8-314">Například, <xref:System.Windows.Controls.Button> se skládá z obou <xref:Microsoft.Windows.Themes.ButtonChrome> <xref:System.Windows.Controls.ContentPresenter> ovládacích prvků i.</span><span class="sxs-lookup"><span data-stu-id="949c8-314">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="949c8-315"><xref:Microsoft.Windows.Themes.ButtonChrome>Poskytuje standardní vzhled tlačítka, zatímco <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka, jak je určeno <xref:System.Windows.Controls.ContentControl.Content%2A> vlastností.</span><span class="sxs-lookup"><span data-stu-id="949c8-315">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="949c8-316">Někdy se může stát, že výchozí vzhled ovládacího prvku bude incongruent s celkovým vzhledem aplikace.</span><span class="sxs-lookup"><span data-stu-id="949c8-316">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="949c8-317">V tomto případě můžete použít <xref:System.Windows.Controls.ControlTemplate> ke změně vzhledu uživatelského rozhraní ovládacího prvku, aniž by došlo ke změně jeho obsahu a chování.</span><span class="sxs-lookup"><span data-stu-id="949c8-317">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="949c8-318">Následující příklad ukazuje, jak změnit vzhled pomocí <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ControlTemplate> :</span><span class="sxs-lookup"><span data-stu-id="949c8-318">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="949c8-319">V tomto příkladu bylo uživatelské rozhraní výchozího tlačítka nahrazeno <xref:System.Windows.Shapes.Ellipse> , které má tmavě modré ohraničení a je vyplněno pomocí <xref:System.Windows.Media.RadialGradientBrush> .</span><span class="sxs-lookup"><span data-stu-id="949c8-319">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="949c8-320"><xref:System.Windows.Controls.ContentPresenter>Ovládací prvek zobrazí obsah <xref:System.Windows.Controls.Button> "klikněte na mě!".</span><span class="sxs-lookup"><span data-stu-id="949c8-320">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="949c8-321">Při <xref:System.Windows.Controls.Button> kliknutí na je <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost stále vyvolána jako součást <xref:System.Windows.Controls.Button> výchozího chování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="949c8-321">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="949c8-322">Výsledek je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="949c8-322">The result is shown in the following figure:</span></span>

![Eliptické tlačítko a druhé okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="949c8-324">Datové šablony</span><span class="sxs-lookup"><span data-stu-id="949c8-324">Data templates</span></span>

<span data-ttu-id="949c8-325">Zatímco šablona ovládacího prvku umožňuje určit vzhled ovládacího prvku, šablona data umožňuje určit vzhled obsahu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="949c8-325">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="949c8-326">Šablony dat se často používají k vylepšení způsobu zobrazení vázaných dat.</span><span class="sxs-lookup"><span data-stu-id="949c8-326">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="949c8-327">Následující obrázek ukazuje výchozí vzhled pro objekt <xref:System.Windows.Controls.ListBox> , který je svázán s kolekcí `Task` objektů, kde každý úkol má název, popis a prioritu:</span><span class="sxs-lookup"><span data-stu-id="949c8-327">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Rozevírací seznam s výchozím vzhledem](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="949c8-329">Výchozí vzhled je to, co byste očekávali od <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="949c8-329">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="949c8-330">Výchozí vzhled jednotlivých úloh však obsahuje pouze název úlohy.</span><span class="sxs-lookup"><span data-stu-id="949c8-330">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="949c8-331">Chcete-li zobrazit název, popis a prioritu úkolu, <xref:System.Windows.Controls.ListBox> musí být výchozí vzhled položek vázaného seznamu ovládacího prvku změněn pomocí <xref:System.Windows.DataTemplate> .</span><span class="sxs-lookup"><span data-stu-id="949c8-331">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="949c8-332">Následující kód XAML definuje takový <xref:System.Windows.DataTemplate> , který je použit pro každý úkol pomocí <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> atributu:</span><span class="sxs-lookup"><span data-stu-id="949c8-332">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

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

<span data-ttu-id="949c8-333">Následující obrázek ukazuje účinek tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="949c8-333">The following figure shows the effect of this code:</span></span>

![Seznam, který používá šablonu dat](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="949c8-335">Všimněte si, že se <xref:System.Windows.Controls.ListBox> zachovalo chování a celkový vzhled; změnil se pouze vzhled obsahu zobrazeného v poli se seznamem.</span><span class="sxs-lookup"><span data-stu-id="949c8-335">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="949c8-336">Další informace najdete v tématu [Přehled šablonování dat](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-336">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="949c8-337">Styly</span><span class="sxs-lookup"><span data-stu-id="949c8-337">Styles</span></span>

<span data-ttu-id="949c8-338">Styly umožňují vývojářům a návrhářům standardizovat konkrétní vzhled pro svůj produkt.</span><span class="sxs-lookup"><span data-stu-id="949c8-338">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="949c8-339">WPF poskytuje model silného stylu, který je základem <xref:System.Windows.Style> elementu.</span><span class="sxs-lookup"><span data-stu-id="949c8-339">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="949c8-340">Následující příklad vytvoří styl, který nastaví barvu pozadí každého <xref:System.Windows.Controls.Button> okna na `Orange` :</span><span class="sxs-lookup"><span data-stu-id="949c8-340">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

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

<span data-ttu-id="949c8-341">Vzhledem k tomu, že tento styl cílí na všechny <xref:System.Windows.Controls.Button> ovládací prvky, styl je automaticky použit pro všechna tlačítka v okně, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="949c8-341">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Dvě oranžová tlačítka](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="949c8-343">Další informace najdete v tématu [styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-343">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="949c8-344">Prostředky</span><span class="sxs-lookup"><span data-stu-id="949c8-344">Resources</span></span>

<span data-ttu-id="949c8-345">Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může obsahovat cokoli z písma a barev pozadí pro řízení šablon, šablon dat a stylů.</span><span class="sxs-lookup"><span data-stu-id="949c8-345">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="949c8-346">Můžete použít podporu WPF pro prostředky uživatelského rozhraní k zapouzdření těchto prostředků v jednom umístění pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="949c8-346">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="949c8-347">Následující příklad definuje společnou barvu pozadí, která je sdílena <xref:System.Windows.Controls.Button> a a <xref:System.Windows.Controls.Label> :</span><span class="sxs-lookup"><span data-stu-id="949c8-347">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

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

<span data-ttu-id="949c8-348">Tento příklad implementuje zdroj barvy pozadí pomocí `Window.Resources` elementu Property.</span><span class="sxs-lookup"><span data-stu-id="949c8-348">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="949c8-349">Tento prostředek je k dispozici všem podřízeným objektům <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="949c8-349">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="949c8-350">Existují různé obory prostředků, včetně následujících, v pořadí, ve kterém jsou vyřešeny:</span><span class="sxs-lookup"><span data-stu-id="949c8-350">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="949c8-351">Individuální ovládací prvek (pomocí zděděné <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> Vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="949c8-351">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="949c8-352">A <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> (také pomocí zděděné <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> Vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="949c8-352">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="949c8-353">A <xref:System.Windows.Application> (pomocí <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> Vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="949c8-353">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="949c8-354">Různé obory vám umožňují flexibilitu v závislosti na způsobu, jakým definujete a sdílíte své prostředky.</span><span class="sxs-lookup"><span data-stu-id="949c8-354">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="949c8-355">Jako alternativu k přímému přiřazení prostředků k určitému oboru můžete jeden nebo víc prostředků zabalit pomocí samostatného, na <xref:System.Windows.ResourceDictionary> které se dá odkazovat v jiných částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="949c8-355">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="949c8-356">Například následující příklad definuje výchozí barvu pozadí ve slovníku prostředků:</span><span class="sxs-lookup"><span data-stu-id="949c8-356">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="949c8-357">Následující příklad odkazuje na slovník prostředků definovaný v předchozím příkladu tak, aby byl sdílen napříč aplikací:</span><span class="sxs-lookup"><span data-stu-id="949c8-357">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

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

<span data-ttu-id="949c8-358">Prostředky a slovníky prostředků jsou základem podpory WPF pro motivy a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="949c8-358">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="949c8-359">Další informace najdete v tématu [prostředky](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="949c8-359">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="949c8-360">Vlastní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="949c8-360">Custom controls</span></span>

<span data-ttu-id="949c8-361">I když WPF poskytuje hostitele podpory přizpůsobení, může dojít k situacím, kdy existující ovládací prvky WPF nesplňují požadavky vaší aplikace nebo jejích uživatelů.</span><span class="sxs-lookup"><span data-stu-id="949c8-361">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="949c8-362">K tomu může dojít v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="949c8-362">This can occur when:</span></span>

- <span data-ttu-id="949c8-363">Uživatelské rozhraní, které požadujete, nelze vytvořit přizpůsobením vzhledu a chování stávajících implementací WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-363">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="949c8-364">Požadované chování není podporováno (nebo není podporováno) stávajícími implementacemi WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-364">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="949c8-365">V tuto chvíli ale můžete využít jeden ze tří modelů WPF pro vytvoření nového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="949c8-365">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="949c8-366">Každý model cílí na konkrétní scénář a vyžaduje, aby váš vlastní ovládací prvek byl odvozen z konkrétní základní třídy WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-366">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="949c8-367">Tady jsou uvedené tři modely:</span><span class="sxs-lookup"><span data-stu-id="949c8-367">The three models are listed here:</span></span>

- <span data-ttu-id="949c8-368">**Model uživatelského ovládacího prvku**.</span><span class="sxs-lookup"><span data-stu-id="949c8-368">**User Control Model**.</span></span> <span data-ttu-id="949c8-369">Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.UserControl> a se skládá z jednoho nebo více dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="949c8-369">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="949c8-370">**Model ovládacího prvku**.</span><span class="sxs-lookup"><span data-stu-id="949c8-370">**Control Model**.</span></span> <span data-ttu-id="949c8-371">Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.Control> a je použit k sestavení implementace, které oddělují své chování od jejich vzhledu pomocí šablon, podobně jako většina ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-371">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="949c8-372">Odvození z <xref:System.Windows.Controls.Control> umožňuje vytvořit vlastní uživatelské rozhraní než uživatelské ovládací prvky, ale může to vyžadovat více úsilí.</span><span class="sxs-lookup"><span data-stu-id="949c8-372">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="949c8-373">**Model elementu rozhraní**.</span><span class="sxs-lookup"><span data-stu-id="949c8-373">**Framework Element Model**.</span></span> <span data-ttu-id="949c8-374">Vlastní ovládací prvek je odvozen z, <xref:System.Windows.FrameworkElement> Pokud je jeho vzhled definován vlastní logikou vykreslování (nikoli šablony).</span><span class="sxs-lookup"><span data-stu-id="949c8-374">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="949c8-375">Následující příklad ukazuje vlastní číselnou kontrolu nahoru/dolů, která je odvozena z <xref:System.Windows.Controls.UserControl> :</span><span class="sxs-lookup"><span data-stu-id="949c8-375">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="949c8-376">Následující příklad ilustruje kód XAML, který je požadován pro zahrnutí uživatelského ovládacího prvku do <xref:System.Windows.Window> :</span><span class="sxs-lookup"><span data-stu-id="949c8-376">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="949c8-377">Následující obrázek znázorňuje `NumericUpDown` ovládací prvek hostovaný v <xref:System.Windows.Window> :</span><span class="sxs-lookup"><span data-stu-id="949c8-377">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Vlastní UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="949c8-379">Další informace o vlastních ovládacích prvcích najdete v tématu [Přehled vytváření ovládacích](controls/control-authoring-overview.md)prvků.</span><span class="sxs-lookup"><span data-stu-id="949c8-379">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="949c8-380">Osvědčené postupy pro WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-380">WPF best practices</span></span>

<span data-ttu-id="949c8-381">Stejně jako u jakékoli vývojové platformy je možné WPF použít různými způsoby, abyste dosáhli požadovaného výsledku.</span><span class="sxs-lookup"><span data-stu-id="949c8-381">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="949c8-382">Jako způsob, jak zajistit, aby vaše aplikace WPF poskytovaly požadované uživatelské prostředí a splňovaly požadavky cílové skupiny obecně, existují Doporučené osvědčené postupy pro přístupnost, globalizaci a lokalizaci a výkon.</span><span class="sxs-lookup"><span data-stu-id="949c8-382">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="949c8-383">Další informace naleznete v tématech:</span><span class="sxs-lookup"><span data-stu-id="949c8-383">For more information, see:</span></span>

- [<span data-ttu-id="949c8-384">Usnadnění</span><span class="sxs-lookup"><span data-stu-id="949c8-384">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="949c8-385">Globalizace a lokalizace WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-385">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="949c8-386">Výkon aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-386">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="949c8-387">Zabezpečení WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-387">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="949c8-388">Další kroky</span><span class="sxs-lookup"><span data-stu-id="949c8-388">Next steps</span></span>

<span data-ttu-id="949c8-389">Prohlédli jsme si klíčové funkce WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-389">We've looked at the key features of WPF.</span></span> <span data-ttu-id="949c8-390">Nyní je čas vytvořit svou první aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="949c8-390">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="949c8-391">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-391">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="949c8-392">Viz také</span><span class="sxs-lookup"><span data-stu-id="949c8-392">See also</span></span>

- [<span data-ttu-id="949c8-393">Začínáme s WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="949c8-393">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="949c8-394">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="949c8-394">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="949c8-395">Komunitní materiály pro WPF</span><span class="sxs-lookup"><span data-stu-id="949c8-395">WPF community resources</span></span>](getting-started/community-feedback.md)
