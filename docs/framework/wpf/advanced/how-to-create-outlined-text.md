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
ms.openlocfilehash: a06ef9adbd5740fee74be2e9d8d13a8a5bdc5b95
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521475"
---
# <a name="how-to-create-outlined-text"></a>Postupy: Vytvoření textu osnovy
Ve většině případů při přidávání dekoru na textové řetězce do vaší [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, používáte text z hlediska kolekce samostatných znaky nebo glyfů. Například lze vytvořit štětec lineárního přechodu a použít ho k <xref:System.Windows.Controls.Control.Foreground%2A> vlastnost <xref:System.Windows.Controls.TextBox> objektu. Při zobrazení nebo upravte pole štětec lineárního přechodu se automaticky využije na aktuální sady znaků v textovém řetězci.  
  
 ![Text zobrazený s štětec lineárního přechodu](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")  
Příklad štětec lineárního přechodu u textového pole  
  
 Ale můžete také převést text do <xref:System.Windows.Media.Geometry> objektům, umožňuje vytvářet jiné druhy vizuálně formátovaný text. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrysu textového řetězce.  
  
 ![Text osnovy pomocí štětec lineárního přechodu](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Příklad štětec lineárního přechodu u geometrie obrysu textu  
  
 Pokud je text převést na <xref:System.Windows.Media.Geometry> objektu, není již sadu znaků – nelze upravit znaků v textovém řetězci. Můžete však vliv na vzhled text převedený úpravou jeho vlastností tahu a výplně. Protože byl zdvih odkazuje na osnovy převedený textu. Výplň odkazuje na oblast uvnitř osnovy text převedený.  
  
 Následující příklady znázorňují několik způsobů vytváření vizuálních efektů úpravou tahu a zadejte text převedený.  
  
 ![Text mají různé barvy výplně a stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Příklad nastavení tahu a výplně různé barvy  
  
 ![Text s obrázkový štětec u stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Příklad obrázkový štětec u tahu  
  
 Je také možné změnit ohraničující obdélník pole nebo zvýraznění převedeného textu. Následující příklad ukazuje způsob, jak vytváření vizuálních efektů úpravou tahu a zvýraznit text převedený.  
  
 ![Text s obrázkový štětec u stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Příklad obrázkový štětec, který je použitý ke stroke a zvýraznění  
  
## <a name="example"></a>Příklad  
 Klíč k převodu textu <xref:System.Windows.Media.Geometry> objektu je použití <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření tohoto objektu můžete použít <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> a <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> metody pro převod textu na <xref:System.Windows.Media.Geometry> objekty. První metoda vrátí geometrie formátovaného textu. Druhá metoda vrátí geometrie formátovaný text ohraničovacího rámečku. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Media.FormattedText> objektu a k načtení geometrie formátovaný text a jeho ohraničujícího rámečku.  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 Aby bylo možné zobrazit načtené <xref:System.Windows.Media.Geometry> objekty, budete potřebovat přístup k <xref:System.Windows.Media.DrawingContext> objektu, který zobrazuje text převedený. V těchto příkladech kódu se provádí tak, že vytvoříte vlastní ovládací prvek objekt, který je odvozen ze třídy, která podporuje uživatelem definované vykreslování.  
  
 Chcete-li zobrazit <xref:System.Windows.Media.Geometry> objekty v ovládacím prvku vlastní poskytují přepsání pro <xref:System.Windows.UIElement.OnRender%2A> metody. Používejte přepsané metody <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> metody, chcete-li nakreslit <xref:System.Windows.Media.Geometry> objekty.  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  Zdrojový objekt příklad vlastního uživatelského ovládacího prvku, naleznete v tématu [OutlineTextControl.cs pro C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) a [OutlineTextControl.vb v jazyce Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb). 
  
## <a name="see-also"></a>Viz také:
- [Kreslení formátovaného textu](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
