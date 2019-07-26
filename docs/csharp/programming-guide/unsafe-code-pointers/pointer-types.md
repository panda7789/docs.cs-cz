---
title: Typy ukazatelů – C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 704af9aae23571abdb82ae851066e3c03dbe7161
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433548"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="801af-102">Typy ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="801af-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="801af-103">V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="801af-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="801af-104">Deklarace typu ukazatele má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="801af-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="801af-105">Typ zadaný před `*` v typu ukazatele se nazývá **typ referenční**.</span><span class="sxs-lookup"><span data-stu-id="801af-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="801af-106">Typ referenční může být pouze [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md) .</span><span class="sxs-lookup"><span data-stu-id="801af-106">Only an [unmanaged type](../../language-reference/builtin-types/unmanaged-types.md) can be a referent type.</span></span>

<span data-ttu-id="801af-107">Typy ukazatelů nedědí z [objektu](../../language-reference/keywords/object.md) a neexistují žádné převody mezi typy ukazatelů a `object`.</span><span class="sxs-lookup"><span data-stu-id="801af-107">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="801af-108">Dále není pro ukazatele k dispozici podpora zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="801af-108">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="801af-109">Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.</span><span class="sxs-lookup"><span data-stu-id="801af-109">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="801af-110">Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (\*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="801af-110">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="801af-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="801af-111">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="801af-112">Ukazatel nemůže odkazovat na odkaz nebo na [strukturu](../../language-reference/keywords/struct.md) , která obsahuje odkazy, protože odkaz na objekt může být uvolněn z paměti i v případě, že na něj odkazuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="801af-112">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="801af-113">Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-113">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="801af-114">Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu. `myType`</span><span class="sxs-lookup"><span data-stu-id="801af-114">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="801af-115">Následují příklady deklarace typu ukazatele:</span><span class="sxs-lookup"><span data-stu-id="801af-115">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="801af-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="801af-116">Example</span></span>|<span data-ttu-id="801af-117">Popis</span><span class="sxs-lookup"><span data-stu-id="801af-117">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="801af-118">`p`je ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="801af-118">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="801af-119">`p`je ukazatel na ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="801af-119">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="801af-120">`p`je jednorozměrné pole ukazatelů na celá čísla.</span><span class="sxs-lookup"><span data-stu-id="801af-120">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="801af-121">`p`je ukazatel na znak.</span><span class="sxs-lookup"><span data-stu-id="801af-121">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="801af-122">`p`je ukazatel na neznámý typ.</span><span class="sxs-lookup"><span data-stu-id="801af-122">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="801af-123">Operátor dereference ukazatele \* lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-123">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="801af-124">Předpokládejme například následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="801af-124">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="801af-125">Výraz `*myVariable` `myVariable`označuje `int` proměnnou nalezenou na adrese obsažené v.</span><span class="sxs-lookup"><span data-stu-id="801af-125">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="801af-126">Existuje několik příkladů ukazatelů v tématech s [příkazy fixed](../../language-reference/keywords/fixed-statement.md) a [převody ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="801af-126">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="801af-127">Následující příklad používá `unsafe` klíčové slovo `fixed` a příkaz a ukazuje, jak zvýšit vnitřní ukazatel.</span><span class="sxs-lookup"><span data-stu-id="801af-127">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="801af-128">Tento kód spustíte vložením do funkce Main konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="801af-128">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="801af-129">Tyto příklady musí být kompilovány pomocí sady možností kompilátoru [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="801af-129">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="801af-130">Nemůžete použít operátor dereference na ukazatel typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="801af-130">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="801af-131">Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.</span><span class="sxs-lookup"><span data-stu-id="801af-131">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="801af-132">Může to být `null`ukazatel.</span><span class="sxs-lookup"><span data-stu-id="801af-132">A pointer can be `null`.</span></span> <span data-ttu-id="801af-133">Použití operátoru dereference na ukazatele null způsobí chování definované implementací.</span><span class="sxs-lookup"><span data-stu-id="801af-133">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="801af-134">Předávání ukazatelů mezi metodami může způsobit nedefinované chování.</span><span class="sxs-lookup"><span data-stu-id="801af-134">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="801af-135">Zvažte metodu, která vrací ukazatel na místní proměnnou prostřednictvím `in`parametru, `out`nebo `ref` jako výsledek funkce.</span><span class="sxs-lookup"><span data-stu-id="801af-135">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="801af-136">Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.</span><span class="sxs-lookup"><span data-stu-id="801af-136">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="801af-137">V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:</span><span class="sxs-lookup"><span data-stu-id="801af-137">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="801af-138">Operátor/Příkaz</span><span class="sxs-lookup"><span data-stu-id="801af-138">Operator/Statement</span></span>|<span data-ttu-id="801af-139">Použití</span><span class="sxs-lookup"><span data-stu-id="801af-139">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="801af-140">Provádí dereferenci ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-140">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="801af-141">Zpřístupňuje člen struktury prostřednictvím ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-141">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="801af-142">Indexuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="801af-142">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="801af-143">Získá adresu proměnné.</span><span class="sxs-lookup"><span data-stu-id="801af-143">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="801af-144">`++` a `--`</span><span class="sxs-lookup"><span data-stu-id="801af-144">`++` and `--`</span></span>|<span data-ttu-id="801af-145">Zvýší a sníží ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-145">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="801af-146">`+` a `-`</span><span class="sxs-lookup"><span data-stu-id="801af-146">`+` and `-`</span></span>|<span data-ttu-id="801af-147">Provádí aritmetické operace ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-147">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="801af-148">`==`, `!=` ,`<`, ,a`>` `<=``>=`</span><span class="sxs-lookup"><span data-stu-id="801af-148">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="801af-149">Porovnává ukazatele.</span><span class="sxs-lookup"><span data-stu-id="801af-149">Compares pointers.</span></span>|
|[<span data-ttu-id="801af-150">`stackalloc`podnikatel</span><span class="sxs-lookup"><span data-stu-id="801af-150">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="801af-151">Přidělí paměť v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="801af-151">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="801af-152">`fixed`vydá</span><span class="sxs-lookup"><span data-stu-id="801af-152">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="801af-153">Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.</span><span class="sxs-lookup"><span data-stu-id="801af-153">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="801af-154">Další informace o operátorech souvisejících s ukazateli naleznete v tématu [operátory související s ukazatelem](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="801af-154">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="801af-155">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="801af-155">C# language specification</span></span>

<span data-ttu-id="801af-156">Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="801af-156">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="801af-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="801af-157">See also</span></span>

- [<span data-ttu-id="801af-158">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="801af-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="801af-159">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="801af-159">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="801af-160">Převody ukazatele</span><span class="sxs-lookup"><span data-stu-id="801af-160">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="801af-161">Typy</span><span class="sxs-lookup"><span data-stu-id="801af-161">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="801af-162">unsafe</span><span class="sxs-lookup"><span data-stu-id="801af-162">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
