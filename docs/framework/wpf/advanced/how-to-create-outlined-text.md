---
title: 'Postupy: Vytvoření textu osnovy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278922"
---
# <a name="how-to-create-outlined-text"></a>Postup: Vytvoření textu s obrysy

Ve většině případů při přidávání ozdoby do textových řetězců v aplikaci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] používáte text z hlediska kolekce samostatných znaků nebo glyfů. Můžete například vytvořit stopu lineárního přechodu <xref:System.Windows.Controls.Control.Foreground%2A> a <xref:System.Windows.Controls.TextBox> aplikovat ji na vlastnost objektu. Když zobrazíte nebo upravíte textové pole, stopa lineárního přechodu se automaticky aplikuje na aktuální sadu znaků v textovém řetězci.  
  
 ![Text zobrazený s lineární modře přechodem](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 Můžete však také převést text na <xref:System.Windows.Media.Geometry> objekty, což vám umožní vytvářet další typy vizuálně bohatého textu. Můžete například vytvořit <xref:System.Windows.Media.Geometry> objekt založený na obrysu textového řetězce.  
  
 ![Obrys textu pomocí stopy lineárního přechodu](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Když je text převeden <xref:System.Windows.Media.Geometry> na objekt, už se nejedná o kolekci znaků – znaky v textovém řetězci nelze měnit. Vzhled převedeného textu však můžete ovlivnit úpravou jeho vlastností tahu a výplně. Tah odkazuje na obrys převedeného textu; výplň odkazuje na oblast uvnitř obrysu převedeného textu.  
  
 Následující příklady ilustrují několik způsobů vytváření vizuálních efektů úpravou tahu a výplně převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Text s obrazovou stopou aplikovanou na tah](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Je také možné upravit obdélník ohraničovacího rámečku nebo zvýraznění převedeného textu. Následující příklad ilustruje způsob, jak vytvořit vizuální efekty úpravou tahu a zvýraznění převedeného textu.  
  
 ![Text s obrazovou stopou aplikovanou na tah a zvýraznění](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Příklad  
 Klíčem k převodu textu <xref:System.Windows.Media.Geometry> na objekt <xref:System.Windows.Media.FormattedText> je použití objektu. Po vytvoření tohoto objektu můžete <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> použít <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody a k <xref:System.Windows.Media.Geometry> převodu textu na objekty. První metoda vrátí geometrii formátovaného textu; druhá metoda vrátí geometrii ohraničovacího rámečku formátovaného textu. Následující příklad kódu ukazuje, <xref:System.Windows.Media.FormattedText> jak vytvořit objekt a načíst geometrie formátovaného textu a jeho ohraničovacího rámečku.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Chcete-li zobrazit načtené <xref:System.Windows.Media.Geometry> objekty, musíte <xref:System.Windows.Media.DrawingContext> získat přístup k objektu, který zobrazuje převedený text. V těchto příkladech kódu je tento přístup dosažen vytvořením vlastního objektu ovládacího prvku, který je odvozen z třídy, která podporuje uživatelem definované vykreslování.  
  
 Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty ve vlastním ovládacím prvku, zadejte přepsání <xref:System.Windows.UIElement.OnRender%2A> metody. Vaše potlačená metoda <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> by měla <xref:System.Windows.Media.Geometry> použít metodu k nakreslení objektů.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Zdroj ukázkového objektu vlastního uživatelského ovládacího prvku naleznete [v tématu OutlineTextControl.cs pro c#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) a [outlineTextControl.vb pro jazyk Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).
  
## <a name="see-also"></a>Viz také

- [Kreslení formátovaného textu](drawing-formatted-text.md)
