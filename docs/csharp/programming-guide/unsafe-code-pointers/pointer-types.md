---
title: Typy ukazatelů – Průvodce programováním v C#
description: Seznamte se s typy ukazatelů. Podívejte se na příklady různých ukazatelů, příklady kódu a zobrazte další dostupné prostředky.
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 9c62a31f9a4a090fe56fb10ac45fe2f93f1b036e
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382032"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="aff1e-104">Typy ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="aff1e-104">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="aff1e-105">V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="aff1e-105">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="aff1e-106">Deklarace typu ukazatele má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="aff1e-106">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="aff1e-107">Typ zadaný před `*` v typu ukazatele se nazývá **typ referenční**.</span><span class="sxs-lookup"><span data-stu-id="aff1e-107">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="aff1e-108">Typ referenční může být pouze [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md) .</span><span class="sxs-lookup"><span data-stu-id="aff1e-108">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="aff1e-109">Typy ukazatelů nedědí z [objektu](../../language-reference/builtin-types/reference-types.md) a neexistují žádné převody mezi typy ukazatelů a `object` .</span><span class="sxs-lookup"><span data-stu-id="aff1e-109">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="aff1e-110">Dále není pro ukazatele k dispozici podpora zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="aff1e-110">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="aff1e-111">Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.</span><span class="sxs-lookup"><span data-stu-id="aff1e-111">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="aff1e-112">Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (\*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="aff1e-112">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="aff1e-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="aff1e-113">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="aff1e-114">Ukazatel nemůže odkazovat na odkaz nebo na [strukturu](../../language-reference/builtin-types/struct.md) , která obsahuje odkazy, protože odkaz na objekt může být uvolněn z paměti i v případě, že na něj odkazuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="aff1e-114">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="aff1e-115">Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-115">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="aff1e-116">Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu `myType` .</span><span class="sxs-lookup"><span data-stu-id="aff1e-116">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="aff1e-117">Následují příklady deklarace typu ukazatele:</span><span class="sxs-lookup"><span data-stu-id="aff1e-117">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="aff1e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="aff1e-118">Example</span></span>|<span data-ttu-id="aff1e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="aff1e-119">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="aff1e-120">`p`je ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="aff1e-120">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="aff1e-121">`p`je ukazatel na ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="aff1e-121">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="aff1e-122">`p`je jednorozměrné pole ukazatelů na celá čísla.</span><span class="sxs-lookup"><span data-stu-id="aff1e-122">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="aff1e-123">`p`je ukazatel na znak.</span><span class="sxs-lookup"><span data-stu-id="aff1e-123">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="aff1e-124">`p`je ukazatel na neznámý typ.</span><span class="sxs-lookup"><span data-stu-id="aff1e-124">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="aff1e-125">Operátor dereference ukazatele \* lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-125">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="aff1e-126">Předpokládejme například následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="aff1e-126">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="aff1e-127">Výraz `*myVariable` označuje `int` proměnnou nalezenou na adrese obsažené v `myVariable` .</span><span class="sxs-lookup"><span data-stu-id="aff1e-127">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="aff1e-128">Existuje několik příkladů ukazatelů v tématech s [příkazy fixed](../../language-reference/keywords/fixed-statement.md) a [převody ukazatelů](./pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="aff1e-128">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="aff1e-129">Následující příklad používá `unsafe` klíčové slovo a `fixed` příkaz a ukazuje, jak zvýšit vnitřní ukazatel.</span><span class="sxs-lookup"><span data-stu-id="aff1e-129">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="aff1e-130">Tento kód spustíte vložením do funkce Main konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="aff1e-130">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="aff1e-131">Tyto příklady musí být kompilovány pomocí sady možností kompilátoru [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="aff1e-131">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](snippets/FixedKeywordExamples.cs#5)]

<span data-ttu-id="aff1e-132">Nemůžete použít operátor dereference na ukazatel typu `void*` .</span><span class="sxs-lookup"><span data-stu-id="aff1e-132">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="aff1e-133">Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.</span><span class="sxs-lookup"><span data-stu-id="aff1e-133">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="aff1e-134">Může to být ukazatel `null` .</span><span class="sxs-lookup"><span data-stu-id="aff1e-134">A pointer can be `null`.</span></span> <span data-ttu-id="aff1e-135">Použití operátoru dereference na ukazatele null způsobí chování definované implementací.</span><span class="sxs-lookup"><span data-stu-id="aff1e-135">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="aff1e-136">Předávání ukazatelů mezi metodami může způsobit nedefinované chování.</span><span class="sxs-lookup"><span data-stu-id="aff1e-136">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="aff1e-137">Zvažte metodu, která vrací ukazatel na místní proměnnou prostřednictvím `in` `out` parametru, nebo `ref` jako výsledek funkce.</span><span class="sxs-lookup"><span data-stu-id="aff1e-137">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="aff1e-138">Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.</span><span class="sxs-lookup"><span data-stu-id="aff1e-138">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="aff1e-139">V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:</span><span class="sxs-lookup"><span data-stu-id="aff1e-139">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="aff1e-140">Operátor/Příkaz</span><span class="sxs-lookup"><span data-stu-id="aff1e-140">Operator/Statement</span></span>|<span data-ttu-id="aff1e-141">Použití</span><span class="sxs-lookup"><span data-stu-id="aff1e-141">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="aff1e-142">Provádí dereferenci ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-142">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="aff1e-143">Zpřístupňuje člen struktury prostřednictvím ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-143">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="aff1e-144">Indexuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="aff1e-144">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="aff1e-145">Získá adresu proměnné.</span><span class="sxs-lookup"><span data-stu-id="aff1e-145">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="aff1e-146">`++` a `--`</span><span class="sxs-lookup"><span data-stu-id="aff1e-146">`++` and `--`</span></span>|<span data-ttu-id="aff1e-147">Zvýší a sníží ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-147">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="aff1e-148">`+` a `-`</span><span class="sxs-lookup"><span data-stu-id="aff1e-148">`+` and `-`</span></span>|<span data-ttu-id="aff1e-149">Provádí aritmetické operace ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-149">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="aff1e-150">`==`, `!=` , `<` , `>` , `<=` a`>=`</span><span class="sxs-lookup"><span data-stu-id="aff1e-150">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="aff1e-151">Porovnává ukazatele.</span><span class="sxs-lookup"><span data-stu-id="aff1e-151">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="aff1e-152">Přidělí paměť v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aff1e-152">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="aff1e-153">`fixed`vydá</span><span class="sxs-lookup"><span data-stu-id="aff1e-153">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="aff1e-154">Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.</span><span class="sxs-lookup"><span data-stu-id="aff1e-154">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="aff1e-155">Další informace o operátorech souvisejících s ukazateli naleznete v tématu [operátory související s ukazatelem](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="aff1e-155">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="aff1e-156">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aff1e-156">C# language specification</span></span>

<span data-ttu-id="aff1e-157">Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="aff1e-157">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aff1e-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aff1e-158">See also</span></span>

- [<span data-ttu-id="aff1e-159">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="aff1e-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aff1e-160">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="aff1e-160">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="aff1e-161">Převody ukazatele</span><span class="sxs-lookup"><span data-stu-id="aff1e-161">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="aff1e-162">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="aff1e-162">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="aff1e-163">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="aff1e-163">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="aff1e-164">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="aff1e-164">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
