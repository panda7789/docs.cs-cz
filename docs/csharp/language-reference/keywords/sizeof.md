---
title: sizeof – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 8bb6d4a37b2eea3060921937cf15a1fdd1be97b4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634001"
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="5638c-102">sizeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5638c-102">sizeof (C# Reference)</span></span>

<span data-ttu-id="5638c-103">Umožňuje získat velikost v bajtech pro nespravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="5638c-103">Used to obtain the size in bytes for an unmanaged type.</span></span>

<span data-ttu-id="5638c-104">Nespravované typy patří:</span><span class="sxs-lookup"><span data-stu-id="5638c-104">Unmanaged types include:</span></span>

- <span data-ttu-id="5638c-105">Jednoduché typy, které jsou uvedeny v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="5638c-105">The simple types that are listed in the following table:</span></span>

   |<span data-ttu-id="5638c-106">Výraz</span><span class="sxs-lookup"><span data-stu-id="5638c-106">Expression</span></span>|<span data-ttu-id="5638c-107">Konstantní hodnota</span><span class="sxs-lookup"><span data-stu-id="5638c-107">Constant value</span></span>|
   |----------------|--------------------|
   |`sizeof(sbyte)`|<span data-ttu-id="5638c-108">1</span><span class="sxs-lookup"><span data-stu-id="5638c-108">1</span></span>|
   |`sizeof(byte)`|<span data-ttu-id="5638c-109">1</span><span class="sxs-lookup"><span data-stu-id="5638c-109">1</span></span>|
   |`sizeof(short)`|<span data-ttu-id="5638c-110">2</span><span class="sxs-lookup"><span data-stu-id="5638c-110">2</span></span>|
   |`sizeof(ushort)`|<span data-ttu-id="5638c-111">2</span><span class="sxs-lookup"><span data-stu-id="5638c-111">2</span></span>|
   |`sizeof(int)`|<span data-ttu-id="5638c-112">4</span><span class="sxs-lookup"><span data-stu-id="5638c-112">4</span></span>|
   |`sizeof(uint)`|<span data-ttu-id="5638c-113">4</span><span class="sxs-lookup"><span data-stu-id="5638c-113">4</span></span>|
   |`sizeof(long)`|<span data-ttu-id="5638c-114">8</span><span class="sxs-lookup"><span data-stu-id="5638c-114">8</span></span>|
   |`sizeof(ulong)`|<span data-ttu-id="5638c-115">8</span><span class="sxs-lookup"><span data-stu-id="5638c-115">8</span></span>|
   |`sizeof(char)`|<span data-ttu-id="5638c-116">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="5638c-116">2 (Unicode)</span></span>|
   |`sizeof(float)`|<span data-ttu-id="5638c-117">4</span><span class="sxs-lookup"><span data-stu-id="5638c-117">4</span></span>|
   |`sizeof(double)`|<span data-ttu-id="5638c-118">8</span><span class="sxs-lookup"><span data-stu-id="5638c-118">8</span></span>|
   |`sizeof(decimal)`|<span data-ttu-id="5638c-119">16</span><span class="sxs-lookup"><span data-stu-id="5638c-119">16</span></span>|
   |`sizeof(bool)`|<span data-ttu-id="5638c-120">1</span><span class="sxs-lookup"><span data-stu-id="5638c-120">1</span></span>|

- <span data-ttu-id="5638c-121">Typy výčtu.</span><span class="sxs-lookup"><span data-stu-id="5638c-121">Enum types.</span></span>

- <span data-ttu-id="5638c-122">Typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="5638c-122">Pointer types.</span></span>

- <span data-ttu-id="5638c-123">Uživatelem definované struktury, které neobsahují žádné instance pole nebo vlastnosti automaticky implementované instance, které jsou odkazové typy nebo sestavené typy.</span><span class="sxs-lookup"><span data-stu-id="5638c-123">User-defined structs that do not contain any instance fields or auto-implemented instance properties that are reference types or constructed types.</span></span>

<span data-ttu-id="5638c-124">Následující příklad ukazuje, jak načíst velikost `int`:</span><span class="sxs-lookup"><span data-stu-id="5638c-124">The following example shows how to retrieve the size of an `int`:</span></span>

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a><span data-ttu-id="5638c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5638c-125">Remarks</span></span>

<span data-ttu-id="5638c-126">Od verze 2.0 jazyka C#, používání `sizeof` jednoduché nebo výčet typů již nevyžaduje zkompilovat kód ve [nebezpečné](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="5638c-126">Starting with version 2.0 of C#, applying `sizeof` to simple or enum types no longer requires that code be compiled in an [unsafe](unsafe.md) context.</span></span>

<span data-ttu-id="5638c-127">`sizeof` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="5638c-127">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="5638c-128">Hodnoty vrácené `sizeof` operátor jsou typu `int`.</span><span class="sxs-lookup"><span data-stu-id="5638c-128">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="5638c-129">V předchozí tabulce jsou uvedeny konstantní hodnoty, které jsou substituovány za `sizeof` výrazy, které mají určité jednoduché typy jako operandy.</span><span class="sxs-lookup"><span data-stu-id="5638c-129">The previous table shows the constant values that are substituted for `sizeof` expressions that have certain simple types as operands.</span></span>

<span data-ttu-id="5638c-130">Pro všechny ostatní typy, včetně struktur, `sizeof` operátor lze použít pouze v nezabezpečené bloky kódu.</span><span class="sxs-lookup"><span data-stu-id="5638c-130">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="5638c-131">Přestože lze použít <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metoda, hodnota vrácená touto metodou není vždy stejná jako hodnota vrácená `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="5638c-131">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="5638c-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> Vrátí velikost po typ byl zařazen, zatímco `sizeof` vrátí velikost tak, jak byl přidělen modulem common language runtime, včetně žádné odsazení.</span><span class="sxs-lookup"><span data-stu-id="5638c-132"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>

## <a name="example"></a><span data-ttu-id="5638c-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="5638c-133">Example</span></span>

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a><span data-ttu-id="5638c-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5638c-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5638c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5638c-135">See also</span></span>

- [<span data-ttu-id="5638c-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5638c-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5638c-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5638c-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5638c-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5638c-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5638c-139">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="5638c-139">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="5638c-140">enum</span><span class="sxs-lookup"><span data-stu-id="5638c-140">enum</span></span>](enum.md)
- [<span data-ttu-id="5638c-141">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="5638c-141">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="5638c-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="5638c-142">Structs</span></span>](../../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="5638c-143">Konstanty</span><span class="sxs-lookup"><span data-stu-id="5638c-143">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)
