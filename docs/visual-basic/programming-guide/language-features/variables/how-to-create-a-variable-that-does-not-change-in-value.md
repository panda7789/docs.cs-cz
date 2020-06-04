---
title: 'Postupy: Vytvoření proměnné, která se nezmění na hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 04e08784b5cfbdeb6db73b9b00fe9afa201bd06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410513"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="f455e-102">Postupy: Vytvoření proměnné, která se nezmění na hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f455e-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="f455e-103">Pojem proměnné, která nemění jeho hodnotu, může být neprotichůdný.</span><span class="sxs-lookup"><span data-stu-id="f455e-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="f455e-104">Existují však situace, kdy konstanta není proveditelná a je užitečné mít proměnnou s pevnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f455e-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="f455e-105">V takovém případě můžete definovat členskou proměnnou s klíčovým slovem [ReadOnly](../../../language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="f455e-105">In such a case you can define a member variable with the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="f455e-106">[Příkaz const](../../../language-reference/statements/const-statement.md) nelze použít k deklaraci a přiřazení konstantní hodnoty v následujících situacích:</span><span class="sxs-lookup"><span data-stu-id="f455e-106">You cannot use the [Const Statement](../../../language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="f455e-107">`Const`Příkaz nepřijímá datový typ, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="f455e-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="f455e-108">Neznáte hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f455e-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="f455e-109">Nemůžete vypočítat konstantní hodnotu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="f455e-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="f455e-110">Vytvoření proměnné, která se nemění v hodnotě</span><span class="sxs-lookup"><span data-stu-id="f455e-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="f455e-111">Na úrovni modulu deklarujte členskou proměnnou pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md)a přidejte klíčové slovo [ReadOnly](../../../language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="f455e-111">At module level, declare a member variable with the [Dim Statement](../../../language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="f455e-112">Můžete zadat `ReadOnly` pouze pro členskou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f455e-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="f455e-113">To znamená, že je nutné definovat proměnnou na úrovni modulu, mimo jakoukoli proceduru.</span><span class="sxs-lookup"><span data-stu-id="f455e-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="f455e-114">Pokud můžete vypočítat hodnotu v jednom příkazu v době kompilace, použijte klauzuli inicializace v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f455e-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="f455e-115">Použijte klauzuli [as](../../../language-reference/statements/as-clause.md) se symbolem rovná se ( `=` ) následovaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="f455e-115">Follow the [As](../../../language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="f455e-116">Ujistěte se, že kompilátor může tento výraz vyhodnotit na konstantní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f455e-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="f455e-117">Hodnotu proměnné můžete přiřadit `ReadOnly` pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="f455e-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="f455e-118">Jakmile to uděláte, žádný kód nemůže někdy změnit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f455e-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="f455e-119">Pokud neznáte hodnotu v době kompilace nebo ji nelze vypočítat v době kompilace v rámci jednoho příkazu, lze ji v konstruktoru přiřadit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f455e-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="f455e-120">K tomu je nutné deklarovat `ReadOnly` proměnnou na úrovni třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="f455e-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="f455e-121">V konstruktoru této třídy nebo struktury vypočítáte pevnou hodnotu proměnné a před návratem z konstruktoru ji přiřaďte proměnné.</span><span class="sxs-lookup"><span data-stu-id="f455e-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="f455e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f455e-122">See also</span></span>

- [<span data-ttu-id="f455e-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="f455e-123">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="f455e-124">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="f455e-124">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
