---
title: Přehled rozšíření
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187115"
---
# <a name="expander-overview"></a>Přehled rozšíření
Ovládací <xref:System.Windows.Controls.Expander> prvek poskytuje způsob, jak poskytnout obsah v rozbalitelné oblasti, která se podobá okno a obsahuje záhlaví.  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>Vytvoření jednoduchého expandéru  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Expander> vytvořit jednoduchý ovládací prvek. Tento příklad <xref:System.Windows.Controls.Expander> vytvoří, který vypadá jako předchozí ilustrace.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 A <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a <xref:System.Windows.Controls.Expander> může také obsahovat komplexní <xref:System.Windows.Controls.RadioButton> <xref:System.Windows.Controls.Image> obsah, jako jsou a objekty.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Nastavení směru rozbalovací oblasti obsahu  
 Pomocí <xref:System.Windows.Controls.ExpandDirection> vlastnosti můžete nastavit <xref:System.Windows.Controls.Expander> oblast obsahu ovládacího prvku<xref:System.Windows.Controls.ExpandDirection.Down>tak, <xref:System.Windows.Controls.ExpandDirection.Left>aby <xref:System.Windows.Controls.ExpandDirection.Right>se rozbalila v jednom ze čtyř směrů ( , <xref:System.Windows.Controls.ExpandDirection.Up>, , nebo ). Když je oblast obsahu sbalená, zobrazí se pouze <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> přepínací tlačítko a a. Ovládací <xref:System.Windows.Controls.Button> prvek, který zobrazuje směrovou šipku, se používá jako přepínací tlačítko pro rozbalení nebo sbalení oblasti obsahu. Po rozbalení <xref:System.Windows.Controls.Expander> se pokusí zobrazit veškerý obsah v oblasti podobné oknu.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Ovládání velikosti expandéru v panelu  
 Pokud <xref:System.Windows.Controls.Expander> je ovládací prvek uvnitř ovládacího <xref:System.Windows.Controls.Panel>prvku <xref:System.Windows.Controls.StackPanel>rozložení, který <xref:System.Windows.FrameworkElement.Height%2A> dědí <xref:System.Windows.Controls.Expander> z <xref:System.Windows.Controls.Expander.ExpandDirection%2A> , například , nezadávejte na při vlastnosti je nastavena <xref:System.Windows.Controls.ExpandDirection.Down> na nebo <xref:System.Windows.Controls.ExpandDirection.Up>. Podobně nezadávejte na <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.Controls.Expander> když <xref:System.Windows.Controls.Expander.ExpandDirection%2A> je vlastnost nastavena na <xref:System.Windows.Controls.ExpandDirection.Left> nebo <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Pokud nastavíte rozměrovou <xref:System.Windows.Controls.Expander> dimenzi ovládacího prvku ve směru, <xref:System.Windows.Controls.Expander> ve které je zobrazen rozbalené holce, převezme kontrolu nad oblastí, která je obsahem používána, a zobrazí kolem něj ohraničení. Ohraničení se zobrazí i při sbalení obsahu. Chcete-li nastavit velikost rozšířené oblasti obsahu, nastavte rozměry <xref:System.Windows.Controls.Expander>velikosti na obsah , nebo <xref:System.Windows.Controls.ScrollViewer> pokud chcete možnost posouvání, na které obklopuje obsah.  
  
 Pokud <xref:System.Windows.Controls.Expander> je ovládací prvek posledním <xref:System.Windows.Controls.DockPanel> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prvkem v <xref:System.Windows.Controls.Expander> aplikaci <xref:System.Windows.Controls.DockPanel>, automaticky nastaví kóty tak, aby se rovnaly zbývající ploše . Chcete-li <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> tomuto výchozímu chování <xref:System.Windows.Controls.DockPanel> zabránit, nastavte vlastnost objektu na `false`položku <xref:System.Windows.Controls.Expander> nebo se ujistěte, že se nejedná o poslední prvek v . <xref:System.Windows.Controls.DockPanel>  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>Vytváření rolovacího obsahu  
 Pokud je obsah příliš velký pro velikost oblasti obsahu, můžete <xref:System.Windows.Controls.Expander> zalomit obsah v za účelem <xref:System.Windows.Controls.ScrollViewer> poskytnutí rolovacího obsahu. Ovládací <xref:System.Windows.Controls.Expander> prvek neposkytuje automaticky možnost posouvání. Následující obrázek <xref:System.Windows.Controls.Expander> znázorňuje <xref:System.Windows.Controls.ScrollViewer> ovládací prvek, který obsahuje ovládací prvek.  
  
 **Expander v ScrollViewer**  
  
 ![Snímek obrazovky, který zobrazuje rozbalovací panel s posuvníkem](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Když umístíte <xref:System.Windows.Controls.Expander> ovládací <xref:System.Windows.Controls.ScrollViewer>prvek do <xref:System.Windows.Controls.ScrollViewer> aplikace , nastavte vlastnost dimenze, <xref:System.Windows.Controls.Expander> která odpovídá směru, <xref:System.Windows.Controls.Expander> ve kterém se obsah otevírá velikosti oblasti obsahu. Pokud například nastavíte <xref:System.Windows.Controls.Expander.ExpandDirection%2A> vlastnost <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.ExpandDirection.Down> na to (oblast obsahu <xref:System.Windows.FrameworkElement.Height%2A> se otevře <xref:System.Windows.Controls.ScrollViewer> dolů), nastavte vlastnost ovládacího prvku na požadovanou výšku pro oblast obsahu. Pokud místo toho nastavíte rozměr <xref:System.Windows.Controls.ScrollViewer> výšky na samotném obsahu, nerozpozná toto nastavení, a proto neposkytuje rolovací obsah.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Expander> vytvořit ovládací prvek, který <xref:System.Windows.Controls.ScrollViewer> má komplexní obsah a který obsahuje ovládací prvek. Tento příklad <xref:System.Windows.Controls.Expander> vytvoří, který je jako ilustrace na začátku tohoto oddílu.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>Použití vlastností trasy  
 Obsah můžete zarovnat <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> nastavením <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastností ovládacího <xref:System.Windows.Controls.Expander> prvku. Když nastavíte tyto vlastnosti, zarovnání se vztahuje na záhlaví a také na rozbalené ho.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Témata s postupy](expander-how-to-topics.md)
