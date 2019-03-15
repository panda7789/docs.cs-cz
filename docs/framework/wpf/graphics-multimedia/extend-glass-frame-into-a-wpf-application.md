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
ms.openlocfilehash: d7a00f2508769534e49c965d098dbacb01a1f189
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843529"
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Rozšíření skleněného rámečku do aplikace WPF

Toto téma ukazuje, jak rozšířit [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] skleněného rámečku do aplikace Windows Presentation Foundation (WPF) v oblasti klienta.

> [!NOTE]
> Tento příklad bude fungovat jenom na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] počítač Správce oken plochy (DWM) pomocí skla povolena. [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Edice Home Basic nepodporuje efekt skla transparentní. Oblasti, které by obvykle vykreslení s efekt skla transparentní na jinou edici [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] jsou generovány neprůhledné.

## <a name="example"></a>Příklad

Následující obrázek ukazuje skleněného rámečku rozšířit do adresa aplikace Internet Explorer 7.

**Internet Explorer s rozšířenou skleněného rámečku za adresního řádku.**

![Aplikace Internet Explorer 7 s rozšířeným za adresního řádku skleněného rámečku. ](./media/ie7glasstopbar.PNG "IE7glasstopbar")

Rozšíření skleněného rámečku na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací, přístupu k nespravované [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] je potřeba. Následující příklad kódu nemá nespravovaného kódu (pinvoke) pro dva [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] potřeba splnit pro rozšíření rámce do klientské oblasti. Každá z těchto [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou deklarovány ve třídě volá **NonClientRegionAPI**.

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

[Dwmextendframeintoclientarea –](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) je funkce Správce oken plochy, která rozšiřuje rámce do klientské oblasti. Přebírá dva parametry; Popisovač okna a [OKRAJE](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) struktury. [OKRAJE](/windows/desktop/api/uxtheme/ns-uxtheme-_margins) Správce oken plochy pozná, kolik dalších rámce by měl být rozšířena na klientské oblasti.

## <a name="example"></a>Příklad

Použít [dwmextendframeintoclientarea –](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea) funkce, je potřeba pořídit popisovač okna. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete získat popisovač okna <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost <xref:System.Windows.Interop.HwndSource>. V následujícím příkladu je na rámce rozšíří do klientské oblasti <xref:System.Windows.FrameworkElement.Loaded> událostí okna.

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

Následující příklad ukazuje, jednoduché okno, ve kterém je rámec rozšíří do klientské oblasti. Snímek je rozšířená za horního ohraničení, která obsahuje dvě <xref:System.Windows.Controls.TextBox> objekty.

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

Následující obrázek ukazuje skleněného rámečku do rozšířené [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.

**Rozšíří skleněného rámečku do**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**aplikace.**

![Skleněného rámečku rozšíří do aplikace WPF. ](./media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")

## <a name="see-also"></a>Viz také:

- [Přehled Správce oken plochy](/windows/desktop/dwm/dwm-overview)
- [Přehled Správce oken plochy rozostření](/windows/desktop/dwm/blur-ovw)
- [DwmExtendFrameIntoClientArea](/windows/desktop/api/dwmapi/nf-dwmapi-dwmextendframeintoclientarea)
