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
ms.openlocfilehash: 2eff66377a3ba9b0e30417cc7dd1e1413d9074d9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369926"
---
# <a name="expander-overview"></a>Přehled rozšíření
<xref:System.Windows.Controls.Expander> Ovládacího prvku poskytuje způsob, jak zadat obsah v rozšiřitelné oblasti, která se podobá okno a obsahuje hlavičku.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Vytvoření jednoduché rozšíření  
 Následující příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Controls.Expander> ovládacího prvku. Tento příklad vytvoří <xref:System.Windows.Controls.Expander> vypadá podobně jako na předchozím obrázku.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> a <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> ze <xref:System.Windows.Controls.Expander> může také obsahovat například složitým obsahem <xref:System.Windows.Controls.RadioButton> a <xref:System.Windows.Controls.Image> objekty.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Nastavení směr rozbalení oblast obsahu  
 Můžete nastavit oblast obsahu <xref:System.Windows.Controls.Expander> ovládacího prvku v jednom ze čtyř směrů (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, nebo <xref:System.Windows.Controls.ExpandDirection.Right>) s použitím <xref:System.Windows.Controls.ExpandDirection> vlastnost. Když oblasti obsahu je sbalena, pouze <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a zobrazí jeho přepínacího tlačítka. A <xref:System.Windows.Controls.Button> ovládací prvek, který zobrazí směrové šipky se používá jako přepínací tlačítko pro rozbalení a sbalení oblasti obsahu. Po rozbalení <xref:System.Windows.Controls.Expander> pokusí zobrazit veškerý jeho obsah v oblasti jako okna.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Řízení velikosti rozšíření v panelu  
 Pokud <xref:System.Windows.Controls.Expander> je ovládací prvek uvnitř rozložení ovládacího prvku, který dědí z <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.StackPanel>, nezadávejte <xref:System.Windows.FrameworkElement.Height%2A> na <xref:System.Windows.Controls.Expander> při <xref:System.Windows.Controls.Expander.ExpandDirection%2A> je nastavena na <xref:System.Windows.Controls.ExpandDirection.Down> nebo <xref:System.Windows.Controls.ExpandDirection.Up>. Podobně, nezadávejte <xref:System.Windows.FrameworkElement.Width%2A> na <xref:System.Windows.Controls.Expander> při <xref:System.Windows.Controls.Expander.ExpandDirection%2A> je nastavena na <xref:System.Windows.Controls.ExpandDirection.Left> nebo <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Pokud nastavíte velikost dimenze na <xref:System.Windows.Controls.Expander> ovládacího prvku ve směru, rozšířené obsah se zobrazí, <xref:System.Windows.Controls.Expander> přebírá řízení oblasti, která používá obsah a zobrazí ohraničení kolem něj. I když je sbalený obsah zobrazí ohraničení. Chcete-li nastavit velikost rozšířené oblasti obsahu, nastavte rozměry na obsah <xref:System.Windows.Controls.Expander>, nebo pokud chcete, aby posouvání na funkce, které se <xref:System.Windows.Controls.ScrollViewer> , který obklopuje obsah.  
  
 Když <xref:System.Windows.Controls.Expander> ovládací prvek je po posledním prvku v <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] automaticky nastaví <xref:System.Windows.Controls.Expander> dimenze na zbývající části <xref:System.Windows.Controls.DockPanel>. Chcete-li toto výchozí chování zakázat, nastavte <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> vlastnost <xref:System.Windows.Controls.DockPanel> objektu `false`, nebo zajistěte, aby <xref:System.Windows.Controls.Expander> není po posledním prvku v <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Vytváření Posouvatelným obsahem  
 Pokud obsah je příliš velký pro velikost oblasti obsahu, můžete zabalit obsah <xref:System.Windows.Controls.Expander> v <xref:System.Windows.Controls.ScrollViewer> negace posouvatelným obsahem. <xref:System.Windows.Controls.Expander> Ovládací prvek automaticky neposkytuje funkce umožňující posouvání. Následující ilustrace ukazuje <xref:System.Windows.Controls.Expander> ovládací prvek, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.  
  
 **Rozšíření v prvku ScrollViewer**  
  
 ![Rozšíření s posuvník](./media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Když umístíte <xref:System.Windows.Controls.Expander> v ovládacím prvku <xref:System.Windows.Controls.ScrollViewer>, nastavte <xref:System.Windows.Controls.ScrollViewer> dimenze vlastnost, která odpovídá směr, ve kterém <xref:System.Windows.Controls.Expander> otevře obsah na velikost <xref:System.Windows.Controls.Expander> obsahu oblasti. Například, pokud jste nastavili <xref:System.Windows.Controls.Expander.ExpandDirection%2A> vlastnost <xref:System.Windows.Controls.Expander> k <xref:System.Windows.Controls.ExpandDirection.Down> (oblasti obsahu otevře dolů), nastavit <xref:System.Windows.FrameworkElement.Height%2A> vlastnost <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku na požadované výšku oblasti obsahu. Pokud nastavíte dimenze výšce místo na samotný, obsah <xref:System.Windows.Controls.ScrollViewer> nerozpozná toto nastavení a proto neposkytuje posouvatelným obsahem.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander> ovládací prvek, který se složitým obsahem, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. Tento příklad vytvoří <xref:System.Windows.Controls.Expander> , který je jako na obrázku na začátku tohoto oddílu.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Pomocí vlastností zarovnání  
 Je možné zarovnat obsah tak, že nastavíte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.Expander> ovládacího prvku. Při nastavování těchto vlastností zarovnání platí pro hlavičku a také rozšířené obsah.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Témata s postupy](expander-how-to-topics.md)
