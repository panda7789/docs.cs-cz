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
ms.openlocfilehash: 5de1068401dac61c5de5b86604da9417e18a94ae
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125938"
---
# <a name="how-to-create-outlined-text"></a>Postupy: Vytvoření textu osnovy
Ve většině případů při přidávání dekoru na textové řetězce do vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, používáte text z hlediska kolekce samostatných znaky nebo glyfů. Například lze vytvořit štětec lineárního přechodu a použít ho k <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.TextBox> objektu. Při zobrazení nebo upravte pole štětec lineárního přechodu se automaticky využije na aktuální sady znaků v textovém řetězci.  
  
 ![Text zobrazený s štětec lineárního přechodu](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 Ale můžete také převést text do <xref:System.Windows.Media.Geometry> objektům, umožňuje vytvářet jiné druhy vizuálně formátovaný text. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrysu textového řetězce.  
  
 ![Text osnovy pomocí štětec lineárního přechodu](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 Pokud je text převést na <xref:System.Windows.Media.Geometry> objektu, není již sadu znaků – nelze upravit znaků v textovém řetězci. Můžete však vliv na vzhled text převedený úpravou jeho vlastností tahu a výplně. Protože byl zdvih odkazuje na osnovy převedený textu. Výplň odkazuje na oblast uvnitř osnovy text převedený.  
  
 Následující příklady znázorňují několik způsobů vytváření vizuálních efektů úpravou tahu a zadejte text převedený.  
  
 ![Text mají různé barvy výplně a tahu](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Text použitý pro stroke obrázkový štětec](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 Je také možné změnit ohraničující obdélník pole nebo zvýraznění převedeného textu. Následující příklad ukazuje způsob, jak vytváření vizuálních efektů úpravou tahu a zvýraznit text převedený.  
  
 ![Text s použita k obtažení a zvýraznit obrázkový štětec](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a>Příklad  
 Klíč k převodu textu <xref:System.Windows.Media.Geometry> objektu je použití <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření tohoto objektu můžete použít <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> a <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody pro převod textu na <xref:System.Windows.Media.Geometry> objekty. První metoda vrátí geometrie formátovaného textu. Druhá metoda vrátí geometrie formátovaný text ohraničovacího rámečku. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a k načtení geometrie formátovaný text a jeho ohraničujícího rámečku.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Aby bylo možné zobrazit načtené <xref:System.Windows.Media.Geometry> objekty, budete potřebovat přístup k <xref:System.Windows.Media.DrawingContext> objektu, který zobrazuje text převedený. V těchto příkladech kódu se provádí tak, že vytvoříte vlastní ovládací prvek objekt, který je odvozen ze třídy, která podporuje uživatelem definované vykreslování.  
  
 Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty v ovládacím prvku vlastní poskytují přepsání pro <xref:System.Windows.UIElement.OnRender%2A> metody. Používejte přepsané metody <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metody, chcete-li nakreslit <xref:System.Windows.Media.Geometry> objekty.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Zdrojový objekt příklad vlastního uživatelského ovládacího prvku, naleznete v tématu [OutlineTextControl.cs pro C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) a [OutlineTextControl.vb v jazyce Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb). 
  
## <a name="see-also"></a>Viz také:
- [Kreslení formátovaného textu](drawing-formatted-text.md)
