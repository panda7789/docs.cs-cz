---
title: Rozšíření skleněného rámečku do aplikace WPF
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
ms.openlocfilehash: ae4d7f23729f5bd39558902a58d33c6c45572d85
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977011"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Rozšíření skleněného rámečku do aplikace WPF

Toto téma ukazuje, jak roztáhnout skleněný rámec Windows Vista do klientské oblasti aplikace Windows Presentation Foundation (WPF).

> [!NOTE]
> Tento příklad bude fungovat pouze v počítači se systémem Windows Vista, na kterém je spuštěná aplikace Správce oken plochy (DWM) se zapnutým skleněným systémem. Edice Home Basic v systému Windows Vista nepodporuje transparentní skleněný efekt. Oblasti, které by se obvykle vygenerovaly s průhledným skleněným efektem v jiných edicích Windows Vista, se vykreslují neprůhledně.

## <a name="example"></a>Příklad

Následující obrázek znázorňuje skleněný rámec rozšířený na adresní řádek aplikace Internet Explorer 7:

![Snímek obrazovky znázorňující skleněný rámec rozšířený na adresní řádek IE7](./media/extend-glass-frame-into-a-wpf-application/internet-explorer-glass-frame-extended-address-bar.png)

Pokud chcete roztáhnout skleněný rámec na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikaci, je potřeba mít přístup k nespravovanému rozhraní API. Následující příklad kódu provádí vyvolání platformy (PInvoke) pro rozhraní API, které je potřeba k rozšiřování rámce do klientské oblasti. Každé z těchto rozhraní API je deklarováno ve třídě s názvem **NonClientRegionAPI**.

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

[DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) je funkce DWM, která rozšiřuje rámec do klientské oblasti. Používá dva parametry; popisovač okna a struktura [okrajů](/windows/win32/api/uxtheme/ns-uxtheme-margins) . Pomocí [okrajů](/windows/win32/api/uxtheme/ns-uxtheme-margins) správce oken informujte, kolik dalšího snímku by se mělo rozšířit do klientské oblasti.

## <a name="example"></a>Příklad

Chcete-li použít funkci [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) , je nutné získat popisovač okna. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]lze popisovač okna získat z vlastnosti <xref:System.Windows.Interop.HwndSource.Handle%2A> <xref:System.Windows.Interop.HwndSource>. V následujícím příkladu je rámec rozšířen do oblasti klienta na události <xref:System.Windows.FrameworkElement.Loaded> okna.

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

## <a name="example"></a>Příklad

Následující příklad ukazuje jednoduché okno, ve kterém je rámec rozšířen do klientské oblasti. Rámec je rozšířen za horní ohraničení, které obsahuje dva objekty <xref:System.Windows.Controls.TextBox>.

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

Následující obrázek znázorňuje skleněný rámec rozšířený do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace:

![Snímek obrazovky znázorňující skleněný rámec rozšířený do aplikace WPF](./media/extend-glass-frame-into-a-wpf-application/glass-frame-extended-wpf-application.png)

## <a name="see-also"></a>Viz také:

- [Přehled Správce oken plochy](/windows/desktop/dwm/dwm-overview)
- [Přehled rozostření Správce oken plochy](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
