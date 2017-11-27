---
title: "Postupy: Odkazování na člena výčtu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4e6eb9c011095c6cf0abe1ee3ac7a68f156f01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="1ddf5-102">Postupy: Odkazování na člena výčtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ddf5-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="1ddf5-103">Výčty poskytují pohodlný způsob pro práci se sadami související konstanty a přidružení konstantních hodnot k názvy.</span><span class="sxs-lookup"><span data-stu-id="1ddf5-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="1ddf5-104">Můžete například deklarovat výčet sady konstanty typu integer, které jsou přidružené k dny v týdnu a pak použít názvy dnů, nikoli jejich celočíselné hodnoty v kódu.</span><span class="sxs-lookup"><span data-stu-id="1ddf5-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="1ddf5-105">Nepoužívejte plně kvalifikované názvy se `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1ddf5-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="1ddf5-106">Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="1ddf5-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="1ddf5-107">K odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="1ddf5-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="1ddf5-108">Název člena s výčtu kvalifikaci.</span><span class="sxs-lookup"><span data-stu-id="1ddf5-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="1ddf5-109">Například následující příklad přiřadí `Saturday` členem `FirstDayOfWeek` výčtu proměnnou `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="1ddf5-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1ddf5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ddf5-110">See Also</span></span>  
 [<span data-ttu-id="1ddf5-111">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="1ddf5-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="1ddf5-112">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="1ddf5-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="1ddf5-113">Postupy: iterace výčet v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ddf5-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="1ddf5-114">Postupy: určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="1ddf5-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="1ddf5-115">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="1ddf5-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
