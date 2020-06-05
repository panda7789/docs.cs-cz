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
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388787"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="15e5c-102">Operátory řetězení v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e5c-102">Concatenation Operators in Visual Basic</span></span>

<span data-ttu-id="15e5c-103">Operátory zřetězení spojí více řetězců do jednoho řetězce.</span><span class="sxs-lookup"><span data-stu-id="15e5c-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="15e5c-104">Existují dva operátory zřetězení `+` a `&` .</span><span class="sxs-lookup"><span data-stu-id="15e5c-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="15e5c-105">Obojí provede základní operaci zřetězení, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="15e5c-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

<span data-ttu-id="15e5c-106">Tyto operátory mohou také zřetězit `String` proměnné, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="15e5c-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="15e5c-107">Rozdíly mezi dvěma operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="15e5c-107">Differences Between the Two Concatenation Operators</span></span>

<span data-ttu-id="15e5c-108">[Operátor +](../../../language-reference/operators/addition-operator.md) má primární účel přidání dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="15e5c-108">The [+ Operator](../../../language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="15e5c-109">Může však také zřetězit číselné operandy pomocí řetězcových operandů.</span><span class="sxs-lookup"><span data-stu-id="15e5c-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="15e5c-110">`+`Operátor má komplexní sadu pravidel, která určuje, zda se má přidat, zřetězit, signalizovat chybu kompilátoru nebo vyvolat výjimku za běhu <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="15e5c-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="15e5c-111">[Operátor&](../../../language-reference/operators/concatenation-operator.md) je definován pouze pro `String` operandy a vždy rozšiřuje jeho operandy na `String` , bez ohledu na nastavení `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="15e5c-111">The [& Operator](../../../language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="15e5c-112">`&`Operátor je doporučen pro zřetězení řetězců, protože je definován výhradně pro řetězce a snižuje pravděpodobnost vygenerování nezamýšlené konverze.</span><span class="sxs-lookup"><span data-stu-id="15e5c-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>

## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="15e5c-113">Výkon: String a StringBuilder</span><span class="sxs-lookup"><span data-stu-id="15e5c-113">Performance: String and StringBuilder</span></span>

<span data-ttu-id="15e5c-114">Pokud provedete velký počet manipulace s řetězcem, jako jsou zřetězení, odstranění a náhrady, váš výkon může být ziskem z <xref:System.Text.StringBuilder> třídy v <xref:System.Text> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="15e5c-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="15e5c-115">Má navíc pokyn k vytvoření a inicializaci <xref:System.Text.StringBuilder> objektu a další instrukce pro převod konečné hodnoty na `String` , ale můžete tento čas obnovit, protože <xref:System.Text.StringBuilder> může být rychlejší.</span><span class="sxs-lookup"><span data-stu-id="15e5c-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>

## <a name="see-also"></a><span data-ttu-id="15e5c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="15e5c-116">See also</span></span>

- [<span data-ttu-id="15e5c-117">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="15e5c-117">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="15e5c-118">Typy metod manipulace s řetězci v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e5c-118">Types of String Manipulation Methods in Visual Basic</span></span>](../strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="15e5c-119">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e5c-119">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="15e5c-120">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e5c-120">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="15e5c-121">Logické a bitové operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15e5c-121">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
