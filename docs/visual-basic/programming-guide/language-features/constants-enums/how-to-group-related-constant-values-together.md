---
title: 'Postupy: Seskupení souvisejících hodnot konstant společně (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 63475487c8a35f5b306b28d4e7097324bef00d85
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977822"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="4c3b3-102">Postupy: Seskupení souvisejících hodnot konstant společně (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c3b3-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="4c3b3-103">Výčet je nejlepší způsob, jak seskupit související s konstantami.</span><span class="sxs-lookup"><span data-stu-id="4c3b3-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="4c3b3-104">Vytvořit výčet s `Enum` příkazu v části deklarace třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="4c3b3-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="4c3b3-105">Další informace najdete v tématu [jak: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="4c3b3-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="4c3b3-106">Ke skupině souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="4c3b3-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="4c3b3-107">Zápis deklarace, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název.</span><span class="sxs-lookup"><span data-stu-id="4c3b3-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="4c3b3-108">Tento příklad vytvoří `Private` výčet, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="4c3b3-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2.  <span data-ttu-id="4c3b3-109">Definujte konstanty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="4c3b3-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="4c3b3-110">Tento příklad vytvoří `Public` výčet `temperatureValues` a přiřazuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4c3b3-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4c3b3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c3b3-111">See also</span></span>
- [<span data-ttu-id="4c3b3-112">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="4c3b3-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="4c3b3-113">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="4c3b3-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="4c3b3-114">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="4c3b3-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="4c3b3-115">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="4c3b3-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="4c3b3-116">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="4c3b3-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="4c3b3-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="4c3b3-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
