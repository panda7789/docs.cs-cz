---
title: Operátory řetězení
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: f86245c649647be4e040a61083d8b93eee4d7422
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353678"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="c9976-102">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9976-102">Concatenation Operators in Visual Basic</span></span>

<span data-ttu-id="c9976-103">Operátory zřetězení spojí více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="c9976-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="c9976-104">Existují dva operátory zřetězení, `+` a `&`.</span><span class="sxs-lookup"><span data-stu-id="c9976-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="c9976-105">Obojí provede základní operaci zřetězení, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c9976-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

<span data-ttu-id="c9976-106">Tyto operátory mohou také zřetězit `String` proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="c9976-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="c9976-107">Rozdíly mezi dvěma operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="c9976-107">Differences Between the Two Concatenation Operators</span></span>

<span data-ttu-id="c9976-108">[Operátor +](../../../../visual-basic/language-reference/operators/addition-operator.md) má primární účel přidání dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="c9976-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="c9976-109">Může však také zřetězit číselné operandy pomocí řetězcových operandů.</span><span class="sxs-lookup"><span data-stu-id="c9976-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="c9976-110">Operátor `+` má komplexní sadu pravidel, která určuje, zda se má přidat, zřetězit, signalizovat chybu kompilátoru nebo vyvolat výjimku za běhu <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="c9976-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="c9976-111">[Operátor &](../../../../visual-basic/language-reference/operators/concatenation-operator.md) je definován pouze pro `String` operandy a vždy rozšiřuje jeho operandy na `String`, bez ohledu na nastavení `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="c9976-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="c9976-112">Operátor `&` je doporučen pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje pravděpodobnost vygenerování nezamýšlené konverze.</span><span class="sxs-lookup"><span data-stu-id="c9976-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>

## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="c9976-113">Výkon: String a StringBuilder</span><span class="sxs-lookup"><span data-stu-id="c9976-113">Performance: String and StringBuilder</span></span>

<span data-ttu-id="c9976-114">Pokud provedete velký počet manipulace s řetězcem, jako jsou zřetězení, odstranění a náhrady, váš výkon může být ziskem z <xref:System.Text.StringBuilder> třídy v oboru názvů <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="c9976-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="c9976-115">Vytvoření a inicializace objektu <xref:System.Text.StringBuilder> a další instrukce pro převod konečné hodnoty na `String`, ale můžete tento čas obnovit, protože <xref:System.Text.StringBuilder> může provádět rychleji.</span><span class="sxs-lookup"><span data-stu-id="c9976-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9976-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9976-116">See also</span></span>

- [<span data-ttu-id="c9976-117">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="c9976-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="c9976-118">Typy metod manipulace s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9976-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="c9976-119">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9976-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="c9976-120">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9976-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="c9976-121">Logické a bitové operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9976-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
