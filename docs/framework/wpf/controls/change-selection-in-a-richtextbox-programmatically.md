---
title: Programová změna výběru v poli RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
ms.openlocfilehash: b8acfe7cde1fe5dae96cd6324f75c5b146be9ec9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096222"
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="0ecee-102">Programová změna výběru v poli RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0ecee-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="0ecee-103">Tento příklad ukazuje, jak programově změnit v aktuálním výběru <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="0ecee-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="0ecee-104">Tento výběr je stejný, jako by uživatel měl vybraný obsah pomocí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ecee-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ecee-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ecee-105">Example</span></span>  
 <span data-ttu-id="0ecee-106">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje pojmenovaná <xref:System.Windows.Controls.RichTextBox> ovládacího prvku s jednoduchým obsahem.</span><span class="sxs-lookup"><span data-stu-id="0ecee-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="0ecee-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ecee-107">Example</span></span>  
 <span data-ttu-id="0ecee-108">Následující kód programově vybere libovolný text, když uživatel klikne v <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="0ecee-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0ecee-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ecee-109">See also</span></span>

- [<span data-ttu-id="0ecee-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="0ecee-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="0ecee-111">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="0ecee-111">TextBox Overview</span></span>](textbox-overview.md)
