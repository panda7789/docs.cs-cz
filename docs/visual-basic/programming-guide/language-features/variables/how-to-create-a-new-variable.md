---
title: "Postupy: Vytvoření nové proměnné (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6806dcbe9e00cbae77181b79d74ddb9a1e1493f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="e4593-102">Postupy: Vytvoření nové proměnné (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4593-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="e4593-103">Vytvořte proměnnou s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e4593-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="e4593-104">Chcete-li vytvořit nové proměnné</span><span class="sxs-lookup"><span data-stu-id="e4593-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="e4593-105">Deklarace proměnné v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e4593-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="e4593-106">Zahrnout specifikace charakteristik proměnné, jako například [privátní](../../../../visual-basic/language-reference/modifiers/private.md), [statické](../../../../visual-basic/language-reference/modifiers/static.md), [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md), nebo [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="e4593-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="e4593-107">Další informace najdete v tématu [deklarované charakteristiky elementu](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="e4593-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="e4593-108">Není nutné `Dim` – klíčové slovo, pokud používáte žádná jiná klíčová slova v deklaraci.</span><span class="sxs-lookup"><span data-stu-id="e4593-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="e4593-109">Postupujte podle specifikace s název proměnné, která musí odpovídat [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pravidla a pravidla týkající se.</span><span class="sxs-lookup"><span data-stu-id="e4593-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rules and conventions.</span></span> <span data-ttu-id="e4593-110">Další informace najdete v tématu [deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e4593-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="e4593-111">Postupujte podle názvu s [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule zadat datový typ proměnné.</span><span class="sxs-lookup"><span data-stu-id="e4593-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="e4593-112">Pokud nezadáte datový typ, použije výchozí hodnota: `Object`.</span><span class="sxs-lookup"><span data-stu-id="e4593-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="e4593-113">Postupujte podle `As` klauzule symbol rovná se (`=`) a postupujte podle pokynů rovná s počáteční hodnota proměnné.</span><span class="sxs-lookup"><span data-stu-id="e4593-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e4593-114">Zadaná hodnota přiřadí proměnné pokaždé, když ji spustí `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e4593-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="e4593-115">Pokud nezadáte hodnotu počáteční [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] po jej nejprve zadá kód, který obsahuje přiřadí výchozí počáteční hodnota pro datový typ proměnné `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e4593-115">If you do not specify an initial value, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="e4593-116">Pokud je proměnná typu odkazu, můžete vytvořit instanci její třídy zahrnutím [operátor New](../../../../visual-basic/language-reference/operators/new-operator.md) – klíčové slovo v `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="e4593-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="e4593-117">Pokud nepoužijete `New`, je počáteční hodnota proměnné [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="e4593-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e4593-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4593-118">See Also</span></span>  
 [<span data-ttu-id="e4593-119">Proměnné</span><span class="sxs-lookup"><span data-stu-id="e4593-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="e4593-120">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="e4593-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="e4593-121">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="e4593-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="e4593-122">Deklarované charakteristiky elementu</span><span class="sxs-lookup"><span data-stu-id="e4593-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="e4593-123">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="e4593-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="e4593-124">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e4593-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="e4593-125">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="e4593-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="e4593-126">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="e4593-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
