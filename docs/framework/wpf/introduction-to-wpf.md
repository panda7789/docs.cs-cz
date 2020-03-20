---
title: Úvod do WPF
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 511ea04a522804b4b2ea2ff173d6cdd738e5c7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186225"
---
# <a name="wpf-overview"></a><span data-ttu-id="1cc09-102">Přehled grafického subsystému WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="1cc09-102">WPF overview</span></span>

<span data-ttu-id="1cc09-103">Windows Presentation Foundation (WPF) umožňuje vytvářet desktopové klientské aplikace pro Windows s vizuálně ohromující uživatelské prostředí.</span><span class="sxs-lookup"><span data-stu-id="1cc09-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Ukázka ui ve zdravotnictví společnosti Contoso](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="1cc09-105">Jádrem WPF je rozlišení nezávislé a vektorové vykreslovací engine, který je vytvořen tak, aby využít moderní grafický hardware.</span><span class="sxs-lookup"><span data-stu-id="1cc09-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="1cc09-106">WPF rozšiřuje jádro o komplexní sadu funkcí pro vývoj aplikací, které zahrnují extensible Application Markup Language (XAML), ovládací prvky, datovou vazbu, rozložení, 2D a 3D grafiku, animaci, styly, šablony, dokumenty, média, text a Typografie.</span><span class="sxs-lookup"><span data-stu-id="1cc09-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="1cc09-107">WPF je součástí rozhraní .NET, takže můžete vytvářet aplikace, které obsahují další prvky rozhraní .NET API.</span><span class="sxs-lookup"><span data-stu-id="1cc09-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="1cc09-108">Tento přehled je určen pro nováčky a pokrývá klíčové možnosti a koncepty WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="1cc09-109">Program s WPF</span><span class="sxs-lookup"><span data-stu-id="1cc09-109">Program with WPF</span></span>

<span data-ttu-id="1cc09-110">WPF existuje jako podmnožina typů .NET, které jsou (z větší části) umístěné v oboru <xref:System.Windows> názvů.</span><span class="sxs-lookup"><span data-stu-id="1cc09-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="1cc09-111">Pokud jste dříve vytvořili aplikace s rozhraním .NET pomocí spravovaných technologií, jako je ASP.NET a Windows Forms, základní wpf programovací prostředí by mělo být známé; můžete vytvořit instanci tříd, nastavit vlastnosti, metody volání a zpracování událostí pomocí oblíbeného programovacího jazyka .NET, například C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1cc09-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="1cc09-112">WPF obsahuje další programovací konstrukce, které vylepšují vlastnosti a události: [vlastnosti závislostí](advanced/dependency-properties-overview.md) a [směrované události](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="1cc09-113">Značky a kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="1cc09-113">Markup and code-behind</span></span>

<span data-ttu-id="1cc09-114">WPF umožňuje vyvíjet aplikaci pomocí *značek* a *kód na pozadí*, prostředí, s nimiž ASP.NET vývojáři by měli být obeznámeni.</span><span class="sxs-lookup"><span data-stu-id="1cc09-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="1cc09-115">Obecně se používá XAML značky k implementaci vzhledu aplikace při použití spravovaných programovacích jazyků (kód na pozadí) k implementaci jeho chování.</span><span class="sxs-lookup"><span data-stu-id="1cc09-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="1cc09-116">Toto oddělení vzhledu a chování má následující výhody:</span><span class="sxs-lookup"><span data-stu-id="1cc09-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="1cc09-117">Náklady na vývoj a údržbu jsou sníženy, protože značky specifické pro vzhled nejsou úzce spojeny s kódem specifickým pro chování.</span><span class="sxs-lookup"><span data-stu-id="1cc09-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="1cc09-118">Vývoj je efektivnější, protože návrháři mohou implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="1cc09-119">[Globalizace a lokalizace](advanced/wpf-globalization-and-localization-overview.md) pro WPF aplikace je zjednodušena.</span><span class="sxs-lookup"><span data-stu-id="1cc09-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="1cc09-120">Kód</span><span class="sxs-lookup"><span data-stu-id="1cc09-120">Markup</span></span>

<span data-ttu-id="1cc09-121">XAML je značkovací jazyk založený na xml, který deklarativně implementuje vzhled aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="1cc09-122">Obvykle se používá k vytvoření oken, dialogových oken, stránek a uživatelských ovládacích prvků a k jejich vyplnění ovládacími prvky, obrazci a grafikou.</span><span class="sxs-lookup"><span data-stu-id="1cc09-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="1cc09-123">Následující příklad používá XAML k implementaci vzhledu okna, které obsahuje jediné tlačítko:</span><span class="sxs-lookup"><span data-stu-id="1cc09-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="1cc09-124">Konkrétně tento XAML definuje okno a tlačítko `Window` pomocí `Button` a prvky, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1cc09-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="1cc09-125">Každý prvek je konfigurován s atributy, `Title` jako je například atribut `Window` prvku k určení textu záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="1cc09-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="1cc09-126">Za běhu WPF převede prvky a atributy, které jsou definovány v značkování na instance tříd WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="1cc09-127">Například `Window` prvek je převeden na instanci <xref:System.Windows.Window> třídy, <xref:System.Windows.Window.Title%2A> jejíž `Title` vlastnost je hodnota atributu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="1cc09-128">Následující obrázek znázorňuje uživatelské rozhraní (UI), které je definováno XAML v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Okno, které obsahuje tlačítko](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="1cc09-130">Vzhledem k tomu, že XAML je založen na XML, uživatelské rozhraní, které s ním tvoříte, je sestaveno v hierarchii vnořených prvků známých jako [strom elementů](advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="1cc09-131">Strom elementů poskytuje logický a intuitivní způsob vytváření a správy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1cc09-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="1cc09-132">Kód na pozadí</span><span class="sxs-lookup"><span data-stu-id="1cc09-132">Code-behind</span></span>

<span data-ttu-id="1cc09-133">Hlavním chováním aplikace je implementace funkcí, které reagují na interakce uživatele, včetně zpracování událostí (například klepnutí na nabídku, panel nástrojů nebo tlačítko) a volání obchodní logiky a logiky přístupu k datům v reakci.</span><span class="sxs-lookup"><span data-stu-id="1cc09-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="1cc09-134">V WPF toto chování je implementováno v kódu, který je spojen se značkami.</span><span class="sxs-lookup"><span data-stu-id="1cc09-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="1cc09-135">Tento typ kódu se označuje jako kód na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1cc09-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="1cc09-136">Následující příklad ukazuje aktualizované značky z předchozího příkladu a kód na pozadí:</span><span class="sxs-lookup"><span data-stu-id="1cc09-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

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

<span data-ttu-id="1cc09-137">V tomto příkladu kód na pozadí implementuje <xref:System.Windows.Window> třídu, která je odvozena z třídy.</span><span class="sxs-lookup"><span data-stu-id="1cc09-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="1cc09-138">Atribut `x:Class` se používá k přidružení značky ke třídě s kódem na pozadí.</span><span class="sxs-lookup"><span data-stu-id="1cc09-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="1cc09-139">`InitializeComponent`je volána z konstruktoru třídy s kódem za sloučit ui, který je definován v značkování s kódem na pozadí třídy.</span><span class="sxs-lookup"><span data-stu-id="1cc09-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="1cc09-140">(`InitializeComponent` je generována pro vás, když je vytvořena aplikace, což je důvod, proč není nutné implementovat ručně.) Kombinace `x:Class` a `InitializeComponent` ujistěte se, že vaše implementace je správně inicializována při každém vytvoření.</span><span class="sxs-lookup"><span data-stu-id="1cc09-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="1cc09-141">Třída s kódem na pozadí také implementuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události pro událost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="1cc09-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="1cc09-142">Po klepnutí na tlačítko se na obslužné rutině události zobrazí okno se zprávou voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metody.</span><span class="sxs-lookup"><span data-stu-id="1cc09-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="1cc09-143">Následující obrázek znázorňuje výsledek klepnutí na tlačítko:</span><span class="sxs-lookup"><span data-stu-id="1cc09-143">The following figure shows the result when the button is clicked:</span></span>

![Okno se zprávou](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="1cc09-145">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="1cc09-145">Controls</span></span>

<span data-ttu-id="1cc09-146">Uživatelské prostředí, které jsou dodané modelaplikace jsou konstruovány ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1cc09-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="1cc09-147">V *WPF, ovládací prvek* je zastřešující termín, který se vztahuje na kategorii WPF třídy, které jsou hostovány v okně nebo na stránce, mají uživatelské rozhraní a implementovat některé chování.</span><span class="sxs-lookup"><span data-stu-id="1cc09-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="1cc09-148">Další informace naleznete v [tématu Controls](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="1cc09-149">WPF ovládací prvky podle funkce</span><span class="sxs-lookup"><span data-stu-id="1cc09-149">WPF controls by function</span></span>

<span data-ttu-id="1cc09-150">Integrované ovládací prvky WPF jsou uvedeny zde:</span><span class="sxs-lookup"><span data-stu-id="1cc09-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="1cc09-151">**Tlačítka** <xref:System.Windows.Controls.Button> : <xref:System.Windows.Controls.Primitives.RepeatButton>a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="1cc09-152">**Zobrazení**dat <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>: <xref:System.Windows.Controls.TreeView>, a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="1cc09-153">**Zobrazení a**výběr <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker>data : a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="1cc09-154">**Dialogová** <xref:Microsoft.Win32.OpenFileDialog>okna <xref:System.Windows.Controls.PrintDialog>: <xref:Microsoft.Win32.SaveFileDialog>, , a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="1cc09-155">**Digitální inkoust** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="1cc09-156">**Dokumenty** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, , a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="1cc09-157">**Vstup** <xref:System.Windows.Controls.TextBox>: <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="1cc09-158">**Rozložení** <xref:System.Windows.Controls.Border>: <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, <xref:System.Windows.Controls.WrapPanel>, , , , , , , , , a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="1cc09-159">**Média** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>, a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="1cc09-160">**Menu**: <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="1cc09-161">**Navigace** <xref:System.Windows.Controls.Frame>: <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="1cc09-162">**Výběr** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="1cc09-163">**Informace o uživateli** <xref:System.Windows.Controls.AccessText>: <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar> <xref:System.Windows.Controls.Primitives.StatusBar>, , a .</span><span class="sxs-lookup"><span data-stu-id="1cc09-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="1cc09-164">Vstup a příkazy</span><span class="sxs-lookup"><span data-stu-id="1cc09-164">Input and commands</span></span>

<span data-ttu-id="1cc09-165">Ovládací prvky nejčastěji detekují vstup uživatele a reagují na něj.</span><span class="sxs-lookup"><span data-stu-id="1cc09-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="1cc09-166">[Vstupní systém WPF](advanced/input-overview.md) používá přímé i směrované události pro podporu zadávání textu, správy fokusu a umístění myši.</span><span class="sxs-lookup"><span data-stu-id="1cc09-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="1cc09-167">Aplikace mají často složité vstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="1cc09-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="1cc09-168">WPF poskytuje [příkazový systém,](advanced/commanding-overview.md) který odděluje akce vstupu uživatele od kódu, který reaguje na tyto akce.</span><span class="sxs-lookup"><span data-stu-id="1cc09-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="1cc09-169">Rozložení</span><span class="sxs-lookup"><span data-stu-id="1cc09-169">Layout</span></span>

<span data-ttu-id="1cc09-170">Při vytváření uživatelského rozhraní uspořádáte ovládací prvky podle umístění a velikosti tak, aby vytvářela rozložení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="1cc09-171">Klíčovým požadavkem každého rozvržení je přizpůsobit se změnám velikosti okna a nastavení zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="1cc09-172">Spíše než nutit psát kód přizpůsobit rozložení za těchto okolností, WPF poskytuje prvotřídní, rozšiřitelné rozložení systému pro vás.</span><span class="sxs-lookup"><span data-stu-id="1cc09-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="1cc09-173">Základním kamenem systému rozvržení je relativní umístění, což zvyšuje schopnost přizpůsobit se měnícím se podmínkám okna a zobrazení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="1cc09-174">Kromě toho systém rozložení spravuje vyjednávání mezi ovládacími prvky k určení rozložení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="1cc09-175">Vyjednávání je dvoustupňový proces: nejprve ovládací prvek sdělí nadřazenému objektu, jaké umístění a velikost vyžaduje; za druhé, nadřazený řekne ovládacímu prvku, jaký prostor může mít.</span><span class="sxs-lookup"><span data-stu-id="1cc09-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="1cc09-176">Systém rozložení je vystaven podřízeným ovládacím prvkům prostřednictvím základních tříd WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="1cc09-177">Pro běžná rozložení, jako jsou mřížky, stohování a ukotvení, wpf obsahuje několik ovládacích prvků rozložení:</span><span class="sxs-lookup"><span data-stu-id="1cc09-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="1cc09-178"><xref:System.Windows.Controls.Canvas>: Podřízené ovládací prvky poskytují vlastní rozložení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="1cc09-179"><xref:System.Windows.Controls.DockPanel>: Podřízené ovládací prvky jsou zarovnány k okrajům panelu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="1cc09-180"><xref:System.Windows.Controls.Grid>: Podřízené ovládací prvky jsou umístěny podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="1cc09-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="1cc09-181"><xref:System.Windows.Controls.StackPanel>: Podřízené ovládací prvky jsou skládané svisle nebo vodorovně.</span><span class="sxs-lookup"><span data-stu-id="1cc09-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="1cc09-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Podřízené ovládací prvky jsou virtualizovány a uspořádány na jednom řádku, který je vodorovně nebo vertikálně orientovaný.</span><span class="sxs-lookup"><span data-stu-id="1cc09-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="1cc09-183"><xref:System.Windows.Controls.WrapPanel>: Podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zalomené na další řádek, pokud je na aktuálním řádku více ovládacích prvků, než umožňuje prostor.</span><span class="sxs-lookup"><span data-stu-id="1cc09-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="1cc09-184">Následující příklad používá <xref:System.Windows.Controls.DockPanel> rozložení několika <xref:System.Windows.Controls.TextBox> ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="1cc09-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="1cc09-185">Umožňuje <xref:System.Windows.Controls.DockPanel> podřízené <xref:System.Windows.Controls.TextBox> ovládací prvky, aby mu řekli, jak je uspořádat.</span><span class="sxs-lookup"><span data-stu-id="1cc09-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="1cc09-186">Chcete-li to <xref:System.Windows.Controls.DockPanel> provést, `Dock` implementuje připojené vlastnosti, která je vystavena podřízené ovládací prvky, aby každý z nich určit styl doku.</span><span class="sxs-lookup"><span data-stu-id="1cc09-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="1cc09-187">Vlastnost, která je implementována nadřazeným ovládacím prvkem pro použití podřízenými ovládacími prvky, je konstrukce WPF nazývaná [připojená vlastnost](advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="1cc09-188">Následující obrázek znázorňuje výsledek značky XAML v předchozím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Stránka DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="1cc09-190">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="1cc09-190">Data binding</span></span>

<span data-ttu-id="1cc09-191">Většina aplikací je vytvořena tak, aby uživatelům poskytovala prostředky k zobrazení a úpravám dat.</span><span class="sxs-lookup"><span data-stu-id="1cc09-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="1cc09-192">Pro aplikace WPF je práce ukládání a přístupu k datům již zajištěna technologiemi, jako je SQL Server a ADO .NET.</span><span class="sxs-lookup"><span data-stu-id="1cc09-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="1cc09-193">Po přístupu k datům a načtení do spravovaných objektů aplikace začíná tvrdá práce pro aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="1cc09-194">V podstatě se jedná o dvě věci:</span><span class="sxs-lookup"><span data-stu-id="1cc09-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="1cc09-195">Kopírování dat ze spravovaných objektů do ovládacích prvků, kde lze data zobrazit a upravit.</span><span class="sxs-lookup"><span data-stu-id="1cc09-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="1cc09-196">Zajištění, že změny provedené v datech pomocí ovládacích prvků jsou zkopírovány zpět do spravovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="1cc09-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="1cc09-197">Pro zjednodušení vývoje aplikací WPF poskytuje modul datové vazby automaticky provádět tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="1cc09-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="1cc09-198">Základní jednotkou modulu datové <xref:System.Windows.Data.Binding> vazby je třída, jejíž úlohou je svázat ovládací prvek (cíl vazby) s datovým objektem (zdrojem vazby).</span><span class="sxs-lookup"><span data-stu-id="1cc09-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="1cc09-199">Tento vztah je znázorněn na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1cc09-199">This relationship is illustrated by the following figure:</span></span>

![Základní diagram datové vazby](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="1cc09-201">Následující příklad ukazuje, jak <xref:System.Windows.Controls.TextBox> vázat a na `Person` instanci vlastního objektu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="1cc09-202">Implementace `Person` je uvedena v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="1cc09-203">Následující značky svážou <xref:System.Windows.Controls.TextBox> instanci `Person` vlastního objektu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

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

<span data-ttu-id="1cc09-204">V tomto příkladu `Person` je instance třídy v kódu na pozadí a `DataBindingWindow`je nastaven jako kontext dat pro .</span><span class="sxs-lookup"><span data-stu-id="1cc09-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="1cc09-205">Ve značkách <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> je vlastnost vlastnosti `Person.Name` vázána na`{Binding ... }`vlastnost (pomocí syntaxe " XAML).</span><span class="sxs-lookup"><span data-stu-id="1cc09-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="1cc09-206">Tento XAML říká WPF <xref:System.Windows.Controls.TextBox> svázat `Person` ovládací prvek k <xref:System.Windows.FrameworkElement.DataContext%2A> objektu, který je uložen ve vlastnosti okna.</span><span class="sxs-lookup"><span data-stu-id="1cc09-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="1cc09-207">WPF datový vázací modul poskytuje další podporu, která zahrnuje ověřování, řazení, filtrování a seskupování.</span><span class="sxs-lookup"><span data-stu-id="1cc09-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="1cc09-208">Kromě toho datová vazba podporuje použití datových šablon k vytvoření vlastního uživatelského rozhraní pro vázaná data, pokud uživatelské rozhraní zobrazené standardními ovládacími prvky WPF není vhodné.</span><span class="sxs-lookup"><span data-stu-id="1cc09-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="1cc09-209">Další informace naleznete v [tématu Přehled datových vazeb](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="1cc09-210">Grafika</span><span class="sxs-lookup"><span data-stu-id="1cc09-210">Graphics</span></span>

<span data-ttu-id="1cc09-211">WPF představuje rozsáhlou, škálovatelnou a flexibilní sadu grafických funkcí, které mají následující výhody:</span><span class="sxs-lookup"><span data-stu-id="1cc09-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="1cc09-212">**Grafika nezávislá na rozlišení a na zařízení**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="1cc09-213">Základní jednotkou měření v grafickém systému WPF je pixel nezávislý na zařízení, který je 1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávislé na rozlišení a nezávislé na zařízení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="1cc09-214">Každý pixel nezávislý na zařízení se automaticky změní tak, aby odpovídal nastavení bodů na palec (dpi) systému, ve kterých se vykresluje.</span><span class="sxs-lookup"><span data-stu-id="1cc09-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="1cc09-215">**Vylepšená přesnost**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-215">**Improved precision**.</span></span> <span data-ttu-id="1cc09-216">Souřadnicový systém WPF se měří s dvojitou přesností s plovoucí desetinnou desetinnou tácek spíše než s jednou přesností.</span><span class="sxs-lookup"><span data-stu-id="1cc09-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="1cc09-217">Transformace a hodnoty krytí jsou také vyjádřeny jako dvojitá přesnost.</span><span class="sxs-lookup"><span data-stu-id="1cc09-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="1cc09-218">WPF také podporuje široký barevný gamut (scRGB) a poskytuje integrovanou podporu pro správu vstupů z různých barevných prostorů.</span><span class="sxs-lookup"><span data-stu-id="1cc09-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="1cc09-219">**Pokročilá podpora grafiky a animace**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="1cc09-220">WPF zjednodušuje programování grafiky správou animačních scén za vás; není třeba se obávat zpracování scény, vykreslování smyček a bilineární interpolace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="1cc09-221">Kromě toho WPF poskytuje podporu testování přístupů a plnou podporu alfa skládání.</span><span class="sxs-lookup"><span data-stu-id="1cc09-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="1cc09-222">**Hardwarová akcelerace**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-222">**Hardware acceleration**.</span></span> <span data-ttu-id="1cc09-223">Grafický systém WPF využívá grafický hardware k minimalizaci využití procesoru.</span><span class="sxs-lookup"><span data-stu-id="1cc09-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="1cc09-224">2D obrazce</span><span class="sxs-lookup"><span data-stu-id="1cc09-224">2D shapes</span></span>

<span data-ttu-id="1cc09-225">WPF poskytuje knihovnu běžných vektorem nakreslených 2D tvarů, jako jsou obdélníky a elipsy, které jsou znázorněny na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1cc09-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Elipsy a obdélníky](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="1cc09-227">Zajímavou schopností tvarů je, že nejsou jen pro zobrazení; obrazce implementovat mnoho funkcí, které očekáváte od ovládacích prvků, včetně klávesnice a myši vstupu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="1cc09-228">Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> událost <xref:System.Windows.Shapes.Ellipse> zpracování:</span><span class="sxs-lookup"><span data-stu-id="1cc09-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="1cc09-229">Následující obrázek znázorňuje, co je vyrobeno podle předchozího kódu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-229">The following figure shows what is produced by the preceding code:</span></span>

![Okno s textem "klikli jste na&#33; elipsy"](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="1cc09-231">Další informace naleznete [v tématu Obrazce a základní výkres v přehledu WPF](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="1cc09-232">2D geometrie</span><span class="sxs-lookup"><span data-stu-id="1cc09-232">2D geometries</span></span>

<span data-ttu-id="1cc09-233">2D tvary poskytované wpf pokrývají standardní sadu základních tvarů.</span><span class="sxs-lookup"><span data-stu-id="1cc09-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="1cc09-234">Může však být nutné vytvořit vlastní obrazce, které usnadní návrh přizpůsobeného uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1cc09-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="1cc09-235">Pro tento účel WPF poskytuje geometrie.</span><span class="sxs-lookup"><span data-stu-id="1cc09-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="1cc09-236">Následující obrázek znázorňuje použití geometrií k vytvoření vlastního tvaru, který lze nakreslit přímo, použít jako stopu nebo použít k oříznutí jiných tvarů a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1cc09-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="1cc09-237"><xref:System.Windows.Shapes.Path>objekty lze použít k kreslení uzavřených nebo otevřených tvarů, více tvarů a dokonce i zakřivených tvarů.</span><span class="sxs-lookup"><span data-stu-id="1cc09-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="1cc09-238"><xref:System.Windows.Media.Geometry>objekty lze použít pro oříznutí, testování přístupů a vykreslování 2D grafických dat.</span><span class="sxs-lookup"><span data-stu-id="1cc09-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Různá použití cesty](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="1cc09-240">Další informace naleznete v [tématu Přehled geometrie](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="1cc09-241">2D efekty</span><span class="sxs-lookup"><span data-stu-id="1cc09-241">2D effects</span></span>

<span data-ttu-id="1cc09-242">Podmnožina 2D funkcí WPF zahrnuje vizuální efekty, jako jsou přechody, bitmapy, kresby, malování videa, otočení, změna měřítka a zkosení.</span><span class="sxs-lookup"><span data-stu-id="1cc09-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="1cc09-243">To vše je dosaženo kartáči; následující obrázek ukazuje některé příklady:</span><span class="sxs-lookup"><span data-stu-id="1cc09-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Ilustrace různých štětců](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="1cc09-245">Další informace naleznete v tématu [Přehled stop y WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="1cc09-246">3D vykreslování</span><span class="sxs-lookup"><span data-stu-id="1cc09-246">3D rendering</span></span>

<span data-ttu-id="1cc09-247">WPF také obsahuje funkce 3D vykreslování, které se integrují s 2D grafikou, aby bylo možné vytvářet zajímavější a zajímavější uživatelská rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1cc09-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="1cc09-248">Například následující obrázek znázorňuje 2D obrazy vykreslené na 3D tvarech:</span><span class="sxs-lookup"><span data-stu-id="1cc09-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Ukázkový snímek obrazovky Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="1cc09-250">Další informace naleznete v tématu [Přehled 3D grafiky](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="1cc09-251">Animace</span><span class="sxs-lookup"><span data-stu-id="1cc09-251">Animation</span></span>

<span data-ttu-id="1cc09-252">Podpora animací WPF umožňuje vytvářet ovládací prvky růst, třást, točit a slábnout, vytvářet zajímavé přechody stránek a další.</span><span class="sxs-lookup"><span data-stu-id="1cc09-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="1cc09-253">Můžete animovat většinu tříd WPF, dokonce i vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="1cc09-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="1cc09-254">Následující obrázek znázorňuje jednoduchou animaci v akci:</span><span class="sxs-lookup"><span data-stu-id="1cc09-254">The following figure shows a simple animation in action:</span></span>

![Obrázky animované krychle](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="1cc09-256">Další informace naleznete v [tématu Přehled animace](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="1cc09-257">Média</span><span class="sxs-lookup"><span data-stu-id="1cc09-257">Media</span></span>

<span data-ttu-id="1cc09-258">Jedním ze způsobů, jak zprostředkovat bohatý obsah, je použití audiovizuálních médií.</span><span class="sxs-lookup"><span data-stu-id="1cc09-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="1cc09-259">WPF poskytuje speciální podporu pro obrázky, video a zvuk.</span><span class="sxs-lookup"><span data-stu-id="1cc09-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="1cc09-260">Image</span><span class="sxs-lookup"><span data-stu-id="1cc09-260">Images</span></span>

<span data-ttu-id="1cc09-261">Obrázky jsou společné pro většinu aplikací a WPF poskytuje několik způsobů, jak je používat.</span><span class="sxs-lookup"><span data-stu-id="1cc09-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="1cc09-262">Následující obrázek znázorňuje uživatelské rozhraní se seznamem, který obsahuje miniatury obrázků.</span><span class="sxs-lookup"><span data-stu-id="1cc09-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="1cc09-263">Když je vybraná miniatura, zobrazí se obrázek v plné velikosti.</span><span class="sxs-lookup"><span data-stu-id="1cc09-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Miniatury obrázků a obrázek v plné&#45;velikosti](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="1cc09-265">Další informace naleznete v tématu [Přehled zobrazování .](graphics-multimedia/imaging-overview.md)</span><span class="sxs-lookup"><span data-stu-id="1cc09-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="1cc09-266">Video a zvuk</span><span class="sxs-lookup"><span data-stu-id="1cc09-266">Video and audio</span></span>

<span data-ttu-id="1cc09-267">Ovládací <xref:System.Windows.Controls.MediaElement> prvek je schopen přehrávat video i zvuk a je dostatečně flexibilní, aby byl základem pro vlastní přehrávač médií.</span><span class="sxs-lookup"><span data-stu-id="1cc09-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="1cc09-268">Následující značky XAML implementují přehrávač médií:</span><span class="sxs-lookup"><span data-stu-id="1cc09-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="1cc09-269">Okno na následujícím obrázku <xref:System.Windows.Controls.MediaElement> znázorňuje ovládací prvek v akci:</span><span class="sxs-lookup"><span data-stu-id="1cc09-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Ovládací prvek MediaElement se zvukem a videem](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="1cc09-271">Další informace naleznete v [tématu Grafika a multimédia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="1cc09-272">Text a typografii</span><span class="sxs-lookup"><span data-stu-id="1cc09-272">Text and typography</span></span>

<span data-ttu-id="1cc09-273">Pro usnadnění vykreslování textu ve vysoké kvalitě nabízí WPF následující funkce:</span><span class="sxs-lookup"><span data-stu-id="1cc09-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="1cc09-274">Podpora písma OpenType.</span><span class="sxs-lookup"><span data-stu-id="1cc09-274">OpenType font support.</span></span>

- <span data-ttu-id="1cc09-275">Vylepšení cleartype.</span><span class="sxs-lookup"><span data-stu-id="1cc09-275">ClearType enhancements.</span></span>

- <span data-ttu-id="1cc09-276">Vysoký výkon, který využívá hardwarovou akceleraci.</span><span class="sxs-lookup"><span data-stu-id="1cc09-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="1cc09-277">Integrace textu s médii, grafikou a animací.</span><span class="sxs-lookup"><span data-stu-id="1cc09-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="1cc09-278">Mezinárodní podpora písem a záložní mechanismy.</span><span class="sxs-lookup"><span data-stu-id="1cc09-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="1cc09-279">Jako ukázku integrace textu s grafikou, následující obrázek ukazuje použití textových dekorací:</span><span class="sxs-lookup"><span data-stu-id="1cc09-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Text s různými textovými dekoracemi](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="1cc09-281">Další informace naleznete [v tématu Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="1cc09-282">Přizpůsobení aplikací WPF</span><span class="sxs-lookup"><span data-stu-id="1cc09-282">Customize WPF apps</span></span>

<span data-ttu-id="1cc09-283">Až do tohoto okamžiku jste viděli základní stavební bloky WPF pro vývoj aplikací.</span><span class="sxs-lookup"><span data-stu-id="1cc09-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="1cc09-284">Model aplikace se používá k hostování a doručování obsahu aplikace, který se skládá hlavně z ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1cc09-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="1cc09-285">Chcete-li zjednodušit uspořádání ovládacích prvků v uživatelském rozhraní a zajistit, aby bylo uspořádání zachováno tváří v tvář změnám velikosti okna a nastavení zobrazení, použijte systém rozložení WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="1cc09-286">Vzhledem k tomu, že většina aplikací umožňuje uživatelům pracovat s daty, můžete pomocí datové vazby omezit práci integrace uživatelského rozhraní s daty.</span><span class="sxs-lookup"><span data-stu-id="1cc09-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="1cc09-287">Chcete-li zlepšit vizuální vzhled aplikace, použijte komplexní rozsah grafiky, animace a podporu médií poskytované WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="1cc09-288">Často však základy nestačí pro vytvoření a správu skutečně odlišného a vizuálně ohromujícího uživatelského zážitku.</span><span class="sxs-lookup"><span data-stu-id="1cc09-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="1cc09-289">Standardní ovládací prvky WPF nemusí integrovat s požadovaný vzhled aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="1cc09-290">Data nemusí být zobrazena nejefektivnějším způsobem.</span><span class="sxs-lookup"><span data-stu-id="1cc09-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="1cc09-291">Celkové uživatelské prostředí aplikace nemusí být vhodné pro výchozí vzhled motivů systému Windows.</span><span class="sxs-lookup"><span data-stu-id="1cc09-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="1cc09-292">V mnoha ohledech, prezentační technologie potřebuje vizuální rozšiřitelnost, stejně jako jakýkoli jiný typ rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="1cc09-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="1cc09-293">Z tohoto důvodu WPF poskytuje řadu mechanismů pro vytváření jedinečných uživatelských prostředí, včetně bohatého modelu obsahu pro ovládací prvky, aktivační události, šablony ovládacích prvků a dat, styly, prostředky uživatelského rozhraní a motivy a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="1cc09-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="1cc09-294">Model obsahu</span><span class="sxs-lookup"><span data-stu-id="1cc09-294">Content model</span></span>

<span data-ttu-id="1cc09-295">Hlavním účelem většiny ovládacích prvků WPF je zobrazení obsahu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="1cc09-296">V WPF typ a počet položek, které mohou představovat obsah ovládacího prvku se označuje jako *model obsahu*ovládacího prvku .</span><span class="sxs-lookup"><span data-stu-id="1cc09-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="1cc09-297">Některé ovládací prvky mohou obsahovat jednu položku a typ obsahu. například obsah a <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která <xref:System.Windows.Controls.TextBox.Text%2A> je přiřazena vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1cc09-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="1cc09-298">Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="1cc09-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="1cc09-299">Následující obrázek znázorňuje výsledek:</span><span class="sxs-lookup"><span data-stu-id="1cc09-299">The following figure shows the result:</span></span>

![Ovládací prvek TextBox, který obsahuje text](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="1cc09-301">Jiné ovládací prvky však mohou obsahovat více položek různých typů obsahu. obsah <xref:System.Windows.Controls.Button>vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> , může obsahovat různé položky včetně ovládacích prvků rozložení, textu, obrázků a obrazců.</span><span class="sxs-lookup"><span data-stu-id="1cc09-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="1cc09-302">Následující příklad ukazuje <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.DockPanel>obsah, který obsahuje <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a <xref:System.Windows.Controls.MediaElement>, a a :</span><span class="sxs-lookup"><span data-stu-id="1cc09-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

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

<span data-ttu-id="1cc09-303">Na následujícím obrázku je znázorněn obsah tohoto tlačítka:</span><span class="sxs-lookup"><span data-stu-id="1cc09-303">The following figure shows the content of this button:</span></span>

![Tlačítko, které obsahuje více typů obsahu](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="1cc09-305">Další informace o typech obsahu, který je podporován různými ovládacími prvky, naleznete v [tématu WPF model obsahu](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="1cc09-306">Aktivační události</span><span class="sxs-lookup"><span data-stu-id="1cc09-306">Triggers</span></span>

<span data-ttu-id="1cc09-307">Přestože hlavním účelem značky XAML je implementovat vzhled aplikace, můžete také použít XAML k implementaci některých aspektů chování aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="1cc09-308">Jedním z příkladů je použití aktivačních událostí ke změně vzhledu aplikace na základě interakcí s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="1cc09-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="1cc09-309">Další informace naleznete v [tématu Styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="1cc09-310">Řídicí šablony</span><span class="sxs-lookup"><span data-stu-id="1cc09-310">Control templates</span></span>

<span data-ttu-id="1cc09-311">Výchozí uživatelská rozhraní pro ovládací prvky WPF jsou obvykle konstruovány z jiných ovládacích prvků a obrazců.</span><span class="sxs-lookup"><span data-stu-id="1cc09-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="1cc09-312">Například a <xref:System.Windows.Controls.Button> se skládá <xref:Microsoft.Windows.Themes.ButtonChrome> <xref:System.Windows.Controls.ContentPresenter> z obou a ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1cc09-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="1cc09-313">Poskytuje <xref:Microsoft.Windows.Themes.ButtonChrome> standardní vzhled tlačítka, <xref:System.Windows.Controls.ContentPresenter> zatímco zobrazuje obsah tlačítka, jak <xref:System.Windows.Controls.ContentControl.Content%2A> je určeno vlastností.</span><span class="sxs-lookup"><span data-stu-id="1cc09-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="1cc09-314">Někdy může být výchozí vzhled ovládacího prvku neslučitelný s celkovým vzhledem aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="1cc09-315">V takovém případě můžete <xref:System.Windows.Controls.ControlTemplate> změnit vzhled uživatelského rozhraní ovládacího prvku bez změny jeho obsahu a chování.</span><span class="sxs-lookup"><span data-stu-id="1cc09-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="1cc09-316">Následující příklad ukazuje, jak změnit <xref:System.Windows.Controls.Button> vzhled a <xref:System.Windows.Controls.ControlTemplate>pomocí :</span><span class="sxs-lookup"><span data-stu-id="1cc09-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="1cc09-317">V tomto příkladu bylo výchozí uživatelské rozhraní <xref:System.Windows.Shapes.Ellipse> tlačítka nahrazeno rozhraním, které <xref:System.Windows.Media.RadialGradientBrush>má tmavě modré ohraničení a je vyplněno pomocí rozhraní .</span><span class="sxs-lookup"><span data-stu-id="1cc09-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="1cc09-318">Ovládací <xref:System.Windows.Controls.ContentPresenter> prvek zobrazí obsah <xref:System.Windows.Controls.Button>, "Klikněte na mě!"</span><span class="sxs-lookup"><span data-stu-id="1cc09-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="1cc09-319">Po <xref:System.Windows.Controls.Button> klepnutí na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost je stále aktivována <xref:System.Windows.Controls.Button> jako součást výchozí chování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cc09-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="1cc09-320">Výsledek je zobrazen na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1cc09-320">The result is shown in the following figure:</span></span>

![Eliptické tlačítko a druhé okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="1cc09-322">Šablony dat</span><span class="sxs-lookup"><span data-stu-id="1cc09-322">Data templates</span></span>

<span data-ttu-id="1cc09-323">Zatímco šablona ovládacího prvku umožňuje určit vzhled ovládacího prvku, šablona dat umožňuje určit vzhled obsahu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cc09-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="1cc09-324">Šablony dat se často používají k vylepšení způsobu zobrazení vázaných dat.</span><span class="sxs-lookup"><span data-stu-id="1cc09-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="1cc09-325">Následující obrázek znázorňuje <xref:System.Windows.Controls.ListBox> výchozí vzhled pro objekt, který je vázán na `Task` kolekci objektů, kde každý úkol má název, popis a prioritu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Seznam s výchozím vzhledem](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="1cc09-327">Výchozí vzhled je to, co <xref:System.Windows.Controls.ListBox>byste očekávali od .</span><span class="sxs-lookup"><span data-stu-id="1cc09-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="1cc09-328">Výchozí vzhled každé úlohy však obsahuje pouze název úkolu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="1cc09-329">Chcete-li zobrazit název, popis a prioritu <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>úkolu, musí být výchozí vzhled vázaných položek seznamu ovládacího prvku změněn pomocí .</span><span class="sxs-lookup"><span data-stu-id="1cc09-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="1cc09-330">Následující XAML definuje takový <xref:System.Windows.DataTemplate>, který se použije pro <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> každý úkol pomocí atributu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

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

<span data-ttu-id="1cc09-331">Následující obrázek znázorňuje účinek tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-331">The following figure shows the effect of this code:</span></span>

![Seznam, který používá šablonu dat](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="1cc09-333">Všimněte <xref:System.Windows.Controls.ListBox> si, že si zachovala své chování a celkový vzhled; pouze vzhled obsahu zobrazeného v seznamu se změnil.</span><span class="sxs-lookup"><span data-stu-id="1cc09-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="1cc09-334">Další informace naleznete [v tématu Přehled templating dat](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="1cc09-335">Styly</span><span class="sxs-lookup"><span data-stu-id="1cc09-335">Styles</span></span>

<span data-ttu-id="1cc09-336">Styly umožňují vývojářům a návrhářům standardizovat konkrétní vzhled svého produktu.</span><span class="sxs-lookup"><span data-stu-id="1cc09-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="1cc09-337">WPF poskytuje silný styl modelu, základem, který je <xref:System.Windows.Style> prvek.</span><span class="sxs-lookup"><span data-stu-id="1cc09-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="1cc09-338">Následující příklad vytvoří styl, který nastaví <xref:System.Windows.Controls.Button> barvu pozadí `Orange`pro každé okno na :</span><span class="sxs-lookup"><span data-stu-id="1cc09-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

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

<span data-ttu-id="1cc09-339">Protože tento styl <xref:System.Windows.Controls.Button> cílí na všechny ovládací prvky, styl se automaticky použije na všechna tlačítka v okně, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="1cc09-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Dvě oranžová tlačítka](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="1cc09-341">Další informace naleznete v [tématu Styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="1cc09-342">Zdroje informací</span><span class="sxs-lookup"><span data-stu-id="1cc09-342">Resources</span></span>

<span data-ttu-id="1cc09-343">Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může zahrnovat cokoli od písem a barev pozadí až po šablony ovládacích prvků, šablony dat a styly.</span><span class="sxs-lookup"><span data-stu-id="1cc09-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="1cc09-344">Podporu WPF pro prostředky uživatelského rozhraní můžete použít k zapouzdření těchto prostředků do jednoho umístění pro opakované použití.</span><span class="sxs-lookup"><span data-stu-id="1cc09-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="1cc09-345">Následující příklad definuje společnou barvu pozadí, která <xref:System.Windows.Controls.Button> je <xref:System.Windows.Controls.Label>sdílena a a :</span><span class="sxs-lookup"><span data-stu-id="1cc09-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

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

<span data-ttu-id="1cc09-346">Tento příklad implementuje prostředek barvy `Window.Resources` pozadí pomocí elementu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1cc09-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="1cc09-347">Tento zdroj je k dispozici <xref:System.Windows.Window>pro všechny podřízené položky rozhraní .</span><span class="sxs-lookup"><span data-stu-id="1cc09-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="1cc09-348">V pořadí, ve kterém jsou vyřešeny, jsou uvedeny různé obory prostředků, včetně následujících:</span><span class="sxs-lookup"><span data-stu-id="1cc09-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="1cc09-349">Individuální ovládací prvek (pomocí <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> zděděné vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="1cc09-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="1cc09-350">A <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> a (také <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> pomocí zděděné vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="1cc09-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="1cc09-351">An <xref:System.Windows.Application> (pomocí <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="1cc09-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="1cc09-352">Rozmanitost oborů poskytuje flexibilitu s ohledem na způsob, jakým definujete a sdílíte své zdroje.</span><span class="sxs-lookup"><span data-stu-id="1cc09-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="1cc09-353">Jako alternativu k přímému sousto prostředků s určitým rozsahem můžete zabalit <xref:System.Windows.ResourceDictionary> jeden nebo více prostředků pomocí samostatného, na který lze odkazovat v jiných částech aplikace.</span><span class="sxs-lookup"><span data-stu-id="1cc09-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="1cc09-354">Například následující příklad definuje výchozí barvu pozadí ve slovníku prostředků:</span><span class="sxs-lookup"><span data-stu-id="1cc09-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="1cc09-355">Následující příklad odkazuje na slovník prostředků definovaný v předchozím příkladu tak, aby byl sdílen v rámci aplikace:</span><span class="sxs-lookup"><span data-stu-id="1cc09-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

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

<span data-ttu-id="1cc09-356">Zdroje a zdroje slovníky jsou základem WPF podporu pro témata a vzhledy.</span><span class="sxs-lookup"><span data-stu-id="1cc09-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="1cc09-357">Další informace naleznete v tématu [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="1cc09-358">Vlastní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="1cc09-358">Custom controls</span></span>

<span data-ttu-id="1cc09-359">Přestože WPF poskytuje celou řadu podpory přizpůsobení, může dojít k situacím, kdy existující ovládací prvky WPF nesplňují potřeby aplikace nebo jejích uživatelů.</span><span class="sxs-lookup"><span data-stu-id="1cc09-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="1cc09-360">K tomu může dojít, když:</span><span class="sxs-lookup"><span data-stu-id="1cc09-360">This can occur when:</span></span>

- <span data-ttu-id="1cc09-361">Uživatelské rozhraní, které požadujete nelze vytvořit přizpůsobením vzhledu existujících implementací WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="1cc09-362">Chování, které požadujete, není podporováno (nebo není snadno podporováno) existujícími implementacemi WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="1cc09-363">V tomto okamžiku však můžete využít jeden ze tří modelů WPF k vytvoření nového ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cc09-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="1cc09-364">Každý model cílí na konkrétní scénář a vyžaduje, aby váš vlastní ovládací prvek byl odvozen z určité základní třídy WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="1cc09-365">Zde jsou uvedeny tři modely:</span><span class="sxs-lookup"><span data-stu-id="1cc09-365">The three models are listed here:</span></span>

- <span data-ttu-id="1cc09-366">**Model uživatelského ovládacího prvku**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-366">**User Control Model**.</span></span> <span data-ttu-id="1cc09-367">Vlastní ovládací prvek <xref:System.Windows.Controls.UserControl> je odvozen z a skládá se z jednoho nebo více dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1cc09-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="1cc09-368">**Řídicí model**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-368">**Control Model**.</span></span> <span data-ttu-id="1cc09-369">Vlastní ovládací prvek <xref:System.Windows.Controls.Control> je odvozen a používá se k vytváření implementací, které oddělují jejich chování od jejich vzhledu pomocí šablon, podobně jako většina ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="1cc09-370">Odvození z <xref:System.Windows.Controls.Control> umožňuje větší svobodu při vytváření vlastního uživatelského rozhraní než uživatelské ovládací prvky, ale může vyžadovat větší úsilí.</span><span class="sxs-lookup"><span data-stu-id="1cc09-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="1cc09-371">**Model prvku rámce**.</span><span class="sxs-lookup"><span data-stu-id="1cc09-371">**Framework Element Model**.</span></span> <span data-ttu-id="1cc09-372">Vlastní ovládací prvek <xref:System.Windows.FrameworkElement> je odvozen od doby, kdy je jeho vzhled definován vlastní logikou vykreslování (nikoli šablon).</span><span class="sxs-lookup"><span data-stu-id="1cc09-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="1cc09-373">Následující příklad ukazuje vlastní číselný ovládací prvek <xref:System.Windows.Controls.UserControl>nahoru/dolů, který je odvozen z :</span><span class="sxs-lookup"><span data-stu-id="1cc09-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="1cc09-374">Následující příklad ilustruje XAML, který je nutný k <xref:System.Windows.Window>začlenění uživatelského ovládacího prvku do :</span><span class="sxs-lookup"><span data-stu-id="1cc09-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="1cc09-375">Následující obrázek `NumericUpDown` znázorňuje ovládací <xref:System.Windows.Window>prvek hostovaný v :</span><span class="sxs-lookup"><span data-stu-id="1cc09-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![Vlastní ovládací prvek UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="1cc09-377">Další informace o vlastních ovládacích prvcích naleznete [v tématu Přehled vytváření ovládacích prvků](controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1cc09-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="1cc09-378">WPF osvědčené postupy</span><span class="sxs-lookup"><span data-stu-id="1cc09-378">WPF best practices</span></span>

<span data-ttu-id="1cc09-379">Stejně jako u jakékoli vývojové platformy, WPF lze použít různými způsoby k dosažení požadovaného výsledku.</span><span class="sxs-lookup"><span data-stu-id="1cc09-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="1cc09-380">Jako způsob, jak zajistit, aby vaše wpf aplikace poskytují požadované uživatelské prostředí a splňují požadavky publika obecně, jsou doporučené osvědčené postupy pro usnadnění přístupu, globalizace a lokalizace a výkon.</span><span class="sxs-lookup"><span data-stu-id="1cc09-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="1cc09-381">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="1cc09-381">For more information, see:</span></span>

- [<span data-ttu-id="1cc09-382">Přístupnost</span><span class="sxs-lookup"><span data-stu-id="1cc09-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="1cc09-383">WPF globalizace a lokalizace</span><span class="sxs-lookup"><span data-stu-id="1cc09-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="1cc09-384">Výkon aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="1cc09-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="1cc09-385">Zabezpečení WPF</span><span class="sxs-lookup"><span data-stu-id="1cc09-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="1cc09-386">Další kroky</span><span class="sxs-lookup"><span data-stu-id="1cc09-386">Next steps</span></span>

<span data-ttu-id="1cc09-387">Podívali jsme se na klíčové rysy WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="1cc09-388">Nyní je čas vytvořit první aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="1cc09-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1cc09-389">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="1cc09-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="1cc09-390">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cc09-390">See also</span></span>

- [<span data-ttu-id="1cc09-391">Začínáme s WPF (Windows Presentation Foundation)</span><span class="sxs-lookup"><span data-stu-id="1cc09-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="1cc09-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="1cc09-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="1cc09-393">Komunitní zdroje WPF</span><span class="sxs-lookup"><span data-stu-id="1cc09-393">WPF community resources</span></span>](getting-started/community-feedback.md)
