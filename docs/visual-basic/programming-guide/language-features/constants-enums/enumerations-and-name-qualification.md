---
title: "Výčty a kvalifikace názvu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb97d6a8f4b7e81f2b759010214e200ec63ff21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="cd302-102">Výčty a kvalifikace názvu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd302-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="cd302-103">Za normálních okolností k odkazování na člena výčtu, musíte před název člena s názvem výčtu.</span><span class="sxs-lookup"><span data-stu-id="cd302-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="cd302-104">Pro příklad, který bude odkazovat na `Sunday` členem vaší `Days` výčet, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="cd302-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="cd302-105">Pomocí příkazu importy</span><span class="sxs-lookup"><span data-stu-id="cd302-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="cd302-106">Používání plně kvalifikované názvy přidáním se můžete vyhnout `Imports` příkaz, který má v oboru názvů deklarace části kódu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cd302-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="cd302-107">`Imports` Příkaz importuje názvy oborů názvů prostřednictvím odkazovaného projekty a sestavení a v rámci stejného projektu jako modul, ve kterém se zobrazí příkaz.</span><span class="sxs-lookup"><span data-stu-id="cd302-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="cd302-108">Po přidání tohoto prohlášení, můžete odkazovat na vaše členy výčtu bez kvalifikace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cd302-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="cd302-109">Uspořádání sady souvisejících konstanty v výčty, můžete pomocí stejné konstantní názvy v různých kontextech.</span><span class="sxs-lookup"><span data-stu-id="cd302-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="cd302-110">Například můžete použít stejné názvy konstanty den v týdnu v `Days` a `WorkDays` výčty.</span><span class="sxs-lookup"><span data-stu-id="cd302-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="cd302-111">Pokud použijete `Imports` příkaz s vaší výčty, musí být snažte se vyhnout nejednoznačný odkazy.</span><span class="sxs-lookup"><span data-stu-id="cd302-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="cd302-112">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="cd302-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="cd302-113">Za předpokladu, že `Monday` je členem obou `Days` výčet a `Workdays` výčtu, tento kód se generuje chyba kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cd302-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="cd302-114">Aby se zabránilo nejednoznačný odkazy k odkazování na jednotlivé konstanta, kvalifikovat konstantní název s její výčet.</span><span class="sxs-lookup"><span data-stu-id="cd302-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="cd302-115">Následující kód odkazuje `Saturday` konstanty v `Days` a `WorkDays` výčty.</span><span class="sxs-lookup"><span data-stu-id="cd302-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cd302-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd302-116">See Also</span></span>  
 [<span data-ttu-id="cd302-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="cd302-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="cd302-118">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="cd302-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="cd302-119">Postupy: odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="cd302-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="cd302-120">Postupy: iterace výčet v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cd302-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="cd302-121">Postupy: určení řetězce spojeného s hodnotou výčtu</span><span class="sxs-lookup"><span data-stu-id="cd302-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="cd302-122">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="cd302-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="cd302-123">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="cd302-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="cd302-124">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="cd302-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="cd302-125">Imports – příkaz (Namespace .NET a typ)</span><span class="sxs-lookup"><span data-stu-id="cd302-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="cd302-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="cd302-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
