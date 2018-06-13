---
title: 'Postupy: Získání kolekce řádků z objektu TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 64187527da3cfb97343e2036338822d479dd997a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552737"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="94abe-102">Postupy: Získání kolekce řádků z objektu TextBox</span><span class="sxs-lookup"><span data-stu-id="94abe-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="94abe-103">Tento příklad ukazuje, jak získat kolekce řádků textu z <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="94abe-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94abe-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="94abe-104">Example</span></span>  
 <span data-ttu-id="94abe-105">Následující příklad ukazuje jednoduchý metody, která přijímá <xref:System.Windows.Controls.TextBox> jako argument a vrátí <xref:System.Collections.Specialized.StringCollection> obsahující řádků textu v **TextBox**.</span><span class="sxs-lookup"><span data-stu-id="94abe-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="94abe-106"><xref:System.Windows.Controls.TextBox.LineCount%2A> Vlastnost se používá k určení, kolik řádků se právě **TextBox**a <xref:System.Windows.Controls.TextBox.GetLineText%2A> metoda se pak používá k extrahování každého řádku a přidat jej do kolekce řádků.</span><span class="sxs-lookup"><span data-stu-id="94abe-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="94abe-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="94abe-107">See Also</span></span>  
 [<span data-ttu-id="94abe-108">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="94abe-108">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="94abe-109">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="94abe-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
