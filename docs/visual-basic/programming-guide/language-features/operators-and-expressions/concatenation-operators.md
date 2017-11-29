---
title: "Operátory řetězení v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a444cca76fbc41807b0c8b69bcbaedbd75c36eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="1ec58-102">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ec58-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="1ec58-103">Operátory řetězení více řetězců připojení do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="1ec58-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="1ec58-104">Existují dva operátory zřetězení `+` a `&`.</span><span class="sxs-lookup"><span data-stu-id="1ec58-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="1ec58-105">Jak provádět základní zřetězení operace, jako ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1ec58-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="1ec58-106">Můžete také zřetězení těchto operátorů `String` proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1ec58-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="1ec58-107">Rozdíly mezi dva operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="1ec58-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="1ec58-108">[+ – Operátor](../../../../visual-basic/language-reference/operators/addition-operator.md) má primárním účelem přidání dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="1ec58-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="1ec58-109">Je však také řetězení číselné operandy s operandy řetězec.</span><span class="sxs-lookup"><span data-stu-id="1ec58-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="1ec58-110">`+` Operátor obsahuje komplexní sadu pravidel, které určují, jestli se mají přidat, zřetězení, signál Chyba kompilátoru nebo throw za běhu <xref:System.InvalidCastException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="1ec58-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="1ec58-111">[& Operátor](../../../../visual-basic/language-reference/operators/concatenation-operator.md) je určená jenom pro `String` operandy a vždy rozšiřuje jejími operandy k `String`, bez ohledu na to, že v nastavení `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="1ec58-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="1ec58-112">`&` Operátor se doporučuje pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje možnost generování nezamýšleným převod.</span><span class="sxs-lookup"><span data-stu-id="1ec58-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="1ec58-113">Výkon: Řetězec a StringBuilder</span><span class="sxs-lookup"><span data-stu-id="1ec58-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="1ec58-114">Pokud tak učiníte velký počet manipulace na řetězec, například zřetězování, odstranění a nahrazení, může výkon zisku z <xref:System.Text.StringBuilder> třídy v <xref:System.Text> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1ec58-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="1ec58-115">Trvá další instrukce k vytvoření a inicializace <xref:System.Text.StringBuilder> objekt a jiné instrukce převést jeho konečná hodnota k `String`, ale tentokrát může obnovit, protože <xref:System.Text.StringBuilder> může pracovat rychleji.</span><span class="sxs-lookup"><span data-stu-id="1ec58-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec58-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ec58-116">See Also</span></span>  
 [<span data-ttu-id="1ec58-117">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="1ec58-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="1ec58-118">Typy metod manipulace s řetězci v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ec58-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [<span data-ttu-id="1ec58-119">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ec58-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="1ec58-120">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ec58-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="1ec58-121">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ec58-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
