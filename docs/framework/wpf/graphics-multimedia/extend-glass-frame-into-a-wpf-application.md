---
title: Rozšíření skleněného rámečku do aplikace WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], extending glass frames into
- graphics [WPF], extending glass frames into applications
- extending glass frames into applications [WPF]
- glass frames [WPF], extending into applications
ms.assetid: 74388a3a-4b69-4a9d-ba1f-e107636bd660
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03a2b8c6184a6cb79d1e42598a65972a08718e10
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="extend-glass-frame-into-a-wpf-application"></a>Rozšíření skleněného rámečku do aplikace WPF
Toto téma ukazuje, jak rozšířit [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] pohotovostní rámce do oblasti klienta aplikace Windows Presentation Foundation (WPF).  
  
> [!NOTE]
>  V tomto příkladu budou fungovat jenom na [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] počítač se systémem Manager okno plochy (správce) s pohotovostní povolena. [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] Domácí edice Basic nepodporuje transparentní skleněný efekt. Oblasti, které by obvykle vykreslení s transparentní skleněný efekt na jinou edici [!INCLUDE[TLA2#tla_winvista](../../../../includes/tla2sharptla-winvista-md.md)] vykreslují neprůhledné.  
  
## <a name="example"></a>Příklad  
 Následující obrázek ukazuje pohotovostní rámečku rozšířené do na adresu aplikace Internet Explorer 7.  
  
 **Internet Explorer s rámečkem rozšířené pohotovostní za panel Adresa.**  
  
 ![IE7 s rámečkem pohotovostní rozšířeným za panel Adresa. ] (../../../../docs/framework/wpf/graphics-multimedia/media/ie7glasstopbar.PNG "IE7glasstopbar")  
  
 Rozšíření rámce přehledné na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, přístup k nespravované [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] je potřeba. Následující příklad kódu nemá nespravovaného (kódu pinvoke) pro dva [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] potřeba splnit pro rozšíření rámečku do klientské oblasti. Každá z těchto [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou deklarované v třídy s názvem **NonClientRegionAPI**.  
  
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
  
 [Dwmextendframeintoclientarea –](https://msdn.microsoft.com/library/aa969512.aspx) je funkce Správce oken plochy, která rozšiřuje rámečku do klientské oblasti. Jak dlouho trvá dva parametry; Popisovač okna a [OKRAJE](https://msdn.microsoft.com/library/bb773244.aspx) struktura. [OKRAJE](https://msdn.microsoft.com/library/bb773244.aspx) Správce oken plochy pozná, kolik velmi rámečku by měla být rozšířena na klientské oblasti.  
  
## <a name="example"></a>Příklad  
 Chcete-li použít [dwmextendframeintoclientarea –](https://msdn.microsoft.com/library/aa969512.aspx) funkce, musí být získána popisovač okna. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], můžete získat popisovač okna <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost <xref:System.Windows.Interop.HwndSource>. V následujícím příkladu je rozšířeno rámečku do oblasti klienta na <xref:System.Windows.FrameworkElement.Loaded> událost okna.  
  
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
 Následující příklad ukazuje jednoduchý okno, ve kterém je rozšířeno rámečku do klientské oblasti. Rámečku je rozšířeno za horního ohraničení, který obsahuje dva <xref:System.Windows.Controls.TextBox> objekty.  
  
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
  
 Následující obrázek ukazuje pohotovostní rámečku rozšířené na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace.  
  
 **Pohotovostní rámec rozšířený do**[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]**aplikace.**  
  
 ![Skleněný rámec rozšířený do aplikace WPF. ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfextendedglassintoclient.PNG "WPFextendedGlassIntoClient")  
  
## <a name="see-also"></a>Viz také  
 [Přehled Správce oken plochy](https://msdn.microsoft.com/library/aa969540.aspx)  
 [Přehled Správce oken plochy rozostření](https://msdn.microsoft.com/library/aa969537.aspx)  
 [DwmExtendFrameIntoClientArea](https://msdn.microsoft.com/library/aa969512.aspx)
