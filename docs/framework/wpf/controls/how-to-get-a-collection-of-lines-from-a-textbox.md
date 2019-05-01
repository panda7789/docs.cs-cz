---
title: 'Postupy: Získání kolekce řádků z prvku TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052479"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="78af0-102">Postupy: Získání kolekce řádků z prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="78af0-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="78af0-103">Tento příklad ukazuje, jak získání kolekce řádků z textu <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="78af0-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78af0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="78af0-104">Example</span></span>  
 <span data-ttu-id="78af0-105">Následující příklad ukazuje jednoduchý způsob, který přijímá <xref:System.Windows.Controls.TextBox> jako argument a vrátí <xref:System.Collections.Specialized.StringCollection> obsahující řádky textu v **TextBox**.</span><span class="sxs-lookup"><span data-stu-id="78af0-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="78af0-106"><xref:System.Windows.Controls.TextBox.LineCount%2A> Vlastnost se používá k určení, kolik řádků se v tuto chvíli **textového pole**a <xref:System.Windows.Controls.TextBox.GetLineText%2A> metoda se pak použije k extrakci každého řádku a přidat ho do kolekce řádků.</span><span class="sxs-lookup"><span data-stu-id="78af0-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="78af0-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78af0-107">See also</span></span>

- [<span data-ttu-id="78af0-108">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="78af0-108">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="78af0-109">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="78af0-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
