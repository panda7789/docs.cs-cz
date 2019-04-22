---
title: Operátory řetězení v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: 124f0ca0cd01d7fd218fd89dfb78e70fe8aad9e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835723"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="788d5-102">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="788d5-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="788d5-103">Operátory řetězení více řetězců připojení do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="788d5-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="788d5-104">Existují dva operátory zřetězení `+` a `&`.</span><span class="sxs-lookup"><span data-stu-id="788d5-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="788d5-105">Obě provedení operace základní zřetězení, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="788d5-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="788d5-106">Tyto operátory lze také zřetězit `String` proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="788d5-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="788d5-107">Rozdíly mezi dva operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="788d5-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="788d5-108">[+ – Operátor](../../../../visual-basic/language-reference/operators/addition-operator.md) je hlavním účelem sečtení dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="788d5-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="788d5-109">Nicméně lze zřetězit také číselné operandů s operandy řetězec.</span><span class="sxs-lookup"><span data-stu-id="788d5-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="788d5-110">`+` Operátor nemá komplexní sadu pravidel, které určují, jestli se má přidat, zřetězit, signalizuje, že chyba kompilátoru nebo výjimku za běhu <xref:System.InvalidCastException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="788d5-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="788d5-111">[& – Operátor](../../../../visual-basic/language-reference/operators/concatenation-operator.md) je určená jenom pro `String` operandy a to vždy rozšiřuje jeho operandy `String`bez ohledu na nastavení `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="788d5-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="788d5-112">`&` Operátor se doporučuje pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje pravděpodobnost generování neúmyslnému převodu.</span><span class="sxs-lookup"><span data-stu-id="788d5-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="788d5-113">Výkon: String a StringBuilder</span><span class="sxs-lookup"><span data-stu-id="788d5-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="788d5-114">Pokud tak učiníte velký počet manipulace na řetězec, například zřetězení, odstranění a nahrazení, může být z zisku výkonu <xref:System.Text.StringBuilder> třídy v <xref:System.Text> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="788d5-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="788d5-115">Přijímá další instrukce k vytváření a inicializace <xref:System.Text.StringBuilder> objektu a další pokyny, jak převést na jeho poslední hodnotu `String`, ale tentokrát může obnovit, protože <xref:System.Text.StringBuilder> může pracovat rychleji.</span><span class="sxs-lookup"><span data-stu-id="788d5-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788d5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="788d5-116">See also</span></span>

- [<span data-ttu-id="788d5-117">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="788d5-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="788d5-118">Typy metod manipulace s řetězci v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="788d5-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="788d5-119">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="788d5-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="788d5-120">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="788d5-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="788d5-121">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="788d5-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
