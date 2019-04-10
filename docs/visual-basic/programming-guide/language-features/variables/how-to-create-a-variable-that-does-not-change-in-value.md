---
title: 'Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 7180e5141572d219ed02c57103e9d4b80cde536e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342931"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="0413e-102">Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0413e-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="0413e-103">Může zobrazit odporuje pojem proměnné, která se nezmění jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0413e-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="0413e-104">Ale existují situace, kdy konstanty není možné vydat je a je užitečné mít proměnná s pevnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0413e-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="0413e-105">V takovém případě můžete členské proměnné s definovat [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0413e-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="0413e-106">Nelze použít [Const příkaz](../../../../visual-basic/language-reference/statements/const-statement.md) k deklaraci a přiřazení konstantní hodnoty v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="0413e-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="0413e-107">`Const` Příkaz nepřijímá datový typ, který chcete použít</span><span class="sxs-lookup"><span data-stu-id="0413e-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="0413e-108">Si nejste jisti hodnotu v době kompilace</span><span class="sxs-lookup"><span data-stu-id="0413e-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="0413e-109">Nejde Vypočítat konstantní hodnotu v době kompilace</span><span class="sxs-lookup"><span data-stu-id="0413e-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="0413e-110">K vytvoření proměnné, která se nezmění na hodnotu</span><span class="sxs-lookup"><span data-stu-id="0413e-110">To create a variable that does not change in value</span></span>  
  
1. <span data-ttu-id="0413e-111">Na úrovni modulu deklarace členské proměnné s [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)a zahrnout [jen pro čtení](../../../../visual-basic/language-reference/modifiers/readonly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="0413e-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="0413e-112">Můžete zadat `ReadOnly` pouze na členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="0413e-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="0413e-113">To znamená, že je nutné definovat proměnné na úrovni modulu mimo všechny procedury.</span><span class="sxs-lookup"><span data-stu-id="0413e-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2. <span data-ttu-id="0413e-114">Pokud můžete vypočítat hodnotu v jediném příkazu v době kompilace, použijte klauzule inicializace v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0413e-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="0413e-115">Postupujte podle [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzule znaménko rovná se (`=`) a potom pomocí výrazu.</span><span class="sxs-lookup"><span data-stu-id="0413e-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="0413e-116">Ujistěte se, že kompilátor můžete vyhodnotit tento výraz s konstantní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0413e-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="0413e-117">Můžete přiřadit hodnoty k `ReadOnly` proměnné pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0413e-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="0413e-118">Až to uděláte tak, žádný kód někdy můžete změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0413e-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="0413e-119">Pokud není známo, hodnota v době kompilace, nebo nelze vypočítat v době kompilace v jediném příkazu, stále ji můžete přiřadit v době běhu v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0413e-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="0413e-120">Chcete-li to provést, je třeba deklarovat `ReadOnly` proměnné na úrovni třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0413e-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="0413e-121">V konstruktoru třídy nebo struktury compute pevnou hodnotu proměnné a přiřadíte ho k proměnné návrat z konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0413e-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0413e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0413e-122">See also</span></span>

- [<span data-ttu-id="0413e-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="0413e-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="0413e-124">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="0413e-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
