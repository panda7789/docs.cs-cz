---
title: Typy ukazatelů – průvodce programováním jazyka C#
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 7bbfa6b2238458d3248da830cf9d6ac36551b431
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507032"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="6bf1a-102">Typy ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="6bf1a-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="6bf1a-103">V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="6bf1a-104">Deklarace typu ukazatele má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="6bf1a-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="6bf1a-105">Typ zadaný `*` před typem ukazatele v typu se nazývá **referenční typ**.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="6bf1a-106">Pouze [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md) může být referenční typ.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="6bf1a-107">Typy ukazatelů nedědí z [objektu](../../language-reference/builtin-types/reference-types.md) a neexistují `object`žádné převody mezi typy ukazatelů a .</span><span class="sxs-lookup"><span data-stu-id="6bf1a-107">Pointer types do not inherit from [object](../../language-reference/builtin-types/reference-types.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="6bf1a-108">Dále není pro ukazatele k dispozici podpora zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="6bf1a-109">Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="6bf1a-110">Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (\*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="6bf1a-111">Například:</span><span class="sxs-lookup"><span data-stu-id="6bf1a-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="6bf1a-112">Ukazatel nemůže odkazovat na odkaz nebo [strukturu,](../../language-reference/builtin-types/struct.md) která obsahuje odkazy, protože odkaz na objekt může být uvolněno i v případě, že na něj ukazuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-112">A pointer cannot point to a reference or to a [struct](../../language-reference/builtin-types/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="6bf1a-113">Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="6bf1a-114">Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="6bf1a-115">Následují příklady deklarace typu ukazatele:</span><span class="sxs-lookup"><span data-stu-id="6bf1a-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="6bf1a-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="6bf1a-116">Example</span></span>|<span data-ttu-id="6bf1a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6bf1a-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="6bf1a-118">`p`je ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="6bf1a-119">`p`je ukazatel na ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="6bf1a-120">`p`je jednorozměrné pole ukazatelů na celá čísla.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="6bf1a-121">`p`je ukazatel na znak.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="6bf1a-122">`p`je ukazatel na neznámý typ.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="6bf1a-123">Operátor dereference ukazatele \* lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="6bf1a-124">Předpokládejme například následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="6bf1a-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="6bf1a-125">Výraz `*myVariable` označuje proměnnou `int` nalezenou na adrese `myVariable`obsažené v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="6bf1a-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="6bf1a-126">Existuje několik příkladů ukazatelů v tématech [pevné prohlášení](../../language-reference/keywords/fixed-statement.md) a [ukazatel převody](./pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="6bf1a-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](./pointer-conversions.md).</span></span> <span data-ttu-id="6bf1a-127">Následující příklad používá `unsafe` klíčové `fixed` slovo a příkaz a ukazuje, jak se zpřímí vnitřní ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="6bf1a-128">Tento kód spustíte vložením do funkce Main konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="6bf1a-129">Tyto příklady musí být zkompilovány s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler sada možností.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="6bf1a-130">Operátor dereference nelze použít na ukazatel `void*`typu .</span><span class="sxs-lookup"><span data-stu-id="6bf1a-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="6bf1a-131">Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="6bf1a-132">Ukazatel může `null`být .</span><span class="sxs-lookup"><span data-stu-id="6bf1a-132">A pointer can be `null`.</span></span> <span data-ttu-id="6bf1a-133">Použití operátoru dereference na ukazatele null způsobí chování definované implementací.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="6bf1a-134">Předávání ukazatelů mezi metodami může způsobit nedefinované chování.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="6bf1a-135">Zvažte metodu, která vrací ukazatel `in`na `out`místní `ref` proměnnou prostřednictvím , nebo parametr nebo jako výsledek funkce.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="6bf1a-136">Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="6bf1a-137">V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:</span><span class="sxs-lookup"><span data-stu-id="6bf1a-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="6bf1a-138">Operátor/Příkaz</span><span class="sxs-lookup"><span data-stu-id="6bf1a-138">Operator/Statement</span></span>|<span data-ttu-id="6bf1a-139">Použití</span><span class="sxs-lookup"><span data-stu-id="6bf1a-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="6bf1a-140">Provádí dereferenci ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="6bf1a-141">Zpřístupňuje člen struktury prostřednictvím ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="6bf1a-142">Indexuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="6bf1a-143">Získá adresu proměnné.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="6bf1a-144">`++` a `--`</span><span class="sxs-lookup"><span data-stu-id="6bf1a-144">`++` and `--`</span></span>|<span data-ttu-id="6bf1a-145">Zvýší a sníží ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="6bf1a-146">`+` a `-`</span><span class="sxs-lookup"><span data-stu-id="6bf1a-146">`+` and `-`</span></span>|<span data-ttu-id="6bf1a-147">Provádí aritmetické operace ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="6bf1a-148">`==`, `!=` `<`, `>` `<=`, , a`>=`</span><span class="sxs-lookup"><span data-stu-id="6bf1a-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="6bf1a-149">Porovnává ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-149">Compares pointers.</span></span>|
|[`stackalloc`](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="6bf1a-150">Přidělí paměť v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-150">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="6bf1a-151">`fixed`Prohlášení</span><span class="sxs-lookup"><span data-stu-id="6bf1a-151">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="6bf1a-152">Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.</span><span class="sxs-lookup"><span data-stu-id="6bf1a-152">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="6bf1a-153">Další informace o operátorech souvisejících s ukazatelem naleznete v [tématu Ukazatele související operátory](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="6bf1a-153">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6bf1a-154">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6bf1a-154">C# language specification</span></span>

<span data-ttu-id="6bf1a-155">Další informace naleznete v části [Typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6bf1a-155">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6bf1a-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bf1a-156">See also</span></span>

- [<span data-ttu-id="6bf1a-157">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6bf1a-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6bf1a-158">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="6bf1a-158">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="6bf1a-159">Převody ukazatele</span><span class="sxs-lookup"><span data-stu-id="6bf1a-159">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="6bf1a-160">Referenční typy</span><span class="sxs-lookup"><span data-stu-id="6bf1a-160">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="6bf1a-161">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="6bf1a-161">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
- [<span data-ttu-id="6bf1a-162">unsafe</span><span class="sxs-lookup"><span data-stu-id="6bf1a-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
