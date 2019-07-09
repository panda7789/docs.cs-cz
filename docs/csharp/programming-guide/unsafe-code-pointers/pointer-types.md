---
title: Typy ukazatelů – C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.openlocfilehash: 59846affb1eea5bd9d6a80c623eab5e3aa9db87c
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661084"
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="10d84-102">Typy ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="10d84-102">Pointer types (C# Programming Guide)</span></span>

<span data-ttu-id="10d84-103">V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="10d84-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="10d84-104">Deklarace typu ukazatele má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="10d84-104">A pointer type declaration takes one of the following forms:</span></span>

``` csharp
type* identifier;
void* identifier; //allowed but not recommended
```

<span data-ttu-id="10d84-105">Typ určený před `*` na ukazatel typu nazývá **referenční typ**.</span><span class="sxs-lookup"><span data-stu-id="10d84-105">The type specified before the `*` in a pointer type is called the **referent type**.</span></span> <span data-ttu-id="10d84-106">Některé z následujících typů může být typu referenční:</span><span class="sxs-lookup"><span data-stu-id="10d84-106">Any of the following types may be a referent type:</span></span>

- <span data-ttu-id="10d84-107">Libovolný integrální typ: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [bajtů](../../language-reference/builtin-types/integral-numeric-types.md), [krátký](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [dlouhé](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-107">Any integral type: [sbyte](../../language-reference/builtin-types/integral-numeric-types.md), [byte](../../language-reference/builtin-types/integral-numeric-types.md), [short](../../language-reference/builtin-types/integral-numeric-types.md), [ushort](../../language-reference/builtin-types/integral-numeric-types.md), [int](../../language-reference/builtin-types/integral-numeric-types.md), [uint](../../language-reference/builtin-types/integral-numeric-types.md), [long](../../language-reference/builtin-types/integral-numeric-types.md), [ulong](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>
- <span data-ttu-id="10d84-108">Libovolný typ s plovoucí desetinnou čárkou: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-108">Any floating-point type: [float](../../language-reference/builtin-types/floating-point-numeric-types.md), [double](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>
- <span data-ttu-id="10d84-109">[Char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-109">[char](../../language-reference/keywords/char.md).</span></span>
- <span data-ttu-id="10d84-110">[BOOL](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-110">[bool](../../language-reference/keywords/bool.md).</span></span>
- <span data-ttu-id="10d84-111">[desetinné](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-111">[decimal](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>
- <span data-ttu-id="10d84-112">Žádné [výčtu](../../language-reference/keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="10d84-112">Any [enum](../../language-reference/keywords/enum.md) type.</span></span>
- <span data-ttu-id="10d84-113">Jakýkoli typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-113">Any pointer type.</span></span> <span data-ttu-id="10d84-114">Díky tomu výrazy, jako `void**`.</span><span class="sxs-lookup"><span data-stu-id="10d84-114">This allows expressions such as `void**`.</span></span>
- <span data-ttu-id="10d84-115">Jakýkoli typ struktury definované uživatelem, který obsahuje pouze pole nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="10d84-115">Any user-defined struct type that contains fields of unmanaged types only.</span></span>

<span data-ttu-id="10d84-116">Typy ukazatelů nedědí z [objekt](../../language-reference/keywords/object.md) a neexistuje žádná možnost převodu mezi typy ukazatelů a `object`.</span><span class="sxs-lookup"><span data-stu-id="10d84-116">Pointer types do not inherit from [object](../../language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="10d84-117">Dále není pro ukazatele k dispozici podpora zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="10d84-117">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="10d84-118">Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.</span><span class="sxs-lookup"><span data-stu-id="10d84-118">However, you can convert between different pointer types and between pointer types and integral types.</span></span>

<span data-ttu-id="10d84-119">Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (\*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="10d84-119">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="10d84-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="10d84-120">For example:</span></span>

```csharp
int* p1, p2, p3;   // Ok
int *p1, *p2, *p3;   // Invalid in C#
```

<span data-ttu-id="10d84-121">Ukazatel nemůže odkazovat na odkaz nebo do [struktura](../../language-reference/keywords/struct.md) , která obsahuje odkazy, protože odkaz na objekt může být uvolněn i v případě, že ukazatel odkazuje na ni.</span><span class="sxs-lookup"><span data-stu-id="10d84-121">A pointer cannot point to a reference or to a [struct](../../language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="10d84-122">Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-122">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>

<span data-ttu-id="10d84-123">Hodnota proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`.</span><span class="sxs-lookup"><span data-stu-id="10d84-123">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="10d84-124">Následují příklady deklarace typu ukazatele:</span><span class="sxs-lookup"><span data-stu-id="10d84-124">The following are examples of pointer type declarations:</span></span>

|<span data-ttu-id="10d84-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="10d84-125">Example</span></span>|<span data-ttu-id="10d84-126">Popis</span><span class="sxs-lookup"><span data-stu-id="10d84-126">Description</span></span>|
|-------------|-----------------|
|`int* p`|<span data-ttu-id="10d84-127">`p` je ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="10d84-127">`p` is a pointer to an integer.</span></span>|
|`int** p`|<span data-ttu-id="10d84-128">`p` je ukazatel na ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="10d84-128">`p` is a pointer to a pointer to an integer.</span></span>|
|`int*[] p`|<span data-ttu-id="10d84-129">`p` je jednorozměrné pole ukazatelů na celá čísla.</span><span class="sxs-lookup"><span data-stu-id="10d84-129">`p` is a single-dimensional array of pointers to integers.</span></span>|
|`char* p`|<span data-ttu-id="10d84-130">`p` je ukazatel na znak.</span><span class="sxs-lookup"><span data-stu-id="10d84-130">`p` is a pointer to a char.</span></span>|
|`void* p`|<span data-ttu-id="10d84-131">`p` je ukazatel na neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="10d84-131">`p` is a pointer to an unknown type.</span></span>|

<span data-ttu-id="10d84-132">Operátor dereference ukazatele \* lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-132">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="10d84-133">Předpokládejme například následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="10d84-133">For example, consider the following declaration:</span></span>

```csharp
int* myVariable;
```

<span data-ttu-id="10d84-134">Výraz `*myVariable` označuje `int` nalezenou v adrese obsažené v proměnné `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="10d84-134">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>

<span data-ttu-id="10d84-135">Existuje několik příkladů ukazatelů v tématech [fixed Statement](../../language-reference/keywords/fixed-statement.md) a [převody ukazatele](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-135">There are several examples of pointers in the topics [fixed Statement](../../language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span> <span data-ttu-id="10d84-136">V následujícím příkladu `unsafe` – klíčové slovo a `fixed` příkaz a ukazuje, jak zvýšení vnitřního ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-136">The following example uses the `unsafe` keyword and the `fixed` statement, and shows how to increment an interior pointer.</span></span>  <span data-ttu-id="10d84-137">Tento kód spustíte vložením do funkce Main konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="10d84-137">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="10d84-138">Tyto příklady musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) sadu možností kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="10d84-138">These examples must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option set.</span></span>

[!code-csharp[Using pointer types](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#5)]

<span data-ttu-id="10d84-139">Operátor dereference nelze použít na ukazatel typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="10d84-139">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="10d84-140">Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.</span><span class="sxs-lookup"><span data-stu-id="10d84-140">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>

<span data-ttu-id="10d84-141">Ukazatel může mít `null`.</span><span class="sxs-lookup"><span data-stu-id="10d84-141">A pointer can be `null`.</span></span> <span data-ttu-id="10d84-142">Použití operátoru dereference na ukazatele null způsobí chování definované implementací.</span><span class="sxs-lookup"><span data-stu-id="10d84-142">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>

<span data-ttu-id="10d84-143">Předávání ukazatelů mezi metodami může způsobit nedefinované chování.</span><span class="sxs-lookup"><span data-stu-id="10d84-143">Passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="10d84-144">Vezměte v úvahu, která vrací ukazatele místní proměnné prostřednictvím `in`, `out`, nebo `ref` parametr nebo jako výsledek funkce.</span><span class="sxs-lookup"><span data-stu-id="10d84-144">Consider a method that returns a pointer to a local variable through an `in`, `out`, or `ref` parameter or as the function result.</span></span> <span data-ttu-id="10d84-145">Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.</span><span class="sxs-lookup"><span data-stu-id="10d84-145">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>

<span data-ttu-id="10d84-146">V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:</span><span class="sxs-lookup"><span data-stu-id="10d84-146">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>

|<span data-ttu-id="10d84-147">Operátor/Příkaz</span><span class="sxs-lookup"><span data-stu-id="10d84-147">Operator/Statement</span></span>|<span data-ttu-id="10d84-148">Použití</span><span class="sxs-lookup"><span data-stu-id="10d84-148">Use</span></span>|
|-------------------------|---------|
|`*`|<span data-ttu-id="10d84-149">Provádí dereferenci ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-149">Performs pointer indirection.</span></span>|
|`->`|<span data-ttu-id="10d84-150">Zpřístupňuje člen struktury prostřednictvím ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-150">Accesses a member of a struct through a pointer.</span></span>|
|`[]`|<span data-ttu-id="10d84-151">Indexuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="10d84-151">Indexes a pointer.</span></span>|
|`&`|<span data-ttu-id="10d84-152">Získá adresu proměnné.</span><span class="sxs-lookup"><span data-stu-id="10d84-152">Obtains the address of a variable.</span></span>|
|<span data-ttu-id="10d84-153">`++` a `--`</span><span class="sxs-lookup"><span data-stu-id="10d84-153">`++` and `--`</span></span>|<span data-ttu-id="10d84-154">Zvýší a sníží ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-154">Increments and decrements pointers.</span></span>|
|<span data-ttu-id="10d84-155">`+` a `-`</span><span class="sxs-lookup"><span data-stu-id="10d84-155">`+` and `-`</span></span>|<span data-ttu-id="10d84-156">Provádí aritmetické operace ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-156">Performs pointer arithmetic.</span></span>|
|<span data-ttu-id="10d84-157">`==`, `!=`, `<`, `>`, `<=`, a `>=`</span><span class="sxs-lookup"><span data-stu-id="10d84-157">`==`, `!=`, `<`, `>`, `<=`, and `>=`</span></span>|<span data-ttu-id="10d84-158">Porovnává ukazatele.</span><span class="sxs-lookup"><span data-stu-id="10d84-158">Compares pointers.</span></span>|
|[<span data-ttu-id="10d84-159">`stackalloc` – Operátor</span><span class="sxs-lookup"><span data-stu-id="10d84-159">`stackalloc` operator</span></span>](../../language-reference/operators/stackalloc.md)|<span data-ttu-id="10d84-160">Přidělí paměť v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="10d84-160">Allocates memory on the stack.</span></span>|
|[<span data-ttu-id="10d84-161">`fixed` – Příkaz</span><span class="sxs-lookup"><span data-stu-id="10d84-161">`fixed` statement</span></span>](../../language-reference/keywords/fixed-statement.md)|<span data-ttu-id="10d84-162">Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.</span><span class="sxs-lookup"><span data-stu-id="10d84-162">Temporarily fixes a variable so that its address may be found.</span></span>|

<span data-ttu-id="10d84-163">Další informace o ukazatel související operátory, naleznete v tématu [ukazatel související s operátory](../../language-reference/operators/pointer-related-operators.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-163">For more information about pointer related operators, see [Pointer related operators](../../language-reference/operators/pointer-related-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="10d84-164">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10d84-164">C# language specification</span></span>

<span data-ttu-id="10d84-165">Další informace najdete v tématu [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="10d84-165">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="10d84-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10d84-166">See also</span></span>

- [<span data-ttu-id="10d84-167">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="10d84-167">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="10d84-168">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="10d84-168">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="10d84-169">Převody ukazatele</span><span class="sxs-lookup"><span data-stu-id="10d84-169">Pointer Conversions</span></span>](pointer-conversions.md)
- [<span data-ttu-id="10d84-170">Typy</span><span class="sxs-lookup"><span data-stu-id="10d84-170">Types</span></span>](../../language-reference/keywords/types.md)
- [<span data-ttu-id="10d84-171">unsafe</span><span class="sxs-lookup"><span data-stu-id="10d84-171">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
