---
title: 'Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 74dff310ccba0bebcf96576d769bf50420ca7397
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971686"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="dd3dd-102">Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd3dd-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="dd3dd-103"><xref:System.Enum.GetValues%2A> a <xref:System.Enum.GetNames%2A> metody umožňují určit řetězců a hodnot spojených s členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="dd3dd-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="dd3dd-104">K určení řetězce spojeného s výčet</span><span class="sxs-lookup"><span data-stu-id="dd3dd-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="dd3dd-105">Použití <xref:System.Enum.GetNames%2A> metody mají být načteny řetězce spojené s členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="dd3dd-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="dd3dd-106">V tomto příkladu deklaruje výčet, `flavorEnum`, použije <xref:System.Enum.GetNames%2A> metodu pro zobrazení řetězce přidružené k jednotlivým členům.</span><span class="sxs-lookup"><span data-stu-id="dd3dd-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dd3dd-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd3dd-107">See also</span></span>
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="dd3dd-108">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="dd3dd-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="dd3dd-109">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="dd3dd-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="dd3dd-110">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="dd3dd-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="dd3dd-111">Postupy: Iterace ve výčtu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd3dd-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="dd3dd-112">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="dd3dd-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="dd3dd-113">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="dd3dd-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
