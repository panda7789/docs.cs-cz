---
title: 'Postupy: Vytvoření proměnné, která se nezmění na hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d5d8a6b066ae7e8795afd2f788b60823d8efdafa
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348634"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="0afe0-102">Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0afe0-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="0afe0-103">Pojem proměnné, která nemění jeho hodnotu, může být neprotichůdný.</span><span class="sxs-lookup"><span data-stu-id="0afe0-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="0afe0-104">Existují však situace, kdy konstanta není proveditelná a je užitečné mít proměnnou s pevnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0afe0-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="0afe0-105">V takovém případě můžete definovat členskou proměnnou s klíčovým slovem [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="0afe0-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="0afe0-106">[Příkaz const](../../../../visual-basic/language-reference/statements/const-statement.md) nelze použít k deklaraci a přiřazení konstantní hodnoty v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="0afe0-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="0afe0-107">Příkaz `Const` nepřijímá datový typ, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="0afe0-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="0afe0-108">Neznáte hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0afe0-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="0afe0-109">Nemůžete vypočítat konstantní hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="0afe0-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="0afe0-110">Vytvoření proměnné, která se nemění v hodnotě</span><span class="sxs-lookup"><span data-stu-id="0afe0-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="0afe0-111">Na úrovni modulu deklarujte členskou proměnnou pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)a přidejte klíčové slovo [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="0afe0-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="0afe0-112">`ReadOnly` lze zadat pouze pro členskou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0afe0-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="0afe0-113">To znamená, že je nutné definovat proměnnou na úrovni modulu, mimo jakoukoli proceduru.</span><span class="sxs-lookup"><span data-stu-id="0afe0-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="0afe0-114">Pokud můžete vypočítat hodnotu v jednom příkazu v době kompilace, použijte klauzuli inicializace v příkazu `Dim`.</span><span class="sxs-lookup"><span data-stu-id="0afe0-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="0afe0-115">Použijte klauzuli [as](../../../../visual-basic/language-reference/statements/as-clause.md) se symbolem rovná se (`=`) následovaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="0afe0-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="0afe0-116">Ujistěte se, že kompilátor může tento výraz vyhodnotit na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0afe0-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="0afe0-117">Hodnotu `ReadOnly` proměnné můžete přiřadit pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0afe0-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="0afe0-118">Jakmile to uděláte, žádný kód nemůže někdy změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0afe0-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="0afe0-119">Pokud neznáte hodnotu v době kompilace nebo ji nelze vypočítat v době kompilace v rámci jednoho příkazu, lze ji v konstruktoru přiřadit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0afe0-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="0afe0-120">Chcete-li to provést, musíte deklarovat `ReadOnly` proměnnou na úrovni třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="0afe0-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="0afe0-121">V konstruktoru této třídy nebo struktury vypočítáte pevnou hodnotu proměnné a před návratem z konstruktoru ji přiřaďte proměnné.</span><span class="sxs-lookup"><span data-stu-id="0afe0-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="0afe0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0afe0-122">See also</span></span>

- [<span data-ttu-id="0afe0-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="0afe0-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="0afe0-124">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="0afe0-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
