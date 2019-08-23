---
title: Mapování vlastnosti Windows Forms a WPF
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: ae4a97bc96a4f9e93942b4995f488c427fda3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917497"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapování vlastnosti Windows Forms a WPF
Technologie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají dva podobné modely vlastností, ale různé. *Mapování vlastností* podporuje vzájemné operace mezi těmito dvěma architekturami a poskytuje následující možnosti:  
  
- Usnadňuje mapování relevantních změn vlastností v hostitelském prostředí na hostovaný ovládací prvek nebo prvek.  
  
- Poskytuje výchozí zpracování pro mapování nejčastěji používaných vlastností.  
  
- Umožňuje snadné odebrání, přepsání nebo rozšíření výchozích vlastností.  
  
- Zajišťuje, aby změny hodnot vlastností na hostiteli byly automaticky rozpoznány a přeloženy do hostovaného ovládacího prvku nebo elementu.  
  
> [!NOTE]
> Události změny vlastností nejsou šířeny do hostitelského ovládacího prvku nebo hierarchie elementu. Převod vlastností se neprovede, pokud se místní hodnota vlastnosti nemění kvůli přímému nastavení, stylům, dědičnosti, datové vazbě nebo jiným mechanismům, které mění hodnotu vlastnosti.  
  
 Pro přístup k mapování vlastností <xref:System.Windows.Forms.Integration.WindowsFormsHost> použijte <xref:System.Windows.Forms.Integration.ElementHost>vlastnostu elementu a <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost ovládacího prvku. <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapování vlastností pomocí elementu WindowsFormsHost  
 Prvek přeloží výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti na jejich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty pomocí následující tabulky překladu. <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
  
|Windows Presentation Foundation hostování|Windows Forms|Chování mezi operacemi|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Element nastaví vlastnost hostovaného ovládacího prvku a <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost hostovaného ovládacího prvku. <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Forms.Integration.WindowsFormsHost> Mapování se provádí pomocí následujících pravidel:<br /><br /> -Pokud <xref:System.Windows.Controls.Control.Background%2A> je plná barva, je převedena a použita k <xref:System.Windows.Forms.Control.BackColor%2A> nastavení vlastnosti hostovaného ovládacího prvku. Vlastnost není nastavena u hostovaného ovládacího prvku, protože hostovaný ovládací prvek může dědit hodnotu <xref:System.Windows.Forms.Control.BackColor%2A> vlastnosti. <xref:System.Windows.Forms.Control.BackColor%2A> **Poznámka:**  Hostovaný ovládací prvek nepodporuje transparentnost. Jakákoli Barva přiřazená <xref:System.Windows.Forms.Control.BackColor%2A> k musí být plně neprůhledná, s hodnotou alfa typu 0xFF. <br /><br /> -Pokud <xref:System.Windows.Controls.Control.Background%2A> není plná barva <xref:System.Windows.Forms.Integration.WindowsFormsHost> , ovládací prvek <xref:System.Windows.Controls.Control.Background%2A> vytvoří rastrový obrázek z vlastnosti. Ovládací prvek přiřadí tento rastrový <xref:System.Windows.Forms.Control.BackgroundImage%2A> obrázek k vlastnosti hostovaného ovládacího prvku. <xref:System.Windows.Forms.Integration.WindowsFormsHost> To poskytuje efekt podobný transparentnosti. **Poznámka:**  Toto chování můžete přepsat nebo můžete odebrat <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Pokud nebylo znovu přiřazeno výchozí mapování, ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> projde svou nadřazenou hierarchii, dokud nenajde nadřazený objekt <xref:System.Windows.FrameworkElement.Cursor%2A> se sadou vlastností. Tato hodnota je přeložena na nejbližší odpovídající [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kurzor.<br /><br /> Pokud nebylo znovu přiřazeno výchozí <xref:System.Windows.FrameworkElement.ForceCursor%2A> mapování vlastnosti, procházení se zastaví na prvním předchůdce s <xref:System.Windows.FrameworkElement.ForceCursor%2A> nastavením na `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>provede mapování <xref:System.Windows.Forms.RightToLeft.No>na.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>provede mapování <xref:System.Windows.Forms.RightToLeft.Yes>na.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>není namapováno.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>provede mapování <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>na.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>v hostovaném ovládacím prvku<xref:System.Drawing.Font?displayProperty=nameWithType>|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností je přeložena do odpovídající <xref:System.Drawing.Font>. Když se jedna z těchto vlastností změní, vytvoří <xref:System.Drawing.Font> se nový. Pro <xref:System.Windows.FontStyles.Normal%2A> :<xref:System.Drawing.FontStyle.Italic> je zakázané. Pro <xref:System.Windows.FontStyles.Italic%2A> nebo <xref:System.Windows.FontStyles.Oblique%2A> :<xref:System.Drawing.FontStyle.Italic> je povolen.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>v hostovaném ovládacím prvku<xref:System.Drawing.Font?displayProperty=nameWithType>|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností je přeložena do odpovídající <xref:System.Drawing.Font>. Když se jedna z těchto vlastností změní, vytvoří <xref:System.Drawing.Font> se nový. Pro <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, ,,<xref:System.Windows.FontWeights.Heavy%2A> ,<xref:System.Drawing.FontStyle.Bold> , ,<xref:System.Windows.FontWeights.SemiBold%2A>nebo :jsoupovoleny<xref:System.Windows.FontWeights.UltraBold%2A>. <xref:System.Windows.FontWeights.DemiBold%2A> <xref:System.Windows.FontWeights.ExtraBold%2A> <xref:System.Windows.FontWeights.Medium%2A> Pro <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, ,,<xref:System.Windows.FontWeights.UltraLight%2A>nebo: je<xref:System.Drawing.FontStyle.Bold> zakázána. <xref:System.Windows.FontWeights.Regular%2A> <xref:System.Windows.FontWeights.Normal%2A> <xref:System.Windows.FontWeights.Thin%2A>|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností je přeložena do odpovídající <xref:System.Drawing.Font>. Když se jedna z těchto vlastností změní, vytvoří <xref:System.Drawing.Font> se nový. Velikost hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku se změní na základě velikosti písma.<br /><br /> Velikost písma v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vyjádřena jako jedna devadesátá šestá palce a v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jedné Seventy sekundy palce. Odpovídající převod je:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]velikost písma = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] velikost písma * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Mapování <xref:System.Windows.Controls.Control.Foreground%2A> vlastností se provádí pomocí následujících pravidel:<br /><br /> – Pokud <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Media.SolidColorBrush.Color%2A> je, použijte pro<xref:System.Windows.Forms.Control.ForeColor%2A>. <xref:System.Windows.Media.SolidColorBrush><br />-Pokud <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Forms.Control.ForeColor%2A>je, použijte barvu snejnižšíhodnotouposunupro.<xref:System.Windows.Media.GradientStop> <xref:System.Windows.Media.GradientBrush><br />– Pro jakýkoliv jiný <xref:System.Windows.Media.Brush> typ ponechte <xref:System.Windows.Forms.Control.ForeColor%2A> beze změny. To znamená, že se použije výchozí hodnota.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Pokud <xref:System.Windows.UIElement.IsEnabled%2A> je nastaveno, <xref:System.Windows.Forms.Integration.WindowsFormsHost> element nastaví <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost v hostovaném ovládacím prvku.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Všechny čtyři hodnoty <xref:System.Windows.Forms.Control.Padding%2A> vlastnosti u hostovaného [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku jsou nastaveny na stejnou <xref:System.Windows.Thickness> hodnotu.<br /><br /> -Hodnoty větší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.<br />-Hodnoty menší než <xref:System.Int32.MinValue> jsou nastaveny na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>provede mapování <xref:System.Windows.Forms.Control.Visible%2A>na  =  .`true` Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek je viditelný. Explicitní nastavení <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti u hostovaného ovládacího prvku na `false` není doporučeno.<br />-   <xref:System.Windows.Visibility.Collapsed>provede mapování <xref:System.Windows.Forms.Control.Visible%2A>  =  na nebo`true` . `false` Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek není vykreslen a jeho oblast je sbalená.<br />-   <xref:System.Windows.Visibility.Hidden> : Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek zabírá prostor v rozložení, ale není viditelný. V tomto případě <xref:System.Windows.Forms.Control.Visible%2A> je vlastnost nastavena na `true`. Explicitní nastavení <xref:System.Windows.Forms.Control.Visible%2A> vlastnosti u hostovaného ovládacího prvku na `false` není doporučeno.|  
  
 Připojené vlastnosti prvků kontejneru jsou plně podporovány <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvkem.  
  
 Další informace najdete v tématu [Návod: Mapování vlastností pomocí elementu](walkthrough-mapping-properties-using-the-windowsformshost-element.md)WindowsFormsHost  
  
## <a name="updates-to-parent-properties"></a>Aktualizace nadřazených vlastností  
 Změny většiny nadřazených vlastností způsobují oznámení hostovanému podřízenému ovládacímu prvku. Následující seznam popisuje vlastnosti, které při změně jejich hodnot nezpůsobují oznámení.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Například pokud změníte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> prvku, <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost hostovaného ovládacího prvku se nezmění.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapování vlastností pomocí ovládacího prvku ElementHost  
 Následující vlastnosti poskytují integrované oznámení o změně. Nevolejte <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> metodu při mapování těchto vlastností:  
  
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
  
- Povoleno  
  
- Písma  
  
- ForeColor  
  
- Umístění  
  
- Rezervy  
  
- Odsazení  
  
- Nadřazené  
  
- Oblast  
  
- RightToLeft  
  
- Velikost  
  
- TabIndex  
  
- Tabelátor  
  
- Text  
  
- Viditelné  
  
 Ovládací prvek přeloží výchozí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti na jejich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty pomocí následující tabulky překladu. <xref:System.Windows.Forms.Integration.ElementHost>  
  
 Další informace najdete v tématu [Návod: Mapování vlastností pomocí ovládacího prvku](walkthrough-mapping-properties-using-the-elementhost-control.md)ElementHost  
  
|model Windows Forms hostování|Windows Presentation Foundation|Chování mezi operacemi|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaném elementu|Nastavení této vlastnosti vynutí překreslení pomocí <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Forms.Control.BackColor%2A> <xref:System.Windows.Media.ImageBrush> `false` <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> <xref:System.Windows.Forms.Control.BackgroundImage%2A>Pokud je <xref:System.Windows.Forms.Integration.ElementHost> vlastnost nastavena na (výchozí hodnota), je založena na vzhledu ovládacího prvku, včetně jeho vlastností,, vlastností a jakékoli připojené malby. <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> žádostí.<br /><br /> <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Forms.Control.BackgroundImage%2A> <xref:System.Windows.Forms.Integration.ElementHost> <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> Pokud je `true`vlastnost nastavena na, je založena na vzhledu nadřazeného ovládacího prvku, včetně nadřazeného <xref:System.Windows.Forms.Control.BackColor%2A>prvku, vlastnosti a jakékoli připojené malby. <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> žádostí.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaném elementu|Nastavení této vlastnosti způsobí, že se pro <xref:System.Windows.Forms.Control.BackColor%2A> mapování napíše stejné chování.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaném elementu|Nastavení této vlastnosti způsobí, že se pro <xref:System.Windows.Forms.Control.BackColor%2A> mapování napíše stejné chování.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Standardní kurzor je přeložen na odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardní kurzor. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Pokud se [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nejedná o standardní kurzor, je přiřazena výchozí hodnota.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Když <xref:System.Windows.Forms.Control.Enabled%2A> je nastaveno <xref:System.Windows.Forms.Integration.ElementHost> , ovládací prvek nastaví <xref:System.Windows.UIElement.IsEnabled%2A> vlastnost v hostovaném elementu.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|Hodnota je přeložena do odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sady vlastností písma. <xref:System.Windows.Forms.Control.Font%2A>|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>v hostovaném elementu|Pokud <xref:System.Drawing.Font.Bold%2A> je `true`, je<xref:System.Windows.Controls.Control.FontWeight%2A> nastaveno na <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Pokud <xref:System.Drawing.Font.Bold%2A> je `false`, je<xref:System.Windows.Controls.Control.FontWeight%2A> nastaveno na <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>v hostovaném elementu|Pokud <xref:System.Drawing.Font.Italic%2A> je `true`, je<xref:System.Windows.Controls.Control.FontStyle%2A> nastaveno na <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Pokud <xref:System.Drawing.Font.Italic%2A> je `false`, je<xref:System.Windows.Controls.Control.FontStyle%2A> nastaveno na <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>v hostovaném elementu|Platí pouze při hostování <xref:System.Windows.Controls.TextBlock> ovládacího prvku.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>v hostovaném elementu|Platí pouze při hostování <xref:System.Windows.Controls.TextBlock> ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>provede mapování <xref:System.Windows.FlowDirection.LeftToRight>na.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>provede mapování <xref:System.Windows.FlowDirection.RightToLeft>na.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek <xref:System.Windows.UIElement.Visibility%2A> nastaví vlastnost u hostovaného elementu pomocí následujících pravidel:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`provede mapování <xref:System.Windows.Visibility.Visible>na.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`provede mapování <xref:System.Windows.Visibility.Hidden>na.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Vzájemná spolupráce subsystémů WPF a Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Návod: Mapování vlastností pomocí elementu WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Návod: Mapování vlastností pomocí ovládacího prvku ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
