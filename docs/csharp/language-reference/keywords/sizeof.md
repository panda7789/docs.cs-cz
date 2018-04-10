---
title: sizeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="e6071-102">sizeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e6071-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="e6071-103">Umožňuje získat velikost v bajtech pro typ nespravované.</span><span class="sxs-lookup"><span data-stu-id="e6071-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="e6071-104">Nespravované typy patří vestavěné typy, které jsou uvedeny v následující tabulce a také následující:</span><span class="sxs-lookup"><span data-stu-id="e6071-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="e6071-105">Typy výčtu</span><span class="sxs-lookup"><span data-stu-id="e6071-105">Enum types</span></span>  
  
-   <span data-ttu-id="e6071-106">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e6071-106">Pointer types</span></span>  
  
-   <span data-ttu-id="e6071-107">Uživatelem definované struktury, které neobsahují žádná pole nebo vlastnosti, které jsou odkazové typy</span><span class="sxs-lookup"><span data-stu-id="e6071-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="e6071-108">Následující příklad ukazuje, jak načíst velikost `int`:</span><span class="sxs-lookup"><span data-stu-id="e6071-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="e6071-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6071-109">Remarks</span></span>  
 <span data-ttu-id="e6071-110">Počínaje verzí 2.0 jazyka C#, použití `sizeof` na předdefinované typy už vyžaduje, aby [unsafe](../../../csharp/language-reference/keywords/unsafe.md) režim použít.</span><span class="sxs-lookup"><span data-stu-id="e6071-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="e6071-111">`sizeof` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="e6071-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="e6071-112">Hodnoty vrácené `sizeof` operátor jsou typu `int`.</span><span class="sxs-lookup"><span data-stu-id="e6071-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="e6071-113">V následující tabulce jsou konstantní hodnoty, které jsou nahrazeny pro `sizeof` výrazy, které mají určité vestavěné typy jako operandy.</span><span class="sxs-lookup"><span data-stu-id="e6071-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="e6071-114">Výraz</span><span class="sxs-lookup"><span data-stu-id="e6071-114">Expression</span></span>|<span data-ttu-id="e6071-115">Konstantní hodnota</span><span class="sxs-lookup"><span data-stu-id="e6071-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="e6071-116">1</span><span class="sxs-lookup"><span data-stu-id="e6071-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="e6071-117">1</span><span class="sxs-lookup"><span data-stu-id="e6071-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="e6071-118">2</span><span class="sxs-lookup"><span data-stu-id="e6071-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="e6071-119">2</span><span class="sxs-lookup"><span data-stu-id="e6071-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="e6071-120">4</span><span class="sxs-lookup"><span data-stu-id="e6071-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="e6071-121">4</span><span class="sxs-lookup"><span data-stu-id="e6071-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="e6071-122">8</span><span class="sxs-lookup"><span data-stu-id="e6071-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="e6071-123">8</span><span class="sxs-lookup"><span data-stu-id="e6071-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="e6071-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="e6071-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="e6071-125">4</span><span class="sxs-lookup"><span data-stu-id="e6071-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="e6071-126">8</span><span class="sxs-lookup"><span data-stu-id="e6071-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="e6071-127">16</span><span class="sxs-lookup"><span data-stu-id="e6071-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="e6071-128">1</span><span class="sxs-lookup"><span data-stu-id="e6071-128">1</span></span>|  
  
 <span data-ttu-id="e6071-129">Pro všechny ostatní typy, včetně struktur, `sizeof` operátor lze použít pouze v blocích nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="e6071-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="e6071-130">Přestože je možné použít <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metoda, hodnota vrácená touto metodou není vždy stejná jako hodnota vrácený `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="e6071-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="e6071-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>Vrátí velikost po typ byl zařazen, zatímco `sizeof` vrátí velikost, protože byla přidělena modul common language runtime, včetně všech odsazení.</span><span class="sxs-lookup"><span data-stu-id="e6071-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6071-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6071-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e6071-133">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6071-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6071-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6071-134">See Also</span></span>  
 [<span data-ttu-id="e6071-135">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6071-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e6071-136">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e6071-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e6071-137">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e6071-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e6071-138">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="e6071-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="e6071-139">výčet</span><span class="sxs-lookup"><span data-stu-id="e6071-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="e6071-140">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="e6071-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="e6071-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="e6071-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="e6071-142">Konstanty</span><span class="sxs-lookup"><span data-stu-id="e6071-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
