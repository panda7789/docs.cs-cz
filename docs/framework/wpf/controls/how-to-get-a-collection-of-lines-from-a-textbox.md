---
title: 'Postupy: Získání kolekce řádků z objektu TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 1aa73e55a3fdfd658c6a337b598dff96244ace40
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354190"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="83acc-102">Postupy: Získání kolekce řádků z objektu TextBox</span><span class="sxs-lookup"><span data-stu-id="83acc-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="83acc-103">Tento příklad ukazuje, jak získání kolekce řádků z textu <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="83acc-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83acc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="83acc-104">Example</span></span>  
 <span data-ttu-id="83acc-105">Následující příklad ukazuje jednoduchý způsob, který přijímá <xref:System.Windows.Controls.TextBox> jako argument a vrátí <xref:System.Collections.Specialized.StringCollection> obsahující řádky textu v **TextBox**.</span><span class="sxs-lookup"><span data-stu-id="83acc-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="83acc-106"><xref:System.Windows.Controls.TextBox.LineCount%2A> Vlastnost se používá k určení, kolik řádků se v tuto chvíli **textového pole**a <xref:System.Windows.Controls.TextBox.GetLineText%2A> metoda se pak použije k extrakci každého řádku a přidat ho do kolekce řádků.</span><span class="sxs-lookup"><span data-stu-id="83acc-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="83acc-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83acc-107">See also</span></span>
- [<span data-ttu-id="83acc-108">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="83acc-108">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="83acc-109">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="83acc-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
