---
title: Výčty a kvalifikace názvu
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347498"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="17372-102">Výčty a kvalifikace názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17372-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="17372-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span><span class="sxs-lookup"><span data-stu-id="17372-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="17372-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span><span class="sxs-lookup"><span data-stu-id="17372-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="17372-105">Using the Imports Statement</span><span class="sxs-lookup"><span data-stu-id="17372-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="17372-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="17372-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="17372-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span><span class="sxs-lookup"><span data-stu-id="17372-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="17372-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="17372-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="17372-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span><span class="sxs-lookup"><span data-stu-id="17372-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="17372-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span><span class="sxs-lookup"><span data-stu-id="17372-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="17372-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span><span class="sxs-lookup"><span data-stu-id="17372-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="17372-112">Consider the following example:</span><span class="sxs-lookup"><span data-stu-id="17372-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="17372-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span><span class="sxs-lookup"><span data-stu-id="17372-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="17372-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span><span class="sxs-lookup"><span data-stu-id="17372-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="17372-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span><span class="sxs-lookup"><span data-stu-id="17372-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="17372-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17372-116">See also</span></span>

- [<span data-ttu-id="17372-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="17372-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="17372-118">How to: Declare an Enumeration</span><span class="sxs-lookup"><span data-stu-id="17372-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="17372-119">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="17372-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="17372-120">How to: Iterate Through An Enumeration in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17372-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="17372-121">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="17372-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="17372-122">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="17372-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="17372-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="17372-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="17372-124">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="17372-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="17372-125">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="17372-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="17372-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="17372-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
