---
title: 'Postupy: Získávání adresy proměnné (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bb52aee3341194697b40b30ec14afced61a200be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340122"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="a9dfb-102">Postupy: Získávání adresy proměnné (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="a9dfb-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="a9dfb-103">Pokud chcete získat adresu unární výraz, který vyhodnocuje pevné proměnné, použijte operátor adresy `&`:</span><span class="sxs-lookup"><span data-stu-id="a9dfb-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="a9dfb-104">Operátor adresy lze použít pouze k proměnné.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="a9dfb-105">Pokud je proměnná přenosné proměnné, můžete použít [příkazu pevnou](../../../csharp/language-reference/keywords/fixed-statement.md) dočasně opravit před získávání adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="a9dfb-106">Je vaší povinností ujistit, že je inicializováno proměnnou.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="a9dfb-107">Kompilátor není vydat chybovou zprávu, pokud proměnnou není inicializován.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="a9dfb-108">Nelze získat adresu konstanta nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9dfb-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9dfb-109">Example</span></span>  
 <span data-ttu-id="a9dfb-110">V tomto příkladu ukazatel na `int`, `p`je deklarovaný a přiřazena adresa proměnná typu integer, `number`.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="a9dfb-111">Proměnná `number` je inicializován v důsledku přiřazení `*p`.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="a9dfb-112">Pokud jste komentář tento příkaz přiřazení inicializace proměnné `number` je odebrán, ale žádné dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="a9dfb-113">Kompilace v tomto příkladu se [ `-unsafe` ](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a9dfb-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="a9dfb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9dfb-114">See Also</span></span>  
 [<span data-ttu-id="a9dfb-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a9dfb-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a9dfb-116">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="a9dfb-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="a9dfb-117">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="a9dfb-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="a9dfb-118">Typy</span><span class="sxs-lookup"><span data-stu-id="a9dfb-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="a9dfb-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="a9dfb-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="a9dfb-120">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="a9dfb-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="a9dfb-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="a9dfb-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
