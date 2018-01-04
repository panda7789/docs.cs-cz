---
title: "Postupy: Načtení výběru textu"
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
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32be79811de4b8056449c2c6d6c53eca8cc063f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-a-text-selection"></a><span data-ttu-id="c252d-102">Postupy: Načtení výběru textu</span><span class="sxs-lookup"><span data-stu-id="c252d-102">How to: Retrieve a Text Selection</span></span>
<span data-ttu-id="c252d-103">Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.TextBox.SelectedText%2A> vlastnost k načtení textu, který uživatel vybral v <xref:System.Windows.Controls.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c252d-103">This example shows one way to use the <xref:System.Windows.Controls.TextBox.SelectedText%2A> property to retrieve text that the user has selected in a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c252d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c252d-104">Example</span></span>  
 <span data-ttu-id="c252d-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad zobrazuje definici <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje chcete vybrat, text a <xref:System.Windows.Controls.Button> ovládací prvek se zadaným <xref:System.Windows.Controls.Button.OnClick%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c252d-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example shows the definition of a <xref:System.Windows.Controls.TextBox> control that contains some text to select, and a <xref:System.Windows.Controls.Button> control with a specified <xref:System.Windows.Controls.Button.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="c252d-106">V tomto příkladu tlačítko s přiřazený <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události se používá k načtení výběr textu.</span><span class="sxs-lookup"><span data-stu-id="c252d-106">In this example, a button with an associated <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler is used to retrieve the text selection.</span></span> <span data-ttu-id="c252d-107">Když uživatel klikne na tlačítko <xref:System.Windows.Controls.Button.OnClick%2A> metoda zkopíruje všechny vybraný text do textového pole na řetězec.</span><span class="sxs-lookup"><span data-stu-id="c252d-107">When the user clicks the button, the <xref:System.Windows.Controls.Button.OnClick%2A> method copies any selected text in the textbox into a string.</span></span> <span data-ttu-id="c252d-108">Zvláštní okolnosti, které výběr textu je načíst (kliknutím na tlačítko), stejně jako akce s výběr (kopírování výběr textu na řetězec), můžete snadno upravit tak, aby dokázala pojmout širokou škálu scénářů.</span><span class="sxs-lookup"><span data-stu-id="c252d-108">The particular circumstances by which the text selection is retrieved (clicking a button), as well as the action taken with that selection (copying the text selection to a string), can easily be modified to accommodate a wide variety of scenarios.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a><span data-ttu-id="c252d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c252d-109">Example</span></span>  
 <span data-ttu-id="c252d-110">Následující [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] ukazuje příklad <xref:System.Windows.Controls.Button.OnClick%2A> obslužné rutiny události pro tlačítko definovaný v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="c252d-110">The following [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] example shows an <xref:System.Windows.Controls.Button.OnClick%2A> event handler for the button defined in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] for this example.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a><span data-ttu-id="c252d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c252d-111">See Also</span></span>  
 [<span data-ttu-id="c252d-112">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="c252d-112">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="c252d-113">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="c252d-113">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
