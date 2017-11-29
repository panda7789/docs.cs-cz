---
title: "Postupy: Získávání adresy proměnné (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="14b9e-102">Postupy: Získávání adresy proměnné (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="14b9e-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="14b9e-103">Získat adresu unární výraz, který vyhodnocuje pevné proměnné, použijte operátor adresy:</span><span class="sxs-lookup"><span data-stu-id="14b9e-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="14b9e-104">Operátor adresy lze použít pouze k proměnné.</span><span class="sxs-lookup"><span data-stu-id="14b9e-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="14b9e-105">Pokud je proměnná přenosné proměnné, můžete použít [příkazu pevnou](../../../csharp/language-reference/keywords/fixed-statement.md) dočasně opravit před získávání adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="14b9e-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="14b9e-106">Je vaší povinností ujistit, že je inicializováno proměnnou.</span><span class="sxs-lookup"><span data-stu-id="14b9e-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="14b9e-107">Kompilátor nevydá chybovou zprávu, pokud není inicializována proměnnou.</span><span class="sxs-lookup"><span data-stu-id="14b9e-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="14b9e-108">Nelze získat adresu konstanta nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="14b9e-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14b9e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="14b9e-109">Example</span></span>  
 <span data-ttu-id="14b9e-110">V tomto příkladu ukazatel na `int`, `p`je deklarovaný a přiřazena adresa proměnná typu integer, `number`.</span><span class="sxs-lookup"><span data-stu-id="14b9e-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="14b9e-111">Proměnná `number` je inicializován v důsledku přiřazení * p.</span><span class="sxs-lookup"><span data-stu-id="14b9e-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="14b9e-112">Pokud provedete tento příkaz přiřazení komentář, inicializace proměnné `number` bude odebrána, ale žádné dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="14b9e-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="14b9e-113">Všimněte si použití [přístup ke členu](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operátor `->` můžete získat a zobrazit adresu uložené v ukazatele.</span><span class="sxs-lookup"><span data-stu-id="14b9e-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="14b9e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="14b9e-114">See Also</span></span>  
 [<span data-ttu-id="14b9e-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="14b9e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="14b9e-116">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="14b9e-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="14b9e-117">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="14b9e-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="14b9e-118">Typy</span><span class="sxs-lookup"><span data-stu-id="14b9e-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="14b9e-119">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="14b9e-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="14b9e-120">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="14b9e-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="14b9e-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="14b9e-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
