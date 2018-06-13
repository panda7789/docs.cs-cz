---
title: Výčty a kvalifikace názvu (Visual Basic)
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
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648577"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="61173-102">Výčty a kvalifikace názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61173-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="61173-103">Za normálních okolností k odkazování na člena výčtu, musíte před název člena s názvem výčtu.</span><span class="sxs-lookup"><span data-stu-id="61173-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="61173-104">Pro příklad, který bude odkazovat na `Sunday` členem vaší `Days` výčet, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="61173-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="61173-105">Pomocí příkazu importy</span><span class="sxs-lookup"><span data-stu-id="61173-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="61173-106">Používání plně kvalifikované názvy přidáním se můžete vyhnout `Imports` příkaz, který má v oboru názvů deklarace části kódu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="61173-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="61173-107">`Imports` Příkaz importuje názvy oborů názvů prostřednictvím odkazovaného projekty a sestavení a v rámci stejného projektu jako modul, ve kterém se zobrazí příkaz.</span><span class="sxs-lookup"><span data-stu-id="61173-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="61173-108">Po přidání tohoto prohlášení, můžete odkazovat na vaše členy výčtu bez kvalifikace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="61173-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="61173-109">Uspořádání sady souvisejících konstanty v výčty, můžete pomocí stejné konstantní názvy v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="61173-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="61173-110">Například můžete použít stejné názvy konstanty den v týdnu v `Days` a `WorkDays` výčty.</span><span class="sxs-lookup"><span data-stu-id="61173-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="61173-111">Pokud použijete `Imports` příkaz s vaší výčty, musí být snažte se vyhnout nejednoznačný odkazy.</span><span class="sxs-lookup"><span data-stu-id="61173-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="61173-112">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="61173-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="61173-113">Za předpokladu, že `Monday` je členem obou `Days` výčet a `Workdays` výčtu, tento kód se generuje chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="61173-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="61173-114">Aby se zabránilo nejednoznačný odkazy k odkazování na jednotlivé konstanta, kvalifikovat konstantní název s její výčet.</span><span class="sxs-lookup"><span data-stu-id="61173-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="61173-115">Následující kód odkazuje `Saturday` konstanty v `Days` a `WorkDays` výčty.</span><span class="sxs-lookup"><span data-stu-id="61173-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="61173-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="61173-116">See Also</span></span>  
 [<span data-ttu-id="61173-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="61173-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="61173-118">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="61173-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="61173-119">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="61173-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="61173-120">Postupy: iterace výčet v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61173-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="61173-121">Postupy: Určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="61173-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="61173-122">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="61173-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="61173-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="61173-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="61173-124">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="61173-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="61173-125">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="61173-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="61173-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="61173-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
