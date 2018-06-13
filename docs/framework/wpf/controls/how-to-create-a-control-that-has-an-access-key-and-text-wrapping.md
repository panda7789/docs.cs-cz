---
title: 'Postupy: Vytvoření ovládacího prvku obsahujícího přístupový klíč a zalamování textu'
ms.date: 03/30/2017
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
ms.openlocfilehash: 8343c660ddeb5487f46e87534e555936d1b86371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553780"
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>Postupy: Vytvoření ovládacího prvku obsahujícího přístupový klíč a zalamování textu
Tento příklad ukazuje postup vytvoření ovládacího prvku, který má přístupový klíč a podporuje zalamování textu. V příkladu se používá <xref:System.Windows.Controls.Label> ovládací prvek pro ilustraci tyto koncepty.  
  
## <a name="example"></a>Příklad  
 **Přidat do vaší popisek zalamování textu**  
  
 <xref:System.Windows.Controls.Label> Ovládací prvek nepodporuje zalamování textu. Pokud potřebujete zalomen na více řádcích štítek, můžete vnořovat jiné element, který podporuje text zabalení a umístí prvku v popisku. Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.TextBlock> aby štítek, který zahrnuje několik řádků textu.  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **Přidat přístupový klíč a zalamování textu na vaše štítek**  
  
 Pokud potřebujete <xref:System.Windows.Controls.Label> s přístupový klíč (symbol), použijte <xref:System.Windows.Controls.AccessText> element, který je uvnitř <xref:System.Windows.Controls.Label>.  
  
 Ovládací prvky jako například <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.Expander>, a <xref:System.Windows.Controls.GroupBox> žádné výchozí šablony ovládacího prvku. Tyto šablony obsahovat <xref:System.Windows.Controls.ContentPresenter>. Jedna z vlastností, které můžete nastavit <xref:System.Windows.Controls.ContentPresenter> je <xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>= "true", který můžete použít k určení přístupový klíč pro ovládací prvek.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Label> , který má přístupový klíč a podporuje zalamování textu. K povolení zalamování textu, v příkladu je nastavena <xref:System.Windows.Controls.AccessText.TextWrapping%2A> vlastnost a používá znak podtržení, které pokud chcete zadat přístupový klíč. (Znak, který následuje znak podtržení se přístupový klíč.)  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavte vlastnost Target tohoto štítku](http://msdn.microsoft.com/library/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
