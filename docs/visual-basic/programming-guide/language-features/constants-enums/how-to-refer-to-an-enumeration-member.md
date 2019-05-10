---
title: 'Postupy: Odkazování na člena výčtu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 000c7f8f87792b598f177cae123010eb8888c328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645966"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="6c38e-102">Postupy: Odkazování na člena výčtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c38e-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="6c38e-103">Výčty poskytují pohodlný způsob pro práci se sadami související s konstantami a přidružení konstantních hodnot s názvy.</span><span class="sxs-lookup"><span data-stu-id="6c38e-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="6c38e-104">Můžete třeba deklarovat výčet sady konstanty typu integer, které jsou spojené s dny v týdnu a potom použít názvy dní, namísto jejich celočíselných hodnot ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="6c38e-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="6c38e-105">Nepoužívejte plně kvalifikované názvy s `Imports` příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c38e-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="6c38e-106">Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="6c38e-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="6c38e-107">K odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="6c38e-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="6c38e-108">Kvalifikujte název člena výčtu.</span><span class="sxs-lookup"><span data-stu-id="6c38e-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="6c38e-109">Například následující příklad přiřadí `Saturday` člena `FirstDayOfWeek` výčet proměnné `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="6c38e-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="6c38e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c38e-110">See also</span></span>

- [<span data-ttu-id="6c38e-111">Postupy: Deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="6c38e-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="6c38e-112">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="6c38e-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="6c38e-113">Postupy: Iterace ve výčtu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c38e-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="6c38e-114">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="6c38e-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="6c38e-115">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="6c38e-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
