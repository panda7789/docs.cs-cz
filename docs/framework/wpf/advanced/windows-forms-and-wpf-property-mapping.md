---
title: Mapování vlastnosti Windows Forms a WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 07e58f87d886212426e25be83f988037549ab642
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735232"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapování vlastnosti Windows Forms a WPF
Technologie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají dva podobné, ale různé modely vlastností. *Mapování vlastností* podporuje vzájemné operace mezi těmito dvěma architekturami a poskytuje následující možnosti:  
  
- Usnadňuje mapování relevantních změn vlastností v hostitelském prostředí na hostovaný ovládací prvek nebo prvek.  
  
- Poskytuje výchozí zpracování pro mapování nejčastěji používaných vlastností.  
  
- Umožňuje snadné odebrání, přepsání nebo rozšíření výchozích vlastností.  
  
- Zajišťuje, aby změny hodnot vlastností na hostiteli byly automaticky rozpoznány a přeloženy do hostovaného ovládacího prvku nebo elementu.  
  
> [!NOTE]
> Události změny vlastností nejsou šířeny do hostitelského ovládacího prvku nebo hierarchie elementu. Převod vlastností se neprovede, pokud se místní hodnota vlastnosti nemění kvůli přímému nastavení, stylům, dědičnosti, datové vazbě nebo jiným mechanismům, které mění hodnotu vlastnosti.  
  
 Pro přístup k mapování vlastností použijte vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> u elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> a vlastnost <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapování vlastností pomocí elementu WindowsFormsHost  
 Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> překládá výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností na jejich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty pomocí následující tabulky překladu.  
  
|Windows Presentation Foundation hostování|Windows Forms|Chování mezi operacemi|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Element <xref:System.Windows.Forms.Integration.WindowsFormsHost> nastaví vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> hostovaného ovládacího prvku a vlastnost <xref:System.Windows.Forms.Control.BackgroundImage%2A> hostovaného ovládacího prvku. Mapování se provádí pomocí následujících pravidel:<br /><br /> -Pokud <xref:System.Windows.Controls.Control.Background%2A> je plná barva, je převedena a použita k nastavení vlastnosti <xref:System.Windows.Forms.Control.BackColor%2A> hostovaného ovládacího prvku. Vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> není nastavena u hostovaného ovládacího prvku, protože hostovaný ovládací prvek může dědit hodnotu vlastnosti <xref:System.Windows.Forms.Control.BackColor%2A>. **Poznámka:**  Hostovaný ovládací prvek nepodporuje transparentnost. Jakákoli Barva přiřazená <xref:System.Windows.Forms.Control.BackColor%2A> musí být plně neprůhledná, s hodnotou alfa typu 0xFF. <br /><br /> -Pokud <xref:System.Windows.Controls.Control.Background%2A> není plná barva, ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> vytvoří bitmapu z vlastnosti <xref:System.Windows.Controls.Control.Background%2A>. Ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> přiřadí tento rastrový obrázek k vlastnosti <xref:System.Windows.Forms.Control.BackgroundImage%2A> hostovaného ovládacího prvku. To poskytuje efekt podobný transparentnosti. **Poznámka:**  Toto chování můžete přepsat nebo můžete odebrat mapování <xref:System.Windows.Controls.Control.Background%2A> vlastností.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Pokud nebylo znovu přiřazeno výchozí mapování, <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení projde hierarchii předchůdce, dokud nenajde nadřazený objekt se sadou vlastností <xref:System.Windows.FrameworkElement.Cursor%2A>. Tato hodnota je přeložena na nejbližší odpovídající [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kurzor.<br /><br /> Pokud nebylo znovu přiřazeno výchozí mapování pro vlastnost <xref:System.Windows.FrameworkElement.ForceCursor%2A>, přesměruje se procházení prvního předchůdce s <xref:System.Windows.FrameworkElement.ForceCursor%2A> nastaveným na `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> se mapuje na <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> se mapuje na <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> není namapovaný.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> se mapuje na <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> <xref:System.Drawing.Font?displayProperty=nameWithType> hostovaného ovládacího prvku|Sada vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je přeložena do odpovídající <xref:System.Drawing.Font>. Když se jedna z těchto vlastností změní, vytvoří se nový <xref:System.Drawing.Font>. Pro <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> je zakázaná. Pro <xref:System.Windows.FontStyles.Italic%2A> nebo <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> je povolený.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> <xref:System.Drawing.Font?displayProperty=nameWithType> hostovaného ovládacího prvku|Sada vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je přeložena do odpovídající <xref:System.Drawing.Font>. Když se jedna z těchto vlastností změní, vytvoří se nový <xref:System.Drawing.Font>. Pro <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>nebo <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> je povolený. Pro <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>nebo <xref:System.Windows.FontWeights.UltraLight%2A>je zakázaný <xref:System.Drawing.FontStyle.Bold>.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Sada vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je přeložena do odpovídající <xref:System.Drawing.Font>. Když se jedna z těchto vlastností změní, vytvoří se nový <xref:System.Drawing.Font>. Velikost hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku se změní na základě velikosti písma.<br /><br /> Velikost písma v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se vyjadřuje jako jedna devadesátá čtvrtina palce a v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jako jedna Seventy palce. Odpovídající převod je:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] velikost písma = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] velikost písma * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Mapování vlastností <xref:System.Windows.Controls.Control.Foreground%2A> se provádí pomocí následujících pravidel:<br /><br /> – Pokud je <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.SolidColorBrush>, použijte <xref:System.Windows.Media.SolidColorBrush.Color%2A> pro <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />– Pokud je <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.GradientBrush>, použijte barvu <xref:System.Windows.Media.GradientStop> s nejnižší hodnotou posunu pro <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />– Pro jakýkoli jiný typ <xref:System.Windows.Media.Brush> ponechte <xref:System.Windows.Forms.Control.ForeColor%2A> beze změny. To znamená, že se použije výchozí hodnota.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Je-li nastavena <xref:System.Windows.UIElement.IsEnabled%2A>, <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvek nastaví vlastnost <xref:System.Windows.Forms.Control.Enabled%2A> v hostovaném ovládacím prvku.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Všechny čtyři hodnoty vlastnosti <xref:System.Windows.Forms.Control.Padding%2A> u hostovaného ovládacího prvku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jsou nastaveny na stejnou hodnotu <xref:System.Windows.Thickness>.<br /><br /> -Hodnoty větší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.<br />-Hodnoty menší než <xref:System.Int32.MinValue> jsou nastaveny na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> se mapuje na <xref:System.Windows.Forms.Control.Visible%2A> = `true`. Ovládací prvek hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] je viditelný. Explicitní nastavení vlastnosti <xref:System.Windows.Forms.Control.Visible%2A> u hostovaného ovládacího prvku na `false` se nedoporučuje.<br />-   <xref:System.Windows.Visibility.Collapsed> se mapuje na <xref:System.Windows.Forms.Control.Visible%2A> = `true` nebo `false`. Ovládací prvek hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není vykreslen a jeho oblast je sbalená.<br />-   <xref:System.Windows.Visibility.Hidden>: hostovaný ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zabírá prostor v rozložení, ale není viditelný. V tomto případě je vlastnost <xref:System.Windows.Forms.Control.Visible%2A> nastavena na hodnotu `true`. Explicitní nastavení vlastnosti <xref:System.Windows.Forms.Control.Visible%2A> u hostovaného ovládacího prvku na `false` se nedoporučuje.|  
  
 Připojené vlastnosti prvků kontejneru jsou plně podporovány prvkem <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Další informace naleznete v tématu [Návod: mapování vlastností pomocí elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Aktualizace nadřazených vlastností  
 Změny většiny nadřazených vlastností způsobují oznámení hostovanému podřízenému ovládacímu prvku. Následující seznam popisuje vlastnosti, které při změně jejich hodnot nezpůsobují oznámení.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Například při změně hodnoty vlastnosti <xref:System.Windows.Controls.Control.Background%2A> elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> se nemění vlastnost <xref:System.Windows.Forms.Control.BackColor%2A> hostovaného ovládacího prvku.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapování vlastností pomocí ovládacího prvku ElementHost  
 Následující vlastnosti poskytují integrované oznámení o změně. Nevolejte metodu <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> při mapování těchto vlastností:  
  
- AutoSize  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- Vlastnosti CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Kurzor  
  
- Vyjměte  
  
- Povolit  
  
- Písma  
  
- ForeColor  
  
- Umístění  
  
- Rezervy  
  
- Odsazení  
  
- nadřazené  
  
- Oblast  
  
- RightToLeft  
  
- Velikost  
  
- TabIndex  
  
- Tabelátor  
  
- Text  
  
- Viditelný  
  
 Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> přeloží výchozí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastností na jejich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty pomocí následující tabulky překladu.  
  
 Další informace naleznete v tématu [Návod: mapování vlastností pomocí ovládacího prvku ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|model Windows Forms hostování|Windows Presentation Foundation|Chování mezi operacemi|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaném elementu|Nastavení této vlastnosti vynutí překreslení pomocí <xref:System.Windows.Media.ImageBrush>. Pokud je vlastnost <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> nastavena na hodnotu `false` (výchozí hodnota), je tato <xref:System.Windows.Media.ImageBrush> založena na vzhledu <xref:System.Windows.Forms.Integration.ElementHost>ho ovládacího prvku, včetně jeho <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> vlastností a všech připojených obslužných rutin nátěru.<br /><br /> Je-li vlastnost <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> nastavena na hodnotu `true`, <xref:System.Windows.Media.ImageBrush> vychází z vzhledu nadřazeného ovládacího prvku <xref:System.Windows.Forms.Integration.ElementHost>, včetně vlastností nadřazeného objektu <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> a všech připojených obslužných rutin nátěru.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaném elementu|Nastavení této vlastnosti způsobí, že se pro mapování <xref:System.Windows.Forms.Control.BackColor%2A> napíše stejné chování.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaném elementu|Nastavení této vlastnosti způsobí, že se pro mapování <xref:System.Windows.Forms.Control.BackColor%2A> napíše stejné chování.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Kurzor [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standard je přeložen na odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardní kurzor. Pokud [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není standardní kurzor, je přiřazena výchozí hodnota.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Je-li nastavena <xref:System.Windows.Forms.Control.Enabled%2A>, ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> nastaví vlastnost <xref:System.Windows.UIElement.IsEnabled%2A> v hostovaném elementu.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|Hodnota <xref:System.Windows.Forms.Control.Font%2A> je přeložena do odpovídající sady [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností písma.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> v hostovaném elementu|Pokud je <xref:System.Drawing.Font.Bold%2A> `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> nastaveno na <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Pokud je <xref:System.Drawing.Font.Bold%2A> `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> nastaveno na <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> v hostovaném elementu|Pokud je <xref:System.Drawing.Font.Italic%2A> `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> nastaveno na <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Pokud je <xref:System.Drawing.Font.Italic%2A> `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> nastaveno na <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> v hostovaném elementu|Platí pouze při hostování ovládacího prvku <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> v hostovaném elementu|Platí pouze při hostování ovládacího prvku <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> se mapuje na <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> se mapuje na <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> nastaví vlastnost <xref:System.Windows.UIElement.Visibility%2A> u hostovaného elementu pomocí následujících pravidel:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` se mapuje na <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` se mapuje na <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Vzájemná spolupráce subsystémů WPF a Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Návod: Mapování vlastností pomocí elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Návod: Mapování vlastností pomocí ovládacího prvku ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
