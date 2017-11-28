---
title: "Přehled rozšíření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff0a4432f6de8458e89132bbf46bab7568a04b60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="expander-overview"></a>Přehled rozšíření
<xref:System.Windows.Controls.Expander> Řízení poskytuje způsob pro poskytování obsahu v rozšíření oblasti, která vypadá přibližně takto: okno a obsahuje hlavičku.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Vytvoření jednoduchého Expander  
 Následující příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Controls.Expander> ovládacího prvku. Tento příklad vytvoří <xref:System.Windows.Controls.Expander> vypadá podobně jako na předchozím obrázku.  
  
 [!code-xaml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> a <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> z <xref:System.Windows.Controls.Expander> může také obsahovat například složitým obsahem <xref:System.Windows.Controls.RadioButton> a <xref:System.Windows.Controls.Image> objekty.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Nastavení směr zvětšující oblast obsahu  
 Můžete nastavit oblasti obsahu <xref:System.Windows.Controls.Expander> řízení rozbalte v jedné ze čtyř směrů (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, nebo <xref:System.Windows.Controls.ExpandDirection.Right>) pomocí <xref:System.Windows.Controls.ExpandDirection> vlastnost. Pokud oblast obsahu sbalena, jenom <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a jeho přepínací tlačítko zobrazit. A <xref:System.Windows.Controls.Button> ovládací prvek, který zobrazí směrové šipky slouží jako přepínač k rozbalit nebo sbalit oblast obsahu. Po rozbalení <xref:System.Windows.Controls.Expander> pokusí zobrazit veškerý jeho obsah v oblasti jako okno.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Řízení velikosti Expander panelu  
 Pokud <xref:System.Windows.Controls.Expander> ovládací prvek nachází v ovládacím prvku rozložení, který dědí z <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.StackPanel>, nezadávejte <xref:System.Windows.FrameworkElement.Height%2A> na <xref:System.Windows.Controls.Expander> při <xref:System.Windows.Controls.Expander.ExpandDirection%2A> je nastavena na <xref:System.Windows.Controls.ExpandDirection.Down> nebo <xref:System.Windows.Controls.ExpandDirection.Up>. Podobně, nezadávejte <xref:System.Windows.FrameworkElement.Width%2A> na <xref:System.Windows.Controls.Expander> při <xref:System.Windows.Controls.Expander.ExpandDirection%2A> je nastavena na <xref:System.Windows.Controls.ExpandDirection.Left> nebo <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Když nastavíte na dimenzi velikost <xref:System.Windows.Controls.Expander> ovládacího prvku ve směru, zobrazí se rozšířené obsah, <xref:System.Windows.Controls.Expander> přebírá řízení k oblasti, která je používána obsah a zobrazí ohraničení kolem něj. I když je obsah sbalený ukazuje ohraničení. Velikost rozšířené oblasti obsahu, nastavit velikost dimenze na obsah <xref:System.Windows.Controls.Expander>, nebo pokud chcete posouvání funkce, které se na <xref:System.Windows.Controls.ScrollViewer> která obklopuje obsah.  
  
 Když <xref:System.Windows.Controls.Expander> ovládací prvek je posledním prvkem v <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] automaticky nastaví <xref:System.Windows.Controls.Expander> dimenze na zbývající oblasti <xref:System.Windows.Controls.DockPanel>. Abyste zabránili toto výchozí chování, nastavte <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> vlastnost <xref:System.Windows.Controls.DockPanel> do objektu `false`, nebo zkontrolujte, zda <xref:System.Windows.Controls.Expander> není posledním prvkem v <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Vytváření Posouvatelným obsahem  
 Pokud obsah je příliš velké vzhledem k velikosti oblasti obsahu, může obtékat obsah <xref:System.Windows.Controls.Expander> v <xref:System.Windows.Controls.ScrollViewer> Chcete-li poskytovat posouvatelným obsahem. <xref:System.Windows.Controls.Expander> Řízení neposkytuje automaticky posouvání schopnosti. Následující obrázek znázorňuje <xref:System.Windows.Controls.Expander> ovládací prvek, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.  
  
 **Expander v ScrollViewer**  
  
 ![Rozšíření s ScrollBar](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Když umístíte <xref:System.Windows.Controls.Expander> řídit ve <xref:System.Windows.Controls.ScrollViewer>, nastavte <xref:System.Windows.Controls.ScrollViewer> dimenze vlastnost, která odpovídá směr, ve kterém <xref:System.Windows.Controls.Expander> obsah otevře na velikost <xref:System.Windows.Controls.Expander> obsahu, oblasti. Například pokud nastavíte <xref:System.Windows.Controls.Expander.ExpandDirection%2A> vlastnost na <xref:System.Windows.Controls.Expander> k <xref:System.Windows.Controls.ExpandDirection.Down> (oblast obsahu otevře dolů), nastavte <xref:System.Windows.FrameworkElement.Height%2A> vlastnost na <xref:System.Windows.Controls.ScrollViewer> ovládací prvek na požadované výšku oblasti obsahu. Pokud nastavíte dimenzi výšky místo na sebe, obsah <xref:System.Windows.Controls.ScrollViewer> nerozpoznává toto nastavení a proto nenabízí posouvatelným obsahem.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander> ovládací prvek, který má složitý obsah, který obsahuje <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku. Tento příklad vytvoří <xref:System.Windows.Controls.Expander> se jako na obrázku na začátku této části.  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Pomocí vlastností zarovnání  
 Obsah můžete zarovnat nastavením <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.Expander> ovládacího prvku. Při nastavení těchto vlastností zarovnání platí pro hlavičku a také rozšířené obsah.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Expander>  
 <xref:System.Windows.Controls.ExpandDirection>  
 [Postupy: témata](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
