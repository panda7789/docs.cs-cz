---
title: 'Postupy: získávání adresy proměnné (C# Programming Guide)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bb752306bcdb630d652d331e95a765aee6afac3d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150937"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="d0742-102">Postupy: získávání adresy proměnné (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d0742-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="d0742-103">Pro získání adresy jednočlenný výraz, který je vyhodnocen pevná proměnná, použití operátoru address-of `&`:</span><span class="sxs-lookup"><span data-stu-id="d0742-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="d0742-104">Operátor address-of může používat jedině pro proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d0742-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="d0742-105">Pokud je proměnná přesunutelný proměnné, můžete použít [oprava příkazu](../../../csharp/language-reference/keywords/fixed-statement.md) dočasně vyřešit proměnnou před získáním adresy.</span><span class="sxs-lookup"><span data-stu-id="d0742-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="d0742-106">Je vaší povinností ujistit, že je proměnná inicializována.</span><span class="sxs-lookup"><span data-stu-id="d0742-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="d0742-107">Kompilátor nebude vydat chybovou zprávu, pokud proměnná není inicializovaná.</span><span class="sxs-lookup"><span data-stu-id="d0742-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="d0742-108">Nelze získat adresu konstanta nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="d0742-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0742-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0742-109">Example</span></span>  
 <span data-ttu-id="d0742-110">V tomto příkladu ukazatel na `int`, `p`, je deklarována a přiřazenou adresu proměnnou celého čísla `number`.</span><span class="sxs-lookup"><span data-stu-id="d0742-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="d0742-111">Proměnná `number` je inicializována v důsledku přiřazení `*p`.</span><span class="sxs-lookup"><span data-stu-id="d0742-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="d0742-112">Pokud jste zakomentovali tohoto příkazu přiřazení, inicializace proměnné `number` Odebereme, ale není vyvolána žádná chyba kompilace.</span><span class="sxs-lookup"><span data-stu-id="d0742-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="d0742-113">Kompilaci tohoto příkladu s [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d0742-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d0742-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0742-114">See Also</span></span>

- [<span data-ttu-id="d0742-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d0742-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d0742-116">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d0742-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="d0742-117">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="d0742-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="d0742-118">Typy</span><span class="sxs-lookup"><span data-stu-id="d0742-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="d0742-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="d0742-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="d0742-120">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="d0742-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="d0742-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="d0742-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
