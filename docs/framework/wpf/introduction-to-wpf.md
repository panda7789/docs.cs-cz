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
# <a name="wpf-overview"></a>Přehled grafického subsystému WPF (Windows Presentation Foundation)

Windows Presentation Foundation (WPF) umožňuje vytvářet desktopové klientské aplikace pro Windows s vizuálně ohromující uživatelské prostředí.

![Ukázka ui ve zdravotnictví společnosti Contoso](media/introduction-to-wpf/wpfintrofigure24.png)

Jádrem WPF je rozlišení nezávislé a vektorové vykreslovací engine, který je vytvořen tak, aby využít moderní grafický hardware. WPF rozšiřuje jádro o komplexní sadu funkcí pro vývoj aplikací, které zahrnují extensible Application Markup Language (XAML), ovládací prvky, datovou vazbu, rozložení, 2D a 3D grafiku, animaci, styly, šablony, dokumenty, média, text a Typografie. WPF je součástí rozhraní .NET, takže můžete vytvářet aplikace, které obsahují další prvky rozhraní .NET API.

Tento přehled je určen pro nováčky a pokrývá klíčové možnosti a koncepty WPF.

## <a name="program-with-wpf"></a>Program s WPF

WPF existuje jako podmnožina typů .NET, které jsou (z větší části) umístěné v oboru <xref:System.Windows> názvů. Pokud jste dříve vytvořili aplikace s rozhraním .NET pomocí spravovaných technologií, jako je ASP.NET a Windows Forms, základní wpf programovací prostředí by mělo být známé; můžete vytvořit instanci tříd, nastavit vlastnosti, metody volání a zpracování událostí pomocí oblíbeného programovacího jazyka .NET, například C# nebo Visual Basic.

WPF obsahuje další programovací konstrukce, které vylepšují vlastnosti a události: [vlastnosti závislostí](advanced/dependency-properties-overview.md) a [směrované události](advanced/routed-events-overview.md).

## <a name="markup-and-code-behind"></a>Značky a kód na pozadí

WPF umožňuje vyvíjet aplikaci pomocí *značek* a *kód na pozadí*, prostředí, s nimiž ASP.NET vývojáři by měli být obeznámeni. Obecně se používá XAML značky k implementaci vzhledu aplikace při použití spravovaných programovacích jazyků (kód na pozadí) k implementaci jeho chování. Toto oddělení vzhledu a chování má následující výhody:

- Náklady na vývoj a údržbu jsou sníženy, protože značky specifické pro vzhled nejsou úzce spojeny s kódem specifickým pro chování.

- Vývoj je efektivnější, protože návrháři mohou implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.

- [Globalizace a lokalizace](advanced/wpf-globalization-and-localization-overview.md) pro WPF aplikace je zjednodušena.

### <a name="markup"></a>Kód

XAML je značkovací jazyk založený na xml, který deklarativně implementuje vzhled aplikace. Obvykle se používá k vytvoření oken, dialogových oken, stránek a uživatelských ovládacích prvků a k jejich vyplnění ovládacími prvky, obrazci a grafikou.

Následující příklad používá XAML k implementaci vzhledu okna, které obsahuje jediné tlačítko:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

Konkrétně tento XAML definuje okno a tlačítko `Window` pomocí `Button` a prvky, v uvedeném pořadí. Každý prvek je konfigurován s atributy, `Title` jako je například atribut `Window` prvku k určení textu záhlaví okna. Za běhu WPF převede prvky a atributy, které jsou definovány v značkování na instance tříd WPF. Například `Window` prvek je převeden na instanci <xref:System.Windows.Window> třídy, <xref:System.Windows.Window.Title%2A> jejíž `Title` vlastnost je hodnota atributu.

Následující obrázek znázorňuje uživatelské rozhraní (UI), které je definováno XAML v předchozím příkladu:

![Okno, které obsahuje tlačítko](media/introduction-to-wpf/wpfintrofigure10.png)

Vzhledem k tomu, že XAML je založen na XML, uživatelské rozhraní, které s ním tvoříte, je sestaveno v hierarchii vnořených prvků známých jako [strom elementů](advanced/trees-in-wpf.md). Strom elementů poskytuje logický a intuitivní způsob vytváření a správy rozhraní.

### <a name="code-behind"></a>Kód na pozadí

Hlavním chováním aplikace je implementace funkcí, které reagují na interakce uživatele, včetně zpracování událostí (například klepnutí na nabídku, panel nástrojů nebo tlačítko) a volání obchodní logiky a logiky přístupu k datům v reakci. V WPF toto chování je implementováno v kódu, který je spojen se značkami. Tento typ kódu se označuje jako kód na pozadí. Následující příklad ukazuje aktualizované značky z předchozího příkladu a kód na pozadí:

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

V tomto příkladu kód na pozadí implementuje <xref:System.Windows.Window> třídu, která je odvozena z třídy. Atribut `x:Class` se používá k přidružení značky ke třídě s kódem na pozadí. `InitializeComponent`je volána z konstruktoru třídy s kódem za sloučit ui, který je definován v značkování s kódem na pozadí třídy. (`InitializeComponent` je generována pro vás, když je vytvořena aplikace, což je důvod, proč není nutné implementovat ručně.) Kombinace `x:Class` a `InitializeComponent` ujistěte se, že vaše implementace je správně inicializována při každém vytvoření. Třída s kódem na pozadí také implementuje <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události pro událost tlačítka. Po klepnutí na tlačítko se na obslužné rutině události zobrazí okno se zprávou voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metody.

Následující obrázek znázorňuje výsledek klepnutí na tlačítko:

![Okno se zprávou](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a>Ovládací prvky

Uživatelské prostředí, které jsou dodané modelaplikace jsou konstruovány ovládací prvky. V *WPF, ovládací prvek* je zastřešující termín, který se vztahuje na kategorii WPF třídy, které jsou hostovány v okně nebo na stránce, mají uživatelské rozhraní a implementovat některé chování.

Další informace naleznete v [tématu Controls](controls/index.md).

### <a name="wpf-controls-by-function"></a>WPF ovládací prvky podle funkce

Integrované ovládací prvky WPF jsou uvedeny zde:

- **Tlačítka** <xref:System.Windows.Controls.Button> : <xref:System.Windows.Controls.Primitives.RepeatButton>a .

- **Zobrazení**dat <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>: <xref:System.Windows.Controls.TreeView>, a .

- **Zobrazení a**výběr <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker>data : a .

- **Dialogová** <xref:Microsoft.Win32.OpenFileDialog>okna <xref:System.Windows.Controls.PrintDialog>: <xref:Microsoft.Win32.SaveFileDialog>, , a .

- **Digitální inkoust** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>a .

- **Dokumenty** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, , a .

- **Vstup** <xref:System.Windows.Controls.TextBox>: <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>a .

- **Rozložení** <xref:System.Windows.Controls.Border>: <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, <xref:System.Windows.Controls.WrapPanel>, , , , , , , , , a .

- **Média** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>, a .

- **Menu**: <xref:System.Windows.Controls.ContextMenu> <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, a .

- **Navigace** <xref:System.Windows.Controls.Frame>: <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, a .

- **Výběr** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, a .

- **Informace o uživateli** <xref:System.Windows.Controls.AccessText>: <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar> <xref:System.Windows.Controls.Primitives.StatusBar>, , a .

## <a name="input-and-commands"></a>Vstup a příkazy

Ovládací prvky nejčastěji detekují vstup uživatele a reagují na něj. [Vstupní systém WPF](advanced/input-overview.md) používá přímé i směrované události pro podporu zadávání textu, správy fokusu a umístění myši.

Aplikace mají často složité vstupní požadavky. WPF poskytuje [příkazový systém,](advanced/commanding-overview.md) který odděluje akce vstupu uživatele od kódu, který reaguje na tyto akce.

## <a name="layout"></a>Rozložení

Při vytváření uživatelského rozhraní uspořádáte ovládací prvky podle umístění a velikosti tak, aby vytvářela rozložení. Klíčovým požadavkem každého rozvržení je přizpůsobit se změnám velikosti okna a nastavení zobrazení. Spíše než nutit psát kód přizpůsobit rozložení za těchto okolností, WPF poskytuje prvotřídní, rozšiřitelné rozložení systému pro vás.

Základním kamenem systému rozvržení je relativní umístění, což zvyšuje schopnost přizpůsobit se měnícím se podmínkám okna a zobrazení. Kromě toho systém rozložení spravuje vyjednávání mezi ovládacími prvky k určení rozložení. Vyjednávání je dvoustupňový proces: nejprve ovládací prvek sdělí nadřazenému objektu, jaké umístění a velikost vyžaduje; za druhé, nadřazený řekne ovládacímu prvku, jaký prostor může mít.

Systém rozložení je vystaven podřízeným ovládacím prvkům prostřednictvím základních tříd WPF. Pro běžná rozložení, jako jsou mřížky, stohování a ukotvení, wpf obsahuje několik ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas>: Podřízené ovládací prvky poskytují vlastní rozložení.

- <xref:System.Windows.Controls.DockPanel>: Podřízené ovládací prvky jsou zarovnány k okrajům panelu.

- <xref:System.Windows.Controls.Grid>: Podřízené ovládací prvky jsou umístěny podle řádků a sloupců.

- <xref:System.Windows.Controls.StackPanel>: Podřízené ovládací prvky jsou skládané svisle nebo vodorovně.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Podřízené ovládací prvky jsou virtualizovány a uspořádány na jednom řádku, který je vodorovně nebo vertikálně orientovaný.

- <xref:System.Windows.Controls.WrapPanel>: Podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zalomené na další řádek, pokud je na aktuálním řádku více ovládacích prvků, než umožňuje prostor.

Následující příklad používá <xref:System.Windows.Controls.DockPanel> rozložení několika <xref:System.Windows.Controls.TextBox> ovládacích prvků:

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

Umožňuje <xref:System.Windows.Controls.DockPanel> podřízené <xref:System.Windows.Controls.TextBox> ovládací prvky, aby mu řekli, jak je uspořádat. Chcete-li to <xref:System.Windows.Controls.DockPanel> provést, `Dock` implementuje připojené vlastnosti, která je vystavena podřízené ovládací prvky, aby každý z nich určit styl doku.

> [!NOTE]
> Vlastnost, která je implementována nadřazeným ovládacím prvkem pro použití podřízenými ovládacími prvky, je konstrukce WPF nazývaná [připojená vlastnost](advanced/attached-properties-overview.md).

Následující obrázek znázorňuje výsledek značky XAML v předchozím příkladu:

![Stránka DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a>Datová vazba

Většina aplikací je vytvořena tak, aby uživatelům poskytovala prostředky k zobrazení a úpravám dat. Pro aplikace WPF je práce ukládání a přístupu k datům již zajištěna technologiemi, jako je SQL Server a ADO .NET. Po přístupu k datům a načtení do spravovaných objektů aplikace začíná tvrdá práce pro aplikace WPF. V podstatě se jedná o dvě věci:

1. Kopírování dat ze spravovaných objektů do ovládacích prvků, kde lze data zobrazit a upravit.

2. Zajištění, že změny provedené v datech pomocí ovládacích prvků jsou zkopírovány zpět do spravovaných objektů.

Pro zjednodušení vývoje aplikací WPF poskytuje modul datové vazby automaticky provádět tyto kroky. Základní jednotkou modulu datové <xref:System.Windows.Data.Binding> vazby je třída, jejíž úlohou je svázat ovládací prvek (cíl vazby) s datovým objektem (zdrojem vazby). Tento vztah je znázorněn na následujícím obrázku:

![Základní diagram datové vazby](media/introduction-to-wpf/databindingmostbasic.png)

Následující příklad ukazuje, jak <xref:System.Windows.Controls.TextBox> vázat a na `Person` instanci vlastního objektu. Implementace `Person` je uvedena v následujícím kódu:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

Následující značky svážou <xref:System.Windows.Controls.TextBox> instanci `Person` vlastního objektu:

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

V tomto příkladu `Person` je instance třídy v kódu na pozadí a `DataBindingWindow`je nastaven jako kontext dat pro . Ve značkách <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> je vlastnost vlastnosti `Person.Name` vázána na`{Binding ... }`vlastnost (pomocí syntaxe " XAML). Tento XAML říká WPF <xref:System.Windows.Controls.TextBox> svázat `Person` ovládací prvek k <xref:System.Windows.FrameworkElement.DataContext%2A> objektu, který je uložen ve vlastnosti okna.

WPF datový vázací modul poskytuje další podporu, která zahrnuje ověřování, řazení, filtrování a seskupování. Kromě toho datová vazba podporuje použití datových šablon k vytvoření vlastního uživatelského rozhraní pro vázaná data, pokud uživatelské rozhraní zobrazené standardními ovládacími prvky WPF není vhodné.

Další informace naleznete v [tématu Přehled datových vazeb](../../desktop-wpf/data/data-binding-overview.md).

## <a name="graphics"></a>Grafika

WPF představuje rozsáhlou, škálovatelnou a flexibilní sadu grafických funkcí, které mají následující výhody:

- **Grafika nezávislá na rozlišení a na zařízení**. Základní jednotkou měření v grafickém systému WPF je pixel nezávislý na zařízení, který je 1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávislé na rozlišení a nezávislé na zařízení. Každý pixel nezávislý na zařízení se automaticky změní tak, aby odpovídal nastavení bodů na palec (dpi) systému, ve kterých se vykresluje.

- **Vylepšená přesnost**. Souřadnicový systém WPF se měří s dvojitou přesností s plovoucí desetinnou desetinnou tácek spíše než s jednou přesností. Transformace a hodnoty krytí jsou také vyjádřeny jako dvojitá přesnost. WPF také podporuje široký barevný gamut (scRGB) a poskytuje integrovanou podporu pro správu vstupů z různých barevných prostorů.

- **Pokročilá podpora grafiky a animace**. WPF zjednodušuje programování grafiky správou animačních scén za vás; není třeba se obávat zpracování scény, vykreslování smyček a bilineární interpolace. Kromě toho WPF poskytuje podporu testování přístupů a plnou podporu alfa skládání.

- **Hardwarová akcelerace**. Grafický systém WPF využívá grafický hardware k minimalizaci využití procesoru.

### <a name="2d-shapes"></a>2D obrazce

WPF poskytuje knihovnu běžných vektorem nakreslených 2D tvarů, jako jsou obdélníky a elipsy, které jsou znázorněny na následujícím obrázku:

![Elipsy a obdélníky](media/introduction-to-wpf/wpfintrofigure4.PNG)

Zajímavou schopností tvarů je, že nejsou jen pro zobrazení; obrazce implementovat mnoho funkcí, které očekáváte od ovládacích prvků, včetně klávesnice a myši vstupu. Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> událost <xref:System.Windows.Shapes.Ellipse> zpracování:

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

Následující obrázek znázorňuje, co je vyrobeno podle předchozího kódu:

![Okno s textem "klikli jste na&#33; elipsy"](media/introduction-to-wpf/wpfintrofigure12.png)

Další informace naleznete [v tématu Obrazce a základní výkres v přehledu WPF](../../desktop-wpf/data/data-binding-overview.md).

### <a name="2d-geometries"></a>2D geometrie

2D tvary poskytované wpf pokrývají standardní sadu základních tvarů. Může však být nutné vytvořit vlastní obrazce, které usnadní návrh přizpůsobeného uživatelského rozhraní. Pro tento účel WPF poskytuje geometrie. Následující obrázek znázorňuje použití geometrií k vytvoření vlastního tvaru, který lze nakreslit přímo, použít jako stopu nebo použít k oříznutí jiných tvarů a ovládacích prvků.

<xref:System.Windows.Shapes.Path>objekty lze použít k kreslení uzavřených nebo otevřených tvarů, více tvarů a dokonce i zakřivených tvarů.

<xref:System.Windows.Media.Geometry>objekty lze použít pro oříznutí, testování přístupů a vykreslování 2D grafických dat.

![Různá použití cesty](media/introduction-to-wpf/wpfintrofigure5.png)

Další informace naleznete v [tématu Přehled geometrie](graphics-multimedia/geometry-overview.md).

### <a name="2d-effects"></a>2D efekty

Podmnožina 2D funkcí WPF zahrnuje vizuální efekty, jako jsou přechody, bitmapy, kresby, malování videa, otočení, změna měřítka a zkosení. To vše je dosaženo kartáči; následující obrázek ukazuje některé příklady:

![Ilustrace různých štětců](media/introduction-to-wpf/wpfintrofigure6.png)

Další informace naleznete v tématu [Přehled stop y WPF](graphics-multimedia/wpf-brushes-overview.md).

### <a name="3d-rendering"></a>3D vykreslování

WPF také obsahuje funkce 3D vykreslování, které se integrují s 2D grafikou, aby bylo možné vytvářet zajímavější a zajímavější uživatelská rozhraní. Například následující obrázek znázorňuje 2D obrazy vykreslené na 3D tvarech:

![Ukázkový snímek obrazovky Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

Další informace naleznete v tématu [Přehled 3D grafiky](graphics-multimedia/3-d-graphics-overview.md).

## <a name="animation"></a>Animace

Podpora animací WPF umožňuje vytvářet ovládací prvky růst, třást, točit a slábnout, vytvářet zajímavé přechody stránek a další. Můžete animovat většinu tříd WPF, dokonce i vlastní třídy. Následující obrázek znázorňuje jednoduchou animaci v akci:

![Obrázky animované krychle](media/introduction-to-wpf/wpfintrofigure7.png)

Další informace naleznete v [tématu Přehled animace](graphics-multimedia/animation-overview.md).

## <a name="media"></a>Média

Jedním ze způsobů, jak zprostředkovat bohatý obsah, je použití audiovizuálních médií. WPF poskytuje speciální podporu pro obrázky, video a zvuk.

### <a name="images"></a>Image

Obrázky jsou společné pro většinu aplikací a WPF poskytuje několik způsobů, jak je používat. Následující obrázek znázorňuje uživatelské rozhraní se seznamem, který obsahuje miniatury obrázků. Když je vybraná miniatura, zobrazí se obrázek v plné velikosti.

![Miniatury obrázků a obrázek v plné&#45;velikosti](media/introduction-to-wpf/wpfintrofigure8.png)

Další informace naleznete v tématu [Přehled zobrazování .](graphics-multimedia/imaging-overview.md)

### <a name="video-and-audio"></a>Video a zvuk

Ovládací <xref:System.Windows.Controls.MediaElement> prvek je schopen přehrávat video i zvuk a je dostatečně flexibilní, aby byl základem pro vlastní přehrávač médií. Následující značky XAML implementují přehrávač médií:

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

Okno na následujícím obrázku <xref:System.Windows.Controls.MediaElement> znázorňuje ovládací prvek v akci:

![Ovládací prvek MediaElement se zvukem a videem](media/introduction-to-wpf/wpfintrofigure1.png)

Další informace naleznete v [tématu Grafika a multimédia](graphics-multimedia/index.md).

## <a name="text-and-typography"></a>Text a typografii

Pro usnadnění vykreslování textu ve vysoké kvalitě nabízí WPF následující funkce:

- Podpora písma OpenType.

- Vylepšení cleartype.

- Vysoký výkon, který využívá hardwarovou akceleraci.

- Integrace textu s médii, grafikou a animací.

- Mezinárodní podpora písem a záložní mechanismy.

Jako ukázku integrace textu s grafikou, následující obrázek ukazuje použití textových dekorací:

![Text s různými textovými dekoracemi](media/introduction-to-wpf/wpfintrofigure23.png)

Další informace naleznete [v tématu Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).

## <a name="customize-wpf-apps"></a>Přizpůsobení aplikací WPF

Až do tohoto okamžiku jste viděli základní stavební bloky WPF pro vývoj aplikací. Model aplikace se používá k hostování a doručování obsahu aplikace, který se skládá hlavně z ovládacích prvků. Chcete-li zjednodušit uspořádání ovládacích prvků v uživatelském rozhraní a zajistit, aby bylo uspořádání zachováno tváří v tvář změnám velikosti okna a nastavení zobrazení, použijte systém rozložení WPF. Vzhledem k tomu, že většina aplikací umožňuje uživatelům pracovat s daty, můžete pomocí datové vazby omezit práci integrace uživatelského rozhraní s daty. Chcete-li zlepšit vizuální vzhled aplikace, použijte komplexní rozsah grafiky, animace a podporu médií poskytované WPF.

Často však základy nestačí pro vytvoření a správu skutečně odlišného a vizuálně ohromujícího uživatelského zážitku. Standardní ovládací prvky WPF nemusí integrovat s požadovaný vzhled aplikace. Data nemusí být zobrazena nejefektivnějším způsobem. Celkové uživatelské prostředí aplikace nemusí být vhodné pro výchozí vzhled motivů systému Windows. V mnoha ohledech, prezentační technologie potřebuje vizuální rozšiřitelnost, stejně jako jakýkoli jiný typ rozšiřitelnosti.

Z tohoto důvodu WPF poskytuje řadu mechanismů pro vytváření jedinečných uživatelských prostředí, včetně bohatého modelu obsahu pro ovládací prvky, aktivační události, šablony ovládacích prvků a dat, styly, prostředky uživatelského rozhraní a motivy a vzhledy.

### <a name="content-model"></a>Model obsahu

Hlavním účelem většiny ovládacích prvků WPF je zobrazení obsahu. V WPF typ a počet položek, které mohou představovat obsah ovládacího prvku se označuje jako *model obsahu*ovládacího prvku . Některé ovládací prvky mohou obsahovat jednu položku a typ obsahu. například obsah a <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která <xref:System.Windows.Controls.TextBox.Text%2A> je přiřazena vlastnosti. Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>:

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Následující obrázek znázorňuje výsledek:

![Ovládací prvek TextBox, který obsahuje text](media/introduction-to-wpf/wpfintrofigure21.png)

Jiné ovládací prvky však mohou obsahovat více položek různých typů obsahu. obsah <xref:System.Windows.Controls.Button>vlastnosti <xref:System.Windows.Controls.ContentControl.Content%2A> , může obsahovat různé položky včetně ovládacích prvků rozložení, textu, obrázků a obrazců. Následující příklad ukazuje <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.DockPanel>obsah, který obsahuje <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a <xref:System.Windows.Controls.MediaElement>, a a :

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

Na následujícím obrázku je znázorněn obsah tohoto tlačítka:

![Tlačítko, které obsahuje více typů obsahu](media/introduction-to-wpf/wpfintrofigure22.png)

Další informace o typech obsahu, který je podporován různými ovládacími prvky, naleznete v [tématu WPF model obsahu](controls/wpf-content-model.md).

### <a name="triggers"></a>Aktivační události

Přestože hlavním účelem značky XAML je implementovat vzhled aplikace, můžete také použít XAML k implementaci některých aspektů chování aplikace. Jedním z příkladů je použití aktivačních událostí ke změně vzhledu aplikace na základě interakcí s uživatelem. Další informace naleznete v [tématu Styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).

### <a name="control-templates"></a>Řídicí šablony

Výchozí uživatelská rozhraní pro ovládací prvky WPF jsou obvykle konstruovány z jiných ovládacích prvků a obrazců. Například a <xref:System.Windows.Controls.Button> se skládá <xref:Microsoft.Windows.Themes.ButtonChrome> <xref:System.Windows.Controls.ContentPresenter> z obou a ovládacích prvků. Poskytuje <xref:Microsoft.Windows.Themes.ButtonChrome> standardní vzhled tlačítka, <xref:System.Windows.Controls.ContentPresenter> zatímco zobrazuje obsah tlačítka, jak <xref:System.Windows.Controls.ContentControl.Content%2A> je určeno vlastností.

Někdy může být výchozí vzhled ovládacího prvku neslučitelný s celkovým vzhledem aplikace. V takovém případě můžete <xref:System.Windows.Controls.ControlTemplate> změnit vzhled uživatelského rozhraní ovládacího prvku bez změny jeho obsahu a chování.

Následující příklad ukazuje, jak změnit <xref:System.Windows.Controls.Button> vzhled a <xref:System.Windows.Controls.ControlTemplate>pomocí :

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

V tomto příkladu bylo výchozí uživatelské rozhraní <xref:System.Windows.Shapes.Ellipse> tlačítka nahrazeno rozhraním, které <xref:System.Windows.Media.RadialGradientBrush>má tmavě modré ohraničení a je vyplněno pomocí rozhraní . Ovládací <xref:System.Windows.Controls.ContentPresenter> prvek zobrazí obsah <xref:System.Windows.Controls.Button>, "Klikněte na mě!" Po <xref:System.Windows.Controls.Button> klepnutí na <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost je stále aktivována <xref:System.Windows.Controls.Button> jako součást výchozí chování ovládacího prvku. Výsledek je zobrazen na následujícím obrázku:

![Eliptické tlačítko a druhé okno](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a>Šablony dat

Zatímco šablona ovládacího prvku umožňuje určit vzhled ovládacího prvku, šablona dat umožňuje určit vzhled obsahu ovládacího prvku. Šablony dat se často používají k vylepšení způsobu zobrazení vázaných dat. Následující obrázek znázorňuje <xref:System.Windows.Controls.ListBox> výchozí vzhled pro objekt, který je vázán na `Task` kolekci objektů, kde každý úkol má název, popis a prioritu:

![Seznam s výchozím vzhledem](media/introduction-to-wpf/wpfintrofigure18.png)

Výchozí vzhled je to, co <xref:System.Windows.Controls.ListBox>byste očekávali od . Výchozí vzhled každé úlohy však obsahuje pouze název úkolu. Chcete-li zobrazit název, popis a prioritu <xref:System.Windows.Controls.ListBox> <xref:System.Windows.DataTemplate>úkolu, musí být výchozí vzhled vázaných položek seznamu ovládacího prvku změněn pomocí . Následující XAML definuje takový <xref:System.Windows.DataTemplate>, který se použije pro <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> každý úkol pomocí atributu:

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

Následující obrázek znázorňuje účinek tohoto kódu:

![Seznam, který používá šablonu dat](media/introduction-to-wpf/wpfintrofigure19.png)

Všimněte <xref:System.Windows.Controls.ListBox> si, že si zachovala své chování a celkový vzhled; pouze vzhled obsahu zobrazeného v seznamu se změnil.

Další informace naleznete [v tématu Přehled templating dat](data/data-templating-overview.md).

### <a name="styles"></a>Styly

Styly umožňují vývojářům a návrhářům standardizovat konkrétní vzhled svého produktu. WPF poskytuje silný styl modelu, základem, který je <xref:System.Windows.Style> prvek. Následující příklad vytvoří styl, který nastaví <xref:System.Windows.Controls.Button> barvu pozadí `Orange`pro každé okno na :

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

Protože tento styl <xref:System.Windows.Controls.Button> cílí na všechny ovládací prvky, styl se automaticky použije na všechna tlačítka v okně, jak je znázorněno na následujícím obrázku:

![Dvě oranžová tlačítka](media/introduction-to-wpf/wpfintrofigure20.png)

Další informace naleznete v [tématu Styly a šablony](../../desktop-wpf/fundamentals/styles-templates-overview.md).

### <a name="resources"></a>Zdroje informací

Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může zahrnovat cokoli od písem a barev pozadí až po šablony ovládacích prvků, šablony dat a styly. Podporu WPF pro prostředky uživatelského rozhraní můžete použít k zapouzdření těchto prostředků do jednoho umístění pro opakované použití.

Následující příklad definuje společnou barvu pozadí, která <xref:System.Windows.Controls.Button> je <xref:System.Windows.Controls.Label>sdílena a a :

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

Tento příklad implementuje prostředek barvy `Window.Resources` pozadí pomocí elementu vlastnosti. Tento zdroj je k dispozici <xref:System.Windows.Window>pro všechny podřízené položky rozhraní . V pořadí, ve kterém jsou vyřešeny, jsou uvedeny různé obory prostředků, včetně následujících:

1. Individuální ovládací prvek (pomocí <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> zděděné vlastnosti).

2. A <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> a (také <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> pomocí zděděné vlastnosti).

3. An <xref:System.Windows.Application> (pomocí <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> vlastnosti).

Rozmanitost oborů poskytuje flexibilitu s ohledem na způsob, jakým definujete a sdílíte své zdroje.

Jako alternativu k přímému sousto prostředků s určitým rozsahem můžete zabalit <xref:System.Windows.ResourceDictionary> jeden nebo více prostředků pomocí samostatného, na který lze odkazovat v jiných částech aplikace. Například následující příklad definuje výchozí barvu pozadí ve slovníku prostředků:

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Následující příklad odkazuje na slovník prostředků definovaný v předchozím příkladu tak, aby byl sdílen v rámci aplikace:

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

Zdroje a zdroje slovníky jsou základem WPF podporu pro témata a vzhledy.

Další informace naleznete v tématu [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).

### <a name="custom-controls"></a>Vlastní ovládací prvky

Přestože WPF poskytuje celou řadu podpory přizpůsobení, může dojít k situacím, kdy existující ovládací prvky WPF nesplňují potřeby aplikace nebo jejích uživatelů. K tomu může dojít, když:

- Uživatelské rozhraní, které požadujete nelze vytvořit přizpůsobením vzhledu existujících implementací WPF.

- Chování, které požadujete, není podporováno (nebo není snadno podporováno) existujícími implementacemi WPF.

V tomto okamžiku však můžete využít jeden ze tří modelů WPF k vytvoření nového ovládacího prvku. Každý model cílí na konkrétní scénář a vyžaduje, aby váš vlastní ovládací prvek byl odvozen z určité základní třídy WPF. Zde jsou uvedeny tři modely:

- **Model uživatelského ovládacího prvku**. Vlastní ovládací prvek <xref:System.Windows.Controls.UserControl> je odvozen z a skládá se z jednoho nebo více dalších ovládacích prvků.

- **Řídicí model**. Vlastní ovládací prvek <xref:System.Windows.Controls.Control> je odvozen a používá se k vytváření implementací, které oddělují jejich chování od jejich vzhledu pomocí šablon, podobně jako většina ovládacích prvků WPF. Odvození z <xref:System.Windows.Controls.Control> umožňuje větší svobodu při vytváření vlastního uživatelského rozhraní než uživatelské ovládací prvky, ale může vyžadovat větší úsilí.

- **Model prvku rámce**. Vlastní ovládací prvek <xref:System.Windows.FrameworkElement> je odvozen od doby, kdy je jeho vzhled definován vlastní logikou vykreslování (nikoli šablon).

Následující příklad ukazuje vlastní číselný ovládací prvek <xref:System.Windows.Controls.UserControl>nahoru/dolů, který je odvozen z :

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

Následující příklad ilustruje XAML, který je nutný k <xref:System.Windows.Window>začlenění uživatelského ovládacího prvku do :

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

Následující obrázek `NumericUpDown` znázorňuje ovládací <xref:System.Windows.Window>prvek hostovaný v :

![Vlastní ovládací prvek UserControl](media/introduction-to-wpf/wpfintrofigure3.png)

Další informace o vlastních ovládacích prvcích naleznete [v tématu Přehled vytváření ovládacích prvků](controls/control-authoring-overview.md).

## <a name="wpf-best-practices"></a>WPF osvědčené postupy

Stejně jako u jakékoli vývojové platformy, WPF lze použít různými způsoby k dosažení požadovaného výsledku. Jako způsob, jak zajistit, aby vaše wpf aplikace poskytují požadované uživatelské prostředí a splňují požadavky publika obecně, jsou doporučené osvědčené postupy pro usnadnění přístupu, globalizace a lokalizace a výkon. Další informace naleznete v tématu:

- [Přístupnost](../ui-automation/accessibility-best-practices.md)
- [WPF globalizace a lokalizace](advanced/wpf-globalization-and-localization-overview.md)
- [Výkon aplikace WPF](advanced/optimizing-wpf-application-performance.md)
- [Zabezpečení WPF](security-wpf.md)

## <a name="next-steps"></a>Další kroky

Podívali jsme se na klíčové rysy WPF. Nyní je čas vytvořit první aplikaci WPF.

> [!div class="nextstepaction"]
> [Návod: Moje první desktopová aplikace WPF](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a>Viz také

- [Začínáme s WPF (Windows Presentation Foundation)](getting-started/index.md)
- [Windows Presentation Foundation](index.md)
- [Komunitní zdroje WPF](getting-started/community-feedback.md)
