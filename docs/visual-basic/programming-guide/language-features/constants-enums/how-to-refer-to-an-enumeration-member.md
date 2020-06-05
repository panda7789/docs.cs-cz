---
title: 'Postupy: Odkazování na člena výčtu'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: 66c527bd4ba4721065de8fca8534fe652d0139be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414411"
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="2a35f-102">Postupy: Odkazování na člena výčtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a35f-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="2a35f-103">Výčty poskytují pohodlný způsob práce se sadami souvisejících konstant a k přidružení konstantních hodnot k názvům.</span><span class="sxs-lookup"><span data-stu-id="2a35f-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="2a35f-104">Můžete například deklarovat výčet pro sadu celočíselných konstant přidružených ke dnům v týdnu a potom použít názvy dnů, nikoli jejich celočíselné hodnoty ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="2a35f-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="2a35f-105">Můžete se vyhnout použití plně kvalifikovaného názvu s `Imports` příkazem.</span><span class="sxs-lookup"><span data-stu-id="2a35f-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="2a35f-106">Další informace naleznete v tématu [výčty a kvalifikace názvu](enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="2a35f-106">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="2a35f-107">Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="2a35f-107">To refer to an enumeration member</span></span>  
  
- <span data-ttu-id="2a35f-108">Kvalifikovat název člena s výčtem.</span><span class="sxs-lookup"><span data-stu-id="2a35f-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="2a35f-109">Například následující příklad přiřadí `Saturday` člena `FirstDayOfWeek` výčtu k proměnné `DayValue` .</span><span class="sxs-lookup"><span data-stu-id="2a35f-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="2a35f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a35f-110">See also</span></span>

- [<span data-ttu-id="2a35f-111">Postupy: deklarace výčtu</span><span class="sxs-lookup"><span data-stu-id="2a35f-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="2a35f-112">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="2a35f-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="2a35f-113">Postupy: Iterace ve výčtu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a35f-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="2a35f-114">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="2a35f-114">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="2a35f-115">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="2a35f-115">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
