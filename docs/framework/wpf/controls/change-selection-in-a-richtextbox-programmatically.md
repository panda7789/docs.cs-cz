---
title: "Programová změna výběru v poli RichTextBox"
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
- changing selections in a text box [WPF]
- changing selections in a RichTextBox [WPF]
ms.assetid: f1213205-1ad7-4cd2-b115-460173cc5aa3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f645a5719425742ba02f8f9056ca788fd6fdb931
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="change-selection-in-a-richtextbox-programmatically"></a><span data-ttu-id="f453d-102">Programová změna výběru v poli RichTextBox</span><span class="sxs-lookup"><span data-stu-id="f453d-102">Change Selection in a RichTextBox Programmatically</span></span>
<span data-ttu-id="f453d-103">Tento příklad ukazuje, jak programově změnit aktuální výběr v <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f453d-103">This example shows how to programmatically change the current selection in a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="f453d-104">Tato volba je stejný, jako by uživatel měl vybraný obsah pomocí uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f453d-104">This selection is the same as if the user had selected the content by using the user interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f453d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f453d-105">Example</span></span>  
 <span data-ttu-id="f453d-106">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje pojmenovaná <xref:System.Windows.Controls.RichTextBox> ovládacího prvku s jednoduchým obsahem.</span><span class="sxs-lookup"><span data-stu-id="f453d-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml#changeselectionprogrammaticalyexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="f453d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="f453d-107">Example</span></span>  
 <span data-ttu-id="f453d-108">Následující kód prostřednictvím kódu programu vybere libovolný text, když uživatel klikne uvnitř <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f453d-108">The following code programmatically selects some arbitrary text when the user clicks inside the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/ChangeSelectionProgrammaticaly.xaml.cs#changeselectionprogrammaticalycodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#ChangeSelectionProgrammaticalyCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/ChangeSelectionProgrammaticaly.xaml.vb#changeselectionprogrammaticalycodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f453d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="f453d-109">See Also</span></span>  
 [<span data-ttu-id="f453d-110">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="f453d-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="f453d-111">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="f453d-111">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
