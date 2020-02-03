---
title: Roztažení skleněného rámečku do aplikace WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
ms.openlocfilehash: b78547aa8b414c585bb2e5c9c6680ed159731bc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746529"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a><span data-ttu-id="42451-102">Rozšíření skleněného rámečku do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="42451-102">Extend Glass Frame Into a WPF Application</span></span>

<span data-ttu-id="42451-103">Toto téma ukazuje, jak roztáhnout skleněný rámec Windows Vista do klientské oblasti aplikace Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="42451-103">This topic demonstrates how to extend the Windows Vista glass frame into the client area of a Windows Presentation Foundation (WPF) application.</span></span>

> [!NOTE]
> <span data-ttu-id="42451-104">Tento příklad bude fungovat pouze v počítači se systémem Windows Vista, na kterém je spuštěná aplikace Správce oken plochy (DWM) se zapnutým skleněným systémem.</span><span class="sxs-lookup"><span data-stu-id="42451-104">This example will only work on a Windows Vista machine running the Desktop Window Manager (DWM) with glass enabled.</span></span> <span data-ttu-id="42451-105">Edice Home Basic v systému Windows Vista nepodporuje transparentní skleněný efekt.</span><span class="sxs-lookup"><span data-stu-id="42451-105">Windows Vista Home Basic edition does not support the transparent glass effect.</span></span> <span data-ttu-id="42451-106">Oblasti, které by se obvykle vygenerovaly s průhledným skleněným efektem v jiných edicích Windows Vista, se vykreslují neprůhledně.</span><span class="sxs-lookup"><span data-stu-id="42451-106">Areas that would typically render with the transparent glass effect on other editions of Windows Vista are rendered opaque.</span></span>

## <a name="example"></a><span data-ttu-id="42451-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="42451-107">Example</span></span>

<span data-ttu-id="42451-108">Následující obrázek znázorňuje skleněný rámec rozšířený na adresní řádek aplikace Internet Explorer 7:</span><span class="sxs-lookup"><span data-stu-id="42451-108">The following image illustrates the glass frame extended into the address bar of Internet Explorer 7:</span></span>

![Snímek obrazovky znázorňující skleněný rámec rozšířený na adresní řádek IE7](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

<span data-ttu-id="42451-110">Chcete-li zvětšit skleněný rámec v aplikaci WPF, je vyžadován přístup k nespravovanému rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="42451-110">To extend the glass frame on a WPF application, access to unmanaged API is needed.</span></span> <span data-ttu-id="42451-111">Následující příklad kódu provádí vyvolání platformy (PInvoke) pro rozhraní API, které je potřeba k rozšiřování rámce do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="42451-111">The following code example does a Platform Invoke (pinvoke) for the two API needed to extend the frame into the client area.</span></span> <span data-ttu-id="42451-112">Každé z těchto rozhraní API je deklarováno ve třídě s názvem **NonClientRegionAPI**.</span><span class="sxs-lookup"><span data-stu-id="42451-112">Each of these API are declared in a class called **NonClientRegionAPI**.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public struct MARGINS
{
    public int cxLeftWidth;      // width of left border that retains its size
    public int cxRightWidth;     // width of right border that retains its size
    public int cyTopHeight;      // height of top border that retains its size
    public int cyBottomHeight;   // height of bottom border that retains its size
};

[DllImport("DwmApi.dll")]
public static extern int DwmExtendFrameIntoClientArea(
    IntPtr hwnd,
    ref MARGINS pMarInset);
```

```vb
<StructLayout(LayoutKind.Sequential)>
Public Structure MARGINS
    Public cxLeftWidth As Integer ' width of left border that retains its size
    Public cxRightWidth As Integer ' width of right border that retains its size
    Public cyTopHeight As Integer ' height of top border that retains its size
    Public cyBottomHeight As Integer ' height of bottom border that retains its size
End Structure

<DllImport("DwmApi.dll")>
Public Shared Function DwmExtendFrameIntoClientArea(ByVal hwnd As IntPtr, ByRef pMarInset As MARGINS) As Integer
End Function
```

<span data-ttu-id="42451-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) je funkce DWM, která rozšiřuje rámec do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="42451-113">[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) is the DWM function that extends the frame into the client area.</span></span> <span data-ttu-id="42451-114">Používá dva parametry; popisovač okna a struktura [okrajů](/windows/win32/api/uxtheme/ns-uxtheme-margins) .</span><span class="sxs-lookup"><span data-stu-id="42451-114">It takes two parameters; a window handle and a [MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) structure.</span></span> <span data-ttu-id="42451-115">Pomocí [okrajů](/windows/win32/api/uxtheme/ns-uxtheme-margins) správce oken informujte, kolik dalšího snímku by se mělo rozšířit do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="42451-115">[MARGINS](/windows/win32/api/uxtheme/ns-uxtheme-margins) is used to tell the DWM how much extra the frame should be extended into the client area.</span></span>

## <a name="example"></a><span data-ttu-id="42451-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="42451-116">Example</span></span>

<span data-ttu-id="42451-117">Chcete-li použít funkci [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) , je nutné získat popisovač okna.</span><span class="sxs-lookup"><span data-stu-id="42451-117">To use the [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) function, a window handle must be obtained.</span></span> <span data-ttu-id="42451-118">V rámci WPF lze popisovač okna získat z vlastnosti <xref:System.Windows.Interop.HwndSource.Handle%2A> <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="42451-118">In WPF, the window handle can be obtained from the <xref:System.Windows.Interop.HwndSource.Handle%2A> property of an <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="42451-119">V následujícím příkladu je rámec rozšířen do oblasti klienta na události <xref:System.Windows.FrameworkElement.Loaded> okna.</span><span class="sxs-lookup"><span data-stu-id="42451-119">In the following example, the frame is extended into the client area on the <xref:System.Windows.FrameworkElement.Loaded> event of the window.</span></span>

```csharp
void OnLoaded(object sender, RoutedEventArgs e)
{
   try
   {
      // Obtain the window handle for WPF application
      IntPtr mainWindowPtr = new WindowInteropHelper(this).Handle;
      HwndSource mainWindowSrc = HwndSource.FromHwnd(mainWindowPtr);
      mainWindowSrc.CompositionTarget.BackgroundColor = Color.FromArgb(0, 0, 0, 0);

      // Get System Dpi
      System.Drawing.Graphics desktop = System.Drawing.Graphics.FromHwnd(mainWindowPtr);
      float DesktopDpiX = desktop.DpiX;
      float DesktopDpiY = desktop.DpiY;

      // Set Margins
      NonClientRegionAPI.MARGINS margins = new NonClientRegionAPI.MARGINS();

      // Extend glass frame into client area
      // Note that the default desktop Dpi is 96dpi. The  margins are
      // adjusted for the system Dpi.
      margins.cxLeftWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cxRightWidth = Convert.ToInt32(5 * (DesktopDpiX / 96));
      margins.cyTopHeight = Convert.ToInt32(((int)topBar.ActualHeight + 5) * (DesktopDpiX / 96));
      margins.cyBottomHeight = Convert.ToInt32(5 * (DesktopDpiX / 96));

      int hr = NonClientRegionAPI.DwmExtendFrameIntoClientArea(mainWindowSrc.Handle, ref margins);
      //
      if (hr < 0)
      {
         //DwmExtendFrameIntoClientArea Failed
      }
   }
   // If not Vista, paint background white.
   catch (DllNotFoundException)
   {
      Application.Current.MainWindow.Background = Brushes.White;
   }
}
```

## <a name="example"></a><span data-ttu-id="42451-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="42451-120">Example</span></span>

<span data-ttu-id="42451-121">Následující příklad ukazuje jednoduché okno, ve kterém je rámec rozšířen do klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="42451-121">The following example shows a simple window in which the frame is extended into the client area.</span></span> <span data-ttu-id="42451-122">Rámec je rozšířen za horní ohraničení, které obsahuje dva objekty <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="42451-122">The frame is extended behind the top border that contains the two <xref:System.Windows.Controls.TextBox> objects.</span></span>

```xaml
<Window x:Class="SDKSample.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Extended Glass in WPF" Height="300" Width="400"
    Loaded="OnLoaded" Background="Transparent"
    >
  <Grid ShowGridLines="True">
    <DockPanel Name="mainDock">
      <!-- The border is used to compute the rendered height with margins.
           topBar contents will be displayed on the extended glass frame.-->
      <Border Name="topBar" DockPanel.Dock="Top" >
        <Grid Name="grid">
          <Grid.ColumnDefinitions>
            <ColumnDefinition MinWidth="100" Width="*"/>
            <ColumnDefinition Width="Auto"/>
          </Grid.ColumnDefinitions>
          <TextBox Grid.Column="0" MinWidth="100" Margin="0,0,10,5">Path</TextBox>
          <TextBox Grid.Column="1" MinWidth="75" Margin="0,0,0,5">Search</TextBox>
        </Grid>
      </Border>
      <Grid DockPanel.Dock="Top" >
        <Grid.ColumnDefinitions>
          <ColumnDefinition/>
        </Grid.ColumnDefinitions>
        <TextBox Grid.Column="0" AcceptsReturn="True"/>
      </Grid>
    </DockPanel>
  </Grid>
</Window>
```

<span data-ttu-id="42451-123">Následující obrázek znázorňuje skleněný rámec rozšířený do aplikace WPF:</span><span class="sxs-lookup"><span data-stu-id="42451-123">The following image illustrates the glass frame extended into a WPF application:</span></span>

![Snímek obrazovky znázorňující skleněný rámec rozšířený do aplikace WPF](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a><span data-ttu-id="42451-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="42451-125">See also</span></span>

- [<span data-ttu-id="42451-126">Přehled Správce oken plochy</span><span class="sxs-lookup"><span data-stu-id="42451-126">Desktop Window Manager Overview</span></span>](/windows/desktop/dwm/dwm-overview)
- [<span data-ttu-id="42451-127">Přehled rozostření Správce oken plochy</span><span class="sxs-lookup"><span data-stu-id="42451-127">Desktop Window Manager Blur Overview</span></span>](/windows/desktop/dwm/blur-ovw)
- [<span data-ttu-id="42451-128">DwmExtendFrameIntoClientArea</span><span class="sxs-lookup"><span data-stu-id="42451-128">DwmExtendFrameIntoClientArea</span></span>](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
