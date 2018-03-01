---
title: "fixed – příkaz (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.assetid: 7ea6db08-ad49-4a7a-b934-d8c4acad1c3a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13633e71c863b075eede41c9a18419d65350bdb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-statement-c-reference"></a><span data-ttu-id="ff2be-102">fixed – příkaz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ff2be-102">fixed Statement (C# Reference)</span></span>
<span data-ttu-id="ff2be-103">`fixed` Příkaz zabrání přemístění mobilní proměnné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ff2be-103">The `fixed` statement prevents the garbage collector from relocating a movable variable.</span></span> <span data-ttu-id="ff2be-104">`fixed` Příkazu je povolená jenom v [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="ff2be-104">The `fixed` statement is only permitted in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="ff2be-105">`Fixed`Můžete také použít k vytvoření [pevnou velikost vyrovnávací paměti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="ff2be-105">`Fixed` can also be used to create [fixed size buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 <span data-ttu-id="ff2be-106">`fixed` Příkaz nastaví ukazatel spravované proměnné a "PIN" tuto proměnnou během provádění příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff2be-106">The `fixed` statement sets a pointer to a managed variable and "pins" that variable during the execution of the statement.</span></span> <span data-ttu-id="ff2be-107">Bez `fixed`, ukazatele na mobilní spravované proměnné by být moc použití, protože uvolňování paměti by mohly přemístit proměnné nepředvídatelné.</span><span class="sxs-lookup"><span data-stu-id="ff2be-107">Without `fixed`, pointers to movable managed variables would be of little use since garbage collection could relocate the variables unpredictably.</span></span> <span data-ttu-id="ff2be-108">Kompilátor jazyka C# pouze umožňuje přiřadit ukazatel spravované proměnné v `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ff2be-108">The C# compiler only lets you assign a pointer to a managed variable in a `fixed` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_1.cs)]  
  
 <span data-ttu-id="ff2be-109">Ukazatel lze inicializovat pomocí pole, řetězec, vyrovnávací paměti pevné velikosti nebo adresy proměnné.</span><span class="sxs-lookup"><span data-stu-id="ff2be-109">You can initialize a pointer by using an array, a string, a fixed-size buffer, or the address of a variable.</span></span> <span data-ttu-id="ff2be-110">Následující příklad ukazuje použití proměnných adresy, pole a řetězce.</span><span class="sxs-lookup"><span data-stu-id="ff2be-110">The following example illustrates the use of variable addresses, arrays, and strings.</span></span> <span data-ttu-id="ff2be-111">Další informace o pevné velikosti vyrovnávací paměti najdete v tématu [pevnou velikost vyrovnávací paměti](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span><span class="sxs-lookup"><span data-stu-id="ff2be-111">For more information about fixed-size buffers, see [Fixed Size Buffers](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md).</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_2.cs)]  
  
 <span data-ttu-id="ff2be-112">Více ukazatele, bude možné inicializovat, dokud nebudou všechny stejného typu.</span><span class="sxs-lookup"><span data-stu-id="ff2be-112">You can initialize multiple pointers, as long as they are all of the same type.</span></span>  
  
```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}  
```
  
 <span data-ttu-id="ff2be-113">K chybě při inicializaci ukazatele různých typů, jednoduše vnořit `fixed` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ff2be-113">To initialize pointers of different types, simply nest `fixed` statements, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_3.cs)]  
  
 <span data-ttu-id="ff2be-114">Po spuštění kódu v příkazu, jsou všechny definovaného proměnné Odepnout a předmět pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ff2be-114">After the code in the statement is executed, any pinned variables are unpinned and subject to garbage collection.</span></span> <span data-ttu-id="ff2be-115">Proto neukazují na tyto proměnné mimo `fixed` příkaz.</span><span class="sxs-lookup"><span data-stu-id="ff2be-115">Therefore, do not point to those variables outside the `fixed` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff2be-116">Ukazatele v pevné příkazy inicializovat nemůže být upraven.</span><span class="sxs-lookup"><span data-stu-id="ff2be-116">Pointers initialized in fixed statements cannot be modified.</span></span>  
  
 <span data-ttu-id="ff2be-117">V režimu unsafe mohou přidělit paměť v zásobníku, kde se nevztahuje uvolňování paměti a proto nemusí být připojena.</span><span class="sxs-lookup"><span data-stu-id="ff2be-117">In unsafe mode, you can allocate memory on the stack, where it is not subject to garbage collection and therefore does not need to be pinned.</span></span> <span data-ttu-id="ff2be-118">Další informace najdete v tématu [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="ff2be-118">For more information, see [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff2be-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff2be-119">Example</span></span>  
 [!code-csharp[csrefKeywordsFixedLock#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/fixed-statement_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ff2be-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff2be-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ff2be-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff2be-121">See Also</span></span>  
 [<span data-ttu-id="ff2be-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff2be-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ff2be-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ff2be-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ff2be-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff2be-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ff2be-125">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="ff2be-125">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="ff2be-126">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="ff2be-126">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
