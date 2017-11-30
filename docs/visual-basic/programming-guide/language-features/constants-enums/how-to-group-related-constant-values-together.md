---
title: "Postupy: Seskupení souvisejících hodnot konstant (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="a94c4-102">Postupy: Seskupení souvisejících hodnot konstant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a94c4-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="a94c4-103">Výčet je nejlepší způsob, jak seskupit související konstanty.</span><span class="sxs-lookup"><span data-stu-id="a94c4-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="a94c4-104">Vytvoření výčtu s `Enum` prohlášení v části prohlášení o třídu nebo modul.</span><span class="sxs-lookup"><span data-stu-id="a94c4-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="a94c4-105">Další informace najdete v tématu [postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="a94c4-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="a94c4-106">Do skupiny souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="a94c4-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="a94c4-107">Zápis deklaraci, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název.</span><span class="sxs-lookup"><span data-stu-id="a94c4-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="a94c4-108">Tento příklad vytvoří `Private` výčtu `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="a94c4-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="a94c4-109">Definujte konstanty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="a94c4-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="a94c4-110">Tento příklad vytvoří `Public` výčtu `temperatureValues` a přiřadí jeho hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a94c4-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a94c4-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a94c4-111">See Also</span></span>  
 [<span data-ttu-id="a94c4-112">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="a94c4-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="a94c4-113">Postupy: odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="a94c4-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="a94c4-114">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="a94c4-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="a94c4-115">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="a94c4-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="a94c4-116">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="a94c4-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="a94c4-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="a94c4-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
