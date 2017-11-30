---
title: "Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e2b0cfa6b1e426b38198581c7d493c8907b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="cb80e-102">Postupy: Určení řetězce spojeného s hodnotou výčtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb80e-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="cb80e-103"><xref:System.Enum.GetValues%2A> a <xref:System.Enum.GetNames%2A> metody vám umožňují určit řetězce a hodnoty přidružené členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="cb80e-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="cb80e-104">K určení řetězce spojeného s výčet</span><span class="sxs-lookup"><span data-stu-id="cb80e-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="cb80e-105">Použití <xref:System.Enum.GetNames%2A> metoda pro načtení řetězců přidružené členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="cb80e-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="cb80e-106">Tento příklad deklaruje výčet, `flavorEnum`, použije <xref:System.Enum.GetNames%2A> metodu pro zobrazení řetězce přidružené k každého člena.</span><span class="sxs-lookup"><span data-stu-id="cb80e-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cb80e-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb80e-107">See Also</span></span>  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [<span data-ttu-id="cb80e-108">Postupy: deklarace výčtů</span><span class="sxs-lookup"><span data-stu-id="cb80e-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="cb80e-109">Postupy: odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="cb80e-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="cb80e-110">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="cb80e-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="cb80e-111">Postupy: iterace výčet v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb80e-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="cb80e-112">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="cb80e-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="cb80e-113">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="cb80e-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
