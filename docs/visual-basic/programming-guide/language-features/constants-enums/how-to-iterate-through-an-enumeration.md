---
title: 'Postupy: Iterace ve výčtu jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646575"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="6b1e9-102">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b1e9-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="6b1e9-103">Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy.</span><span class="sxs-lookup"><span data-stu-id="6b1e9-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="6b1e9-104">K iteraci v rámci výčet, můžete jej přesunout do pole pomocí <xref:System.Enum.GetValues%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="6b1e9-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="6b1e9-105">Můžete také iterovat k výčtu pomocí `For...Each` příkaz, pomocí <xref:System.Enum.GetNames%2A> nebo <xref:System.Enum.GetValues%2A> Metoda získání řetězec nebo číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6b1e9-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="6b1e9-106">K iteraci v rámci výčet</span><span class="sxs-lookup"><span data-stu-id="6b1e9-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="6b1e9-107">Deklarace pole a převést jej s výčtu <xref:System.Enum.GetValues%2A> metody před předáním pole jako jste by jakoukoli jinou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6b1e9-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="6b1e9-108">Následující příklad zobrazí každý člen výčtu <xref:Microsoft.VisualBasic.FirstDayOfWeek> jako iteruje v rámci výčtu.</span><span class="sxs-lookup"><span data-stu-id="6b1e9-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6b1e9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b1e9-109">See Also</span></span>  
 [<span data-ttu-id="6b1e9-110">Přehled výčtů</span><span class="sxs-lookup"><span data-stu-id="6b1e9-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="6b1e9-111">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="6b1e9-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="6b1e9-112">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="6b1e9-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="6b1e9-113">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="6b1e9-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="6b1e9-114">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="6b1e9-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="6b1e9-115">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="6b1e9-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="6b1e9-116">Pole</span><span class="sxs-lookup"><span data-stu-id="6b1e9-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
