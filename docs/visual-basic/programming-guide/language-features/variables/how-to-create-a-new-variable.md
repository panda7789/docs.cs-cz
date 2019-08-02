---
title: 'Postupy: Vytvořit novou proměnnou (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: a6cb7225ea203f0b38b731795684bfb0cfdfd2d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630896"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="56cad-102">Postupy: Vytvořit novou proměnnou (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56cad-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="56cad-103">Vytvoříte proměnnou pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="56cad-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="56cad-104">Vytvoření nové proměnné</span><span class="sxs-lookup"><span data-stu-id="56cad-104">To create a new variable</span></span>

1. <span data-ttu-id="56cad-105">Deklarujte proměnnou v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="56cad-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="56cad-106">Zahrňte specifikace charakteristik proměnných, jako jsou [Private](../../../../visual-basic/language-reference/modifiers/private.md), [static](../../../../visual-basic/language-reference/modifiers/static.md), Shadows [](../../../../visual-basic/language-reference/modifiers/shadows.md)nebo [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="56cad-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="56cad-107">Další informace naleznete v tématu [deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="56cad-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="56cad-108">Klíčové slovo nemusíte `Dim` potřebovat, pokud v deklaraci použijete jiná klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="56cad-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="56cad-109">Postupujte podle specifikace s názvem proměnné, který musí dodržovat pravidla Visual Basic a konvence.</span><span class="sxs-lookup"><span data-stu-id="56cad-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="56cad-110">Další informace naleznete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="56cad-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="56cad-111">Podle názvu s klauzulí [as](../../../../visual-basic/language-reference/statements/as-clause.md) určete datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="56cad-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="56cad-112">Pokud datový typ nezadáte, použije se výchozí hodnota: `Object`.</span><span class="sxs-lookup"><span data-stu-id="56cad-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="56cad-113">Použijte klauzuli symbolem rovná se (`=`) a použijte symbol rovná se s počáteční hodnotou proměnné. `As`</span><span class="sxs-lookup"><span data-stu-id="56cad-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="56cad-114">Visual Basic přiřazuje zadanou hodnotu proměnné při každém spuštění `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="56cad-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="56cad-115">Pokud nezadáte počáteční hodnotu, Visual Basic přiřadí výchozí počáteční hodnotu pro datový typ proměnné při prvním zadání kódu, který obsahuje `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="56cad-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="56cad-116">Pokud je proměnná typem odkazu, můžete vytvořit instanci své třídy zahrnutím klíčového slova [New operátor](../../../../visual-basic/language-reference/operators/new-operator.md) do `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="56cad-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="56cad-117">Pokud nepoužijete `New`, počáteční hodnota proměnné není [Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="56cad-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="56cad-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56cad-118">See also</span></span>

- [<span data-ttu-id="56cad-119">Proměnné</span><span class="sxs-lookup"><span data-stu-id="56cad-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="56cad-120">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="56cad-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="56cad-121">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="56cad-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="56cad-122">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="56cad-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="56cad-123">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="56cad-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="56cad-124">Příkazy</span><span class="sxs-lookup"><span data-stu-id="56cad-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="56cad-125">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="56cad-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="56cad-126">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="56cad-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
