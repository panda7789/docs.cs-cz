---
title: "Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="ccf7a-102">Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ccf7a-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="ccf7a-103">Znalost problematicky proměnné, která se nezmění jeho hodnota může vypadat jako odporuje.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="ccf7a-104">Ale existují situace, když konstanta není vhodná, a je užitečné používat proměnné s pevnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="ccf7a-105">V takovém případě můžete definovat členské proměnné s [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="ccf7a-106">Nelze použít [příkaz Const](../../../../visual-basic/language-reference/statements/const-statement.md) deklarovat a přiřadit konstantní hodnotu v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="ccf7a-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="ccf7a-107">`Const` Příkaz nepřijímá datový typ, který chcete použít</span><span class="sxs-lookup"><span data-stu-id="ccf7a-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="ccf7a-108">Neznáte hodnota v době kompilace</span><span class="sxs-lookup"><span data-stu-id="ccf7a-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="ccf7a-109">Nelze vypočítat hodnotu konstanty v době kompilace</span><span class="sxs-lookup"><span data-stu-id="ccf7a-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="ccf7a-110">K vytvoření proměnné, která se nezmění na hodnotu</span><span class="sxs-lookup"><span data-stu-id="ccf7a-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="ccf7a-111">Na úrovni modulu deklarovat členské proměnné s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)a zahrnout [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="ccf7a-112">Můžete zadat `ReadOnly` pouze na členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="ccf7a-113">To znamená, že je nutné definovat proměnnou na úrovni modulu mimo jakéhokoli postupu.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="ccf7a-114">Pokud hodnota v jediném příkazu v době kompilace můžete vypočítat, použijte klauzuli inicializace v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="ccf7a-115">Postupujte podle [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule symbol rovná se (`=`), za nímž následují výrazu.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="ccf7a-116">Ujistěte se, že kompilátor můžete vyhodnotit na konstantní hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="ccf7a-117">Můžete přiřadit hodnotu na `ReadOnly` proměnné pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="ccf7a-118">Až to uděláte tak, žádný kód někdy změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="ccf7a-119">Pokud neznáte hodnotu v době kompilace, nebo nelze výpočetní v době kompilace v jediném příkazu, můžete ho přiřadit stále za běhu v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="ccf7a-120">K tomu je potřeba deklarovat `ReadOnly` proměnné na úrovni třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="ccf7a-121">V konstruktoru pro tuto třídu nebo strukturu výpočetní pevná hodnota proměnné a přiřaďte ho do proměnné před vrácením z konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ccf7a-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf7a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccf7a-122">See Also</span></span>  
 [<span data-ttu-id="ccf7a-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="ccf7a-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="ccf7a-124">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="ccf7a-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
