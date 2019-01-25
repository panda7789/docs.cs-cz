---
title: 'Postupy: Vytvoření nové proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: db317b160a27c7e38bddba82eb4eac3088886705
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506885"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="db5f7-102">Postupy: Vytvoření nové proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db5f7-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="db5f7-103">Vytvořte proměnnou s [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="db5f7-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="db5f7-104">Chcete-li vytvořit nové proměnné</span><span class="sxs-lookup"><span data-stu-id="db5f7-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="db5f7-105">Deklarujte proměnnou v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="db5f7-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="db5f7-106">Zahrnout specifikace vlastnosti proměnné, třeba [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [statické](../../../../visual-basic/language-reference/modifiers/static.md), [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md), nebo [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="db5f7-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="db5f7-107">Další informace najdete v tématu [deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="db5f7-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="db5f7-108">Není nutné `Dim` – klíčové slovo použití dalších klíčových slovech v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="db5f7-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="db5f7-109">Postupujte podle specifikace s názvem proměnné, které musí následovat Visual Basic – pravidla a pravidla týkající se.</span><span class="sxs-lookup"><span data-stu-id="db5f7-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="db5f7-110">Další informace najdete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="db5f7-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="db5f7-111">Postupujte podle názvu se [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule zadejte datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="db5f7-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="db5f7-112">Pokud nezadáte datový typ, použije výchozí hodnota: `Object`.</span><span class="sxs-lookup"><span data-stu-id="db5f7-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="db5f7-113">Postupujte podle `As` klauzule znaménko rovná se (`=`) a postupujte podle pokynů znaménka rovnosti s počáteční hodnotou proměnné.</span><span class="sxs-lookup"><span data-stu-id="db5f7-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="db5f7-114">Visual Basic přiřadí zadanou hodnotu k proměnné pokaždé, když ji spustí `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="db5f7-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="db5f7-115">Pokud počáteční hodnotu nezadáte, Visual Basic přiřadí výchozí počáteční hodnotu pro datový typ proměnné, když poprvé vstoupí kód, který obsahuje `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="db5f7-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="db5f7-116">Pokud je proměnná typu odkazu, můžete vytvořit instanci její třídy zahrnutím [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo v `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="db5f7-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="db5f7-117">Pokud nepoužijete `New`, je počáteční hodnota proměnné [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="db5f7-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="db5f7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db5f7-118">See also</span></span>
- [<span data-ttu-id="db5f7-119">Proměnné</span><span class="sxs-lookup"><span data-stu-id="db5f7-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="db5f7-120">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="db5f7-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="db5f7-121">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="db5f7-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="db5f7-122">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="db5f7-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="db5f7-123">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="db5f7-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="db5f7-124">Příkazy</span><span class="sxs-lookup"><span data-stu-id="db5f7-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
- [<span data-ttu-id="db5f7-125">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="db5f7-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="db5f7-126">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="db5f7-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
