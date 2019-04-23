---
title: 'Postupy: Seskupení souvisejících hodnot konstant společně (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: a4f74e48cfdd5c0bc0f745d0f32eb39442f5bd83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333324"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="0c13e-102">Postupy: Seskupení souvisejících hodnot konstant společně (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c13e-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="0c13e-103">Výčet je nejlepší způsob, jak seskupit související s konstantami.</span><span class="sxs-lookup"><span data-stu-id="0c13e-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="0c13e-104">Vytvořit výčet s `Enum` příkazu v části deklarace třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="0c13e-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="0c13e-105">Další informace najdete v tématu [jak: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="0c13e-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="0c13e-106">Ke skupině souvisejících hodnot konstant</span><span class="sxs-lookup"><span data-stu-id="0c13e-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="0c13e-107">Zápis deklarace, která zahrnuje úroveň přístupu kódu, `Enum` – klíčové slovo a platný název.</span><span class="sxs-lookup"><span data-stu-id="0c13e-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="0c13e-108">Tento příklad vytvoří `Private` výčet, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="0c13e-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="0c13e-109">Definujte konstanty ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0c13e-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="0c13e-110">Tento příklad vytvoří `Public` výčet `temperatureValues` a přiřazuje hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0c13e-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0c13e-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c13e-111">See also</span></span>

- [<span data-ttu-id="0c13e-112">Výčty a kvalifikace názvu</span><span class="sxs-lookup"><span data-stu-id="0c13e-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="0c13e-113">Postupy: Odkazování na člena výčtu</span><span class="sxs-lookup"><span data-stu-id="0c13e-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="0c13e-114">Kdy použít výčet</span><span class="sxs-lookup"><span data-stu-id="0c13e-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="0c13e-115">Přehled konstant</span><span class="sxs-lookup"><span data-stu-id="0c13e-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="0c13e-116">Datové typy konstanty a literálu</span><span class="sxs-lookup"><span data-stu-id="0c13e-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="0c13e-117">Konstanty a výčty</span><span class="sxs-lookup"><span data-stu-id="0c13e-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
