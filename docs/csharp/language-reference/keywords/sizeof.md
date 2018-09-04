---
title: sizeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: f2507dd8528e2e66016524873ada890227a74ed8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517035"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="d16f9-102">sizeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d16f9-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="d16f9-103">Umožňuje získat velikost v bajtech pro nespravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="d16f9-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="d16f9-104">Nespravované typy patří:</span><span class="sxs-lookup"><span data-stu-id="d16f9-104">Unmanaged types include:</span></span>

-   <span data-ttu-id="d16f9-105">Jednoduché typy, které jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="d16f9-105">The simple types that are listed in the following table:</span></span>
  
   |<span data-ttu-id="d16f9-106">Výraz</span><span class="sxs-lookup"><span data-stu-id="d16f9-106">Expression</span></span>|<span data-ttu-id="d16f9-107">Konstantní hodnota</span><span class="sxs-lookup"><span data-stu-id="d16f9-107">Constant value</span></span>|  
   |----------------|--------------------|  
   |`sizeof(sbyte)`|<span data-ttu-id="d16f9-108">1</span><span class="sxs-lookup"><span data-stu-id="d16f9-108">1</span></span>|  
   |`sizeof(byte)`|<span data-ttu-id="d16f9-109">1</span><span class="sxs-lookup"><span data-stu-id="d16f9-109">1</span></span>|  
   |`sizeof(short)`|<span data-ttu-id="d16f9-110">2</span><span class="sxs-lookup"><span data-stu-id="d16f9-110">2</span></span>|  
   |`sizeof(ushort)`|<span data-ttu-id="d16f9-111">2</span><span class="sxs-lookup"><span data-stu-id="d16f9-111">2</span></span>|  
   |`sizeof(int)`|<span data-ttu-id="d16f9-112">4</span><span class="sxs-lookup"><span data-stu-id="d16f9-112">4</span></span>|  
   |`sizeof(uint)`|<span data-ttu-id="d16f9-113">4</span><span class="sxs-lookup"><span data-stu-id="d16f9-113">4</span></span>|  
   |`sizeof(long)`|<span data-ttu-id="d16f9-114">8</span><span class="sxs-lookup"><span data-stu-id="d16f9-114">8</span></span>|  
   |`sizeof(ulong)`|<span data-ttu-id="d16f9-115">8</span><span class="sxs-lookup"><span data-stu-id="d16f9-115">8</span></span>|  
   |`sizeof(char)`|<span data-ttu-id="d16f9-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="d16f9-116">2 (Unicode)</span></span>|  
   |`sizeof(float)`|<span data-ttu-id="d16f9-117">4</span><span class="sxs-lookup"><span data-stu-id="d16f9-117">4</span></span>|  
   |`sizeof(double)`|<span data-ttu-id="d16f9-118">8</span><span class="sxs-lookup"><span data-stu-id="d16f9-118">8</span></span>|  
   |`sizeof(decimal)`|<span data-ttu-id="d16f9-119">16</span><span class="sxs-lookup"><span data-stu-id="d16f9-119">16</span></span>|  
   |`sizeof(bool)`|<span data-ttu-id="d16f9-120">1</span><span class="sxs-lookup"><span data-stu-id="d16f9-120">1</span></span>| 
  
-   <span data-ttu-id="d16f9-121">Typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="d16f9-121">Enum types.</span></span>
  
-   <span data-ttu-id="d16f9-122">Typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="d16f9-122">Pointer types.</span></span>
  
-   <span data-ttu-id="d16f9-123">Uživatelem definované struktury, které neobsahují žádné instance pole nebo vlastnosti automaticky implementované instance, které jsou odkazové typy nebo sestavené typy.</span><span class="sxs-lookup"><span data-stu-id="d16f9-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>
  
 <span data-ttu-id="d16f9-124">Následující příklad ukazuje, jak načíst velikost `int`:</span><span class="sxs-lookup"><span data-stu-id="d16f9-124">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="d16f9-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d16f9-125">Remarks</span></span>  
 <span data-ttu-id="d16f9-126">Od verze 2.0 jazyka C#, používání `sizeof` jednoduché nebo výčet typů již nevyžaduje zkompilovat kód ve [nebezpečné](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="d16f9-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>
  
 <span data-ttu-id="d16f9-127">`sizeof` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="d16f9-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="d16f9-128">Hodnoty vrácené `sizeof` operátor jsou typu `int`.</span><span class="sxs-lookup"><span data-stu-id="d16f9-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="d16f9-129">V předchozí tabulce jsou uvedeny konstantní hodnoty, které jsou substituovány za `sizeof` výrazy, které mají určité jednoduché typy jako operandy.</span><span class="sxs-lookup"><span data-stu-id="d16f9-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>  
    
 <span data-ttu-id="d16f9-130">Pro všechny ostatní typy, včetně struktur, `sizeof` operátor lze použít pouze v nezabezpečené bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="d16f9-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="d16f9-131">Přestože lze použít <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metoda, hodnota vrácená touto metodou není vždy stejná jako hodnota vrácená `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="d16f9-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="d16f9-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Vrátí velikost po typ byl zařazen, zatímco `sizeof` vrátí velikost tak, jak byl přidělen modulem common language runtime, včetně žádné odsazení.</span><span class="sxs-lookup"><span data-stu-id="d16f9-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d16f9-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="d16f9-133">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d16f9-134">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d16f9-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d16f9-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="d16f9-135">See Also</span></span>

- [<span data-ttu-id="d16f9-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d16f9-136">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d16f9-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d16f9-137">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d16f9-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d16f9-138">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="d16f9-139">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="d16f9-139">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [<span data-ttu-id="d16f9-140">enum</span><span class="sxs-lookup"><span data-stu-id="d16f9-140">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
- [<span data-ttu-id="d16f9-141">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="d16f9-141">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="d16f9-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="d16f9-142">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
- [<span data-ttu-id="d16f9-143">Konstanty</span><span class="sxs-lookup"><span data-stu-id="d16f9-143">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
