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
ms.openlocfilehash: 9e2cd55d0d5eb453ad5d29b707a14b9894d40089
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493700"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mapování vlastnosti Windows Forms a WPF
[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie mají dva modely podobné, ale jiné vlastnosti. *Mapování vlastností* podporuje interoperabilitu mezi dvěma architektury a poskytuje následující možnosti:  
  
-   Usnadňuje mapování odpovídající vlastnost změny v prostředí hostitele do hostovaného ovládacího prvku nebo prvku.  
  
-   Poskytuje výchozí zpracování pro mapování většinu běžně používá vlastnosti.  
  
-   Umožňuje snadné odstranění přepsání nebo rozšíření z výchozí vlastnosti.  
  
-   Zajišťuje, že změny hodnot vlastnosti na hostiteli jsou automaticky zjištěny a přeložit do hostovaného ovládacího prvku nebo prvku.  
  
> [!NOTE]
>  Události změny vlastnosti nejsou šířeny hostující ovládací prvek nebo hierarchie elementů. Vlastnost překladu se neprovádí, pokud místní hodnota vlastnosti se nezmění z důvodu nastavení s přímým přístupem, styly, dědičnost, datové vazby nebo jiných mechanismů, které změňte hodnotu vlastnosti.  
  
 Použití <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu a <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> vlastnost <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek pro přístup k mapování vlastností.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mapování vlastností pomocí elementu WindowsFormsHost  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Element přeloží výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti k jejich [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty pomocí následující tabulky.  
  
|Hostování Windows Presentation Foundation|Windows Forms|Chování vzájemné spolupráce|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Integration.WindowsFormsHost> Nastaví element <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost hostovaného ovládacího prvku a <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost hostovaného ovládacího prvku. Mapování se provádí pomocí následujících pravidel:<br /><br /> – Pokud <xref:System.Windows.Controls.Control.Background%2A> plnou barvu, je převedena a slouží k nastavení <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost hostovaného ovládacího prvku. <xref:System.Windows.Forms.Control.BackColor%2A> Vlastnost není nastavena na hostované ovládací prvek, protože hostovaného ovládacího prvku může zdědit hodnoty <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost. **Poznámka:**  Hostované ovládací prvek nepodporuje průhlednosti. Libovolné barvy přiřazené k <xref:System.Windows.Forms.Control.BackColor%2A> musí být úplně neprůhledné alfanumerické hodnotou 0xFF. <br /><br /> – Pokud <xref:System.Windows.Controls.Control.Background%2A> není plnou barvu <xref:System.Windows.Forms.Integration.WindowsFormsHost> vytvoří rastrový obrázek z ovládacího prvku <xref:System.Windows.Controls.Control.Background%2A> vlastnost. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Přiřadí tento rastrový obrázek pro ovládací prvek <xref:System.Windows.Forms.Control.BackgroundImage%2A> vlastnost hostovaného ovládacího prvku. Tímto způsobem efekt, který je podobný průhlednost. **Poznámka:**  Toto chování můžete přepsat nebo můžete odebrat <xref:System.Windows.Controls.Control.Background%2A> mapování vlastností.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Pokud výchozí mapování nebyla přiřazena, <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek prochází jeho předchůdce hierarchie, dokud nenajde podřízeném objektu s jeho <xref:System.Windows.FrameworkElement.Cursor%2A> sadu vlastností. Tato hodnota se přeloží na nejbližší odpovídající [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kurzoru.<br /><br /> Pokud výchozí mapování <xref:System.Windows.FrameworkElement.ForceCursor%2A> vlastnost nebyla změnilo, průchodu zastaví na prvním podřízeném objektu s <xref:System.Windows.FrameworkElement.ForceCursor%2A> nastavena na `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> mapuje <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> mapuje <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> není namapována.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> mapuje <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> na hostovaného ovládacího prvku <xref:System.Drawing.Font?displayProperty=nameWithType>|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti je převést na odpovídající <xref:System.Drawing.Font>. Když se změní jednu z těchto vlastností, nový <xref:System.Drawing.Font> se vytvoří. Pro <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> je zakázaná. Pro <xref:System.Windows.FontStyles.Italic%2A> nebo <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> je povolená.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> na hostovaného ovládacího prvku <xref:System.Drawing.Font?displayProperty=nameWithType>|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti je převést na odpovídající <xref:System.Drawing.Font>. Když se změní jednu z těchto vlastností, nový <xref:System.Drawing.Font> se vytvoří. Pro <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>, nebo <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> je povolená. Pro <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>, nebo <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> je zakázaná.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Sada [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti je převést na odpovídající <xref:System.Drawing.Font>. Když se změní jednu z těchto vlastností, nový <xref:System.Drawing.Font> se vytvoří. Hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídit změny velikosti na základě velikosti písma.<br /><br /> Velikost písma v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vyjádřena jako jedna devadesát čtvrtinu, šestinu palce a v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] jako jedna sekunda sedmdesáti palce. Odpovídající převod je:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] velikost písma = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] velikost písma * 72.0 / 96.0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Foreground%2A> Mapování vlastností se provádí pomocí následujících pravidel:<br /><br /> -Pokud <xref:System.Windows.Controls.Control.Foreground%2A> je <xref:System.Windows.Media.SolidColorBrush>, použijte <xref:System.Windows.Media.SolidColorBrush.Color%2A> pro <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Pokud <xref:System.Windows.Controls.Control.Foreground%2A> je <xref:System.Windows.Media.GradientBrush>, použít barvu <xref:System.Windows.Media.GradientStop> s nejnižší hodnota posunu <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />– U kteréhokoli jiného <xref:System.Windows.Media.Brush> zadejte, ponechte <xref:System.Windows.Forms.Control.ForeColor%2A> beze změny. To znamená, že je použita výchozí hodnota.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Při <xref:System.Windows.UIElement.IsEnabled%2A> nastavena, <xref:System.Windows.Forms.Integration.WindowsFormsHost> nastaví element <xref:System.Windows.Forms.Control.Enabled%2A> vlastnosti hostovaného ovládacího prvku.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Všechny čtyři hodnoty <xref:System.Windows.Forms.Control.Padding%2A> vlastnost na hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek se nastaví na stejnou <xref:System.Windows.Thickness> hodnotu.<br /><br /> -Hodnoty větší než <xref:System.Int32.MaxValue> jsou nastaveny na <xref:System.Int32.MaxValue>.<br />-Hodnoty menší než <xref:System.Int32.MinValue> jsou nastaveny na <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  `true`. Hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] je ovládací prvek viditelný. Explicitním nastavením <xref:System.Windows.Forms.Control.Visible%2A> vlastnost na hostovaný ovládací prvek `false` se nedoporučuje.<br />-   <xref:System.Windows.Visibility.Collapsed> mapuje <xref:System.Windows.Forms.Control.Visible%2A>  =  `true` nebo `false`. Hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není vykresleno ovládacího prvku a jeho oblast je sbalené.<br />-   <xref:System.Windows.Visibility.Hidden> : Hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zabírá místo v rozložení ovládacího prvku, ale není viditelný. V takovém případě <xref:System.Windows.Forms.Control.Visible%2A> je nastavena na `true`. Explicitním nastavením <xref:System.Windows.Forms.Control.Visible%2A> vlastnost na hostovaný ovládací prvek `false` se nedoporučuje.|  
  
 Připojené vlastnosti na prvky kontejneru jsou plně podporovány <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu.  
  
 Další informace najdete v tématu [názorný postup: Mapování vlastností použitím elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Aktualizace vlastnosti nadřazené  
 Změny vlastnosti většina nadřazené způsobit oznámení hostované podřízený ovládací prvek. Následující seznam popisuje vlastnosti, které nezpůsobí oznámení, když se změní jejich hodnoty.  
  
-   <xref:System.Windows.Controls.Control.Background%2A>  
  
-   <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
-   <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
-   <xref:System.Windows.UIElement.Visibility%2A>  
  
 Například, pokud změníte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Forms.Integration.WindowsFormsHost> elementu, <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost ovládacího prvku prostředí se nemění.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mapování vlastností pomocí ovládacího prvku ElementHost  
 Následující vlastnosti poskytují oznámení o změně integrované. Nevolejte <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> metoda při mapování těchto vlastností:  
  
-   AutoSize  
  
-   BackColor  
  
-   BackgroundImage  
  
-   BackgroundImageLayout  
  
-   BindingContext  
  
-   Vlastnosti CausesValidation  
  
-   ContextMenu  
  
-   ContextMenuStrip  
  
-   Kurzor  
  
-   Ukotvení  
  
-   Povoleno  
  
-   Písma  
  
-   ForeColor  
  
-   Umístění  
  
-   Okraj  
  
-   Padding  
  
-   Nadřazené  
  
-   Oblast  
  
-   RightToLeft  
  
-   Velikost  
  
-   TabIndex  
  
-   TabStop  
  
-   Text  
  
-   Viditelné  
  
 <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek přeloží výchozí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vlastnosti k jejich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty pomocí následující tabulky překladu.  
  
 Další informace najdete v tématu [názorný postup: Mapování vlastností použitím ovládacího prvku ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hostující formuláře Windows|Windows Presentation Foundation|Chování vzájemné spolupráce|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaný prvek|Nastavení této vlastnosti donutí repaint s <xref:System.Windows.Media.ImageBrush>. Pokud <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> je nastavena na `false` (výchozí hodnota), to <xref:System.Windows.Media.ImageBrush> vychází vzhled <xref:System.Windows.Forms.Integration.ElementHost> řídit, včetně jeho <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> vlastnosti a všechny připojené Malování obslužné rutiny.<br /><br /> Pokud <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> je nastavena na `true`, <xref:System.Windows.Media.ImageBrush> vychází vzhled <xref:System.Windows.Forms.Integration.ElementHost> nadřazeného ovládacího prvku, včetně nadřazeného objektu <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> vlastnosti a všechny připojené Malování obslužné rutiny.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaný prvek|Nastavení této vlastnosti způsobí, že stejné chování popsaných <xref:System.Windows.Forms.Control.BackColor%2A> mapování.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) na hostovaný prvek|Nastavení této vlastnosti způsobí, že stejné chování popsaných <xref:System.Windows.Forms.Control.BackColor%2A> mapování.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Standardní kurzoru se přeloží na odpovídající [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] standardní kurzoru. Pokud [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není standardní kurzoru, výchozí hodnota je přiřazen.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Při <xref:System.Windows.Forms.Control.Enabled%2A> je nastavena <xref:System.Windows.Forms.Integration.ElementHost> řídit sady <xref:System.Windows.UIElement.IsEnabled%2A> vlastnosti hostované prvku.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A> Hodnota je převést na odpovídající sadu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností písma.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> na hostovaný – element|Pokud <xref:System.Drawing.Font.Bold%2A> je `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> je nastavena na <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Pokud <xref:System.Drawing.Font.Bold%2A> je `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> je nastavena na <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> na hostovaný – element|Pokud <xref:System.Drawing.Font.Italic%2A> je `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> je nastavena na <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Pokud <xref:System.Drawing.Font.Italic%2A> je `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> je nastavena na <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> na hostovaný – element|Platí pouze při hostování <xref:System.Windows.Controls.TextBlock> ovládacího prvku.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> na hostovaný – element|Platí pouze při hostování <xref:System.Windows.Controls.TextBlock> ovládacího prvku.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> mapuje <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> mapuje <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Integration.ElementHost> Řídit sad <xref:System.Windows.UIElement.Visibility%2A> vlastnosti hostované elementu s použitím následujících pravidel:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` mapuje <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` mapuje <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
- [Vzájemná spolupráce subsystémů WPF a Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)
- [Návod: Mapování vlastností použitím elementu WindowsFormsHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Návod: Mapování vlastností použitím ovládacího prvku ElementHost](../../../../docs/framework/wpf/advanced/walkthrough-mapping-properties-using-the-elementhost-control.md)
