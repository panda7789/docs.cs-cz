---
title: "Mapování vlastnosti Windows Forms a WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0af1015747e2f27b19c2cac2c896dd60214264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapování vlastnosti Windows Forms a WPF
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie mít dva modely podobné, ale jiné vlastnosti. *Mapování vlastností* podporuje vzájemná spolupráce mezi dvěma architektury a poskytuje následující možnosti:  
  
-   Usnadňuje hostované ovládací prvek nebo element mapy relevantní vlastnost změny v hostitelském prostředí.  
  
-   Poskytuje výchozí zpracování pro mapování nejvíc běžně používá vlastnosti.  
  
-   Umožňuje snadno odebrání přepsání nebo rozšíření výchozí vlastnosti.  
  
-   Zajistí, aby se automaticky zjistil a přeložit hostované ovládací prvek nebo element změn hodnot vlastností na hostiteli.  
  
> [!NOTE]
>  Změna vlastnosti události nebudou rozšířeny hostování ovládacího prvku nebo element hierarchie. Vlastnost překlad není provést, pokud místní hodnota vlastnosti se nezmění z důvodu přímé nastavení, styly, dědičnosti, vazby dat nebo jiných mechanismů, které změňte hodnotu vlastnosti.  
  
 Použití <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> vlastnost na <xref:System.Windows.Forms.Integration.WindowsFormsHost> element a <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost na <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek pro přístup k mapování vlastností.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapování vlastností s elementem WindowsFormsHost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element překládá výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti k jejich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty pomocí následující tabulky.  
  
|Hostování Windows Presentation Foundation|Windows Forms|Součinnosti chování|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> Nastaví element <xref:System.Windows.Forms.Control.BackColor%2A> vlastnosti hostované ovládacího prvku a <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnosti hostované ovládacího prvku. Mapování se provádí na základě následujících pravidel:<br /><br /> -Pokud <xref:System.Windows.Controls.Control.Background%2A> je plnou barvou je převést a používá se k nastavení <xref:System.Windows.Forms.Control.BackColor%2A> vlastnosti hostované ovládacího prvku. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost není nastaven na hostované ovládací prvek, protože hostovaného ovládacího prvku může dědit vlastnosti hodnotu <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost. **Poznámka:** hostované ovládací prvek nepodporuje průhlednost. Všechny barva přiřazená <xref:System.Windows.Forms.Control.BackColor%2A> musí být zcela neprůhledné, s hodnotou alfa 0xFF. <br /><br /> -Pokud <xref:System.Windows.Controls.Control.Background%2A> není plnou barvou <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení vytvoří rastrového obrázku z <xref:System.Windows.Controls.Control.Background%2A> vlastnost. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Přiřadí této bitové mapy do ovládacího prvku <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnosti hostované ovládacího prvku. To poskytuje efektu, který je podobný průhlednost. **Poznámka:** toto chování můžete přepsat nebo můžete odebrat <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Pokud nebyl byl znovu přiřazen výchozí mapování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení prochází jeho předchůdce hierarchie, dokud nenajde nadřazený prvek s jeho <xref:System.Windows.FrameworkElement.Cursor%2A> sadu vlastností. Tato hodnota se převede na nejbližší odpovídající [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kurzoru.<br /><br /> Pokud výchozí mapování <xref:System.Windows.FrameworkElement.ForceCursor%2A> vlastnost nebyla byl znovu přiřazen, průchodu zastaví v první podřízeném objektu s <xref:System.Windows.FrameworkElement.ForceCursor%2A> nastavena na `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>se mapuje na <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>se mapuje na <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>Není namapovaná.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>se mapuje na <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>v hostované ovládacího prvku<xref:System.Drawing.Font?displayProperty=nameWithType>|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti je přeložit na odpovídající <xref:System.Drawing.Font>. Když se změní jednu z těchto vlastností, nový <xref:System.Drawing.Font> je vytvořena. Pro <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> je zakázána. Pro <xref:System.Windows.FontStyles.Italic%2A> nebo <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> je povoleno.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>v hostované ovládacího prvku<xref:System.Drawing.Font?displayProperty=nameWithType>|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti je přeložit na odpovídající <xref:System.Drawing.Font>. Když se změní jednu z těchto vlastností, nový <xref:System.Drawing.Font> je vytvořena. Pro <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, nebo <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> je povoleno. Pro <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, nebo <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> je zakázána.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti je přeložit na odpovídající <xref:System.Drawing.Font>. Když se změní jednu z těchto vlastností, nový <xref:System.Drawing.Font> je vytvořena. Hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení změní velikost na základě velikosti písma.<br /><br /> Velikost písma v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vyjádřena jako jedna 90 šestinu palce a v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jako jednu sekundu sedmdesáti palce. Odpovídající převod je:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]velikost písma = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] velikost písma * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Mapování vlastností se provádí na základě následujících pravidel:<br /><br /> -Pokud <xref:System.Windows.Controls.Control.Foreground%2A> je <xref:System.Windows.Media.SolidColorBrush>, použijte <xref:System.Windows.Media.SolidColorBrush.Color%2A> pro <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Pokud <xref:System.Windows.Controls.Control.Foreground%2A> je <xref:System.Windows.Media.GradientBrush>, použijte barvu <xref:System.Windows.Media.GradientStop> s nejnižší hodnotou posunutí pro <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />– Pro všechny ostatní <xref:System.Windows.Media.Brush> typem, nechte <xref:System.Windows.Forms.Control.ForeColor%2A> beze změny. To znamená, že se používá výchozí nastavení.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Když <xref:System.Windows.UIElement.IsEnabled%2A> nastavena, <xref:System.Windows.Forms.Integration.WindowsFormsHost> nastaví element <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost u prvku hostované.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Všechny čtyři hodnoty <xref:System.Windows.Forms.Control.Padding%2A> vlastnost hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení se nastaví na stejnou <xref:System.Windows.Thickness> hodnotu.<br /><br /> -Hodnoty vyšší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.<br />-Hodnoty menší než <xref:System.Int32.MinValue> jsou nastaveny na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>se mapuje na <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je viditelný. Explicitní nastavení <xref:System.Windows.Forms.Control.Visible%2A> vlastnost u prvku hostované na `false` se nedoporučuje.<br />-   <xref:System.Windows.Visibility.Collapsed>se mapuje na <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` nebo `false`. Hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není vykreslovat ovládací prvek a jeho oblasti sbalena.<br />-   <xref:System.Windows.Visibility.Hidden>: Hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení zabírá prostoru v rozložení, ale není viditelná. V takovém případě <xref:System.Windows.Forms.Control.Visible%2A> je nastavena na `true`. Explicitní nastavení <xref:System.Windows.Forms.Control.Visible%2A> vlastnost u prvku hostované na `false` se nedoporučuje.|  
  
 Přidružené vlastnosti na elementy kontejnerů plně podporuje <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
 Další informace najdete v tématu [návod: mapování vlastností pomocí elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Aktualizace vlastnosti nadřazené  
 Změny většina vlastnosti nadřazené způsobit oznámení do ovládacího prvku hostovaná podřízená. Následující seznam popisuje vlastnosti, které nezpůsobí oznámení, pokud jejich hodnoty změnit.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Například, pokud změníte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, <xref:System.Windows.Forms.Control.BackColor%2A> vlastnosti hostované ovládacího prvku se nemění.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapování vlastností s elementhost – ovládací prvek  
 Následující vlastnosti poskytují oznámení o změně předdefinované. Nevolejte <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> metoda při mapování těchto vlastností:  
  
-   AutoSize  
  
-   Barva pozadí  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   Vazby  
  
-   CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Kurzor  
  
-   Ukotvení  
  
-   Povoleno  
  
-   Písma  
  
-   ForeColor  
  
-   Umístění  
  
-   Okraj  
  
-   Odsazení  
  
-   Nadřazené  
  
-   Oblast  
  
-   RightToLeft  
  
-   Velikost  
  
-   Pořadové číslo prvku  
  
-   Zarážek tabulátorů  
  
-   Text  
  
-   Viditelné  
  
 <xref:System.Windows.Forms.Integration.ElementHost> Řízení překládá výchozí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti, které chcete jejich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty podle pomocí následující tabulky.  
  
 Další informace najdete v tématu [návod: mapování vlastností pomocí ovládacího prvku ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Windows Forms hostování|Windows Presentation Foundation|Součinnosti chování|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostované elementu|Nastavení této vlastnosti vynutí překreslit s <xref:System.Windows.Media.ImageBrush>. Pokud <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> je nastavena na `false` (výchozí hodnota), to <xref:System.Windows.Media.ImageBrush> je založena na vzhled <xref:System.Windows.Forms.Integration.ElementHost> řídit, včetně jeho <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> vlastnosti a všechny připojené Malování obslužné rutiny.<br /><br /> Pokud <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> je nastavena na `true`, <xref:System.Windows.Media.ImageBrush> je založena na vzhled <xref:System.Windows.Forms.Integration.ElementHost> nadřazeného ovládacího prvku, včetně nadřazeného <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> vlastnosti a všechny připojené Malování obslužné rutiny.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostované elementu|Nastavení této vlastnosti způsobí, že stejné chování pro popsané <xref:System.Windows.Forms.Control.BackColor%2A> mapování.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostované elementu|Nastavení této vlastnosti způsobí, že stejné chování pro popsané <xref:System.Windows.Forms.Control.BackColor%2A> mapování.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standardní kurzor převádějí do odpovídajících [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardní kurzoru. Pokud [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není standardní kurzoru, výchozí hodnota je přiřazen.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Při <xref:System.Windows.Forms.Control.Enabled%2A> nastavena, <xref:System.Windows.Forms.Integration.ElementHost> řízení nastaví <xref:System.Windows.UIElement.IsEnabled%2A> vlastnost u prvku hostované.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> Hodnota je přeložit na odpovídající sadu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti písma.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>u hostované elementu|Pokud <xref:System.Drawing.Font.Bold%2A> je `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> je nastaven na <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Pokud <xref:System.Drawing.Font.Bold%2A> je `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> je nastaven na <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>u hostované elementu|Pokud <xref:System.Drawing.Font.Italic%2A> je `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> je nastaven na <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Pokud <xref:System.Drawing.Font.Italic%2A> je `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> je nastaven na <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>u hostované elementu|Platí pouze při hostování <xref:System.Windows.Controls.TextBlock> ovládacího prvku.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>u hostované elementu|Platí pouze při hostování <xref:System.Windows.Controls.TextBlock> ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>se mapuje na <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>se mapuje na <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Řízení nastaví <xref:System.Windows.UIElement.Visibility%2A> vlastnost u prvku hostované pomocí následujících pravidel:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`se mapuje na <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`se mapuje na <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [WPF a vzájemná spolupráce Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [Návod: Mapování vlastností pomocí elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)  
 [Návod: Mapování vlastností pomocí elementhost – ovládací prvek](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
