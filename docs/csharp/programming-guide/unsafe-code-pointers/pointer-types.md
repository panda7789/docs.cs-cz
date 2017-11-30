---
title: "Typy ukazatelů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0699793e91199cc623c0d13e42937c8b919e992a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="98c75-102">Typy ukazatelů (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="98c75-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="98c75-103">V nezabezpečeném kontextu lze jako konkrétní typ použít typ ukazatele, typ hodnoty nebo typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="98c75-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="98c75-104">Deklarace typu ukazatele má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="98c75-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="98c75-105">Typem ukazatele může být jakýkoli z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="98c75-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="98c75-106">[SByte –](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátké](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [ dlouhé](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [dvojité](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), nebo [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="98c75-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="98c75-107">Všechny [výčtu](../../../csharp/language-reference/keywords/enum.md) typu.</span><span class="sxs-lookup"><span data-stu-id="98c75-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="98c75-108">Jakýkoli typ ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="98c75-109">Jakýkoli typ struktury definované uživatelem, který obsahuje pouze pole nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="98c75-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="98c75-110">Typy ukazatelů nedědí z [objekt](../../../csharp/language-reference/keywords/object.md) a neexistují žádné převody mezi typy ukazatelů a `object`.</span><span class="sxs-lookup"><span data-stu-id="98c75-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="98c75-111">Dále není pro ukazatele k dispozici podpora zabalení a rozbalení.</span><span class="sxs-lookup"><span data-stu-id="98c75-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="98c75-112">Můžete však převádět mezi různými typy ukazatele, nebo mezi různými typy ukazatele a integrálními typy.</span><span class="sxs-lookup"><span data-stu-id="98c75-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="98c75-113">Při deklaraci většího počtu ukazatelů ve stejné deklaraci je spolu se základním typem zapsán pouze symbol hvězdičky (*). Nepoužívá se jako předpona u názvů jednotlivých ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="98c75-113">When you declare multiple pointers in the same declaration, the asterisk (*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="98c75-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="98c75-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="98c75-115">Ukazatel nemůže odkazovat na odkaz nebo na [struktura](../../../csharp/language-reference/keywords/struct.md) obsahující odkazy, protože odkaz na objekt může být uvolnění z paměti i v případě, že ukazatel ukazovat na ni.</span><span class="sxs-lookup"><span data-stu-id="98c75-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="98c75-116">Systém uvolňování paměti neukládá přehled o tom, zda na konkrétní objekt neodkazují některé typy ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="98c75-117">Hodnoty proměnné ukazatele typu `myType*` je adresa proměnné typu `myType`.</span><span class="sxs-lookup"><span data-stu-id="98c75-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="98c75-118">Následují příklady deklarace typu ukazatele:</span><span class="sxs-lookup"><span data-stu-id="98c75-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="98c75-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="98c75-119">Example</span></span>|<span data-ttu-id="98c75-120">Popis</span><span class="sxs-lookup"><span data-stu-id="98c75-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="98c75-121">`p`je zde ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="98c75-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="98c75-122">`p`je zde ukazatel na ukazatel na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="98c75-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="98c75-123">`p`je jednorozměrná pole ukazatele na celá čísla.</span><span class="sxs-lookup"><span data-stu-id="98c75-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="98c75-124">`p`je zde ukazatel na char.</span><span class="sxs-lookup"><span data-stu-id="98c75-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="98c75-125">`p`je zde ukazatel na neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="98c75-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="98c75-126">Operátor dereference ukazatele * lze použít pro přístup k obsahu v umístění, na které odkazuje proměnná ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-126">The pointer indirection operator * can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="98c75-127">Předpokládejme například následující deklaraci:</span><span class="sxs-lookup"><span data-stu-id="98c75-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="98c75-128">Výraz `*myVariable` označuje `int` proměnná najít na adrese obsažené v `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="98c75-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="98c75-129">Existuje několik příkladů ukazatele v tématech [příkazu pevnou](../../../csharp/language-reference/keywords/fixed-statement.md) a [převody ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="98c75-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="98c75-130">Následující příklad ukazuje potřebu `unsafe` – klíčové slovo a `fixed` příkaz a jak se zvýší vnitřní ukazatel.</span><span class="sxs-lookup"><span data-stu-id="98c75-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="98c75-131">Tento kód spustíte vložením do funkce Main konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="98c75-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="98c75-132">(Nezapomeňte povolit nezabezpečený kód v **Návrhář projektu**; zvolte **projektu**, **vlastnosti** v nabídce panelu a pak vyberte **povolit nezabezpečený kód** v **sestavení** karta.)</span><span class="sxs-lookup"><span data-stu-id="98c75-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="98c75-133">Deferenční operátor nelze použít pro ukazatel typu `void*`.</span><span class="sxs-lookup"><span data-stu-id="98c75-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="98c75-134">Můžete však použít přetypování neplatného ukazatele a převést jej na jiný typ ukazatele, a naopak.</span><span class="sxs-lookup"><span data-stu-id="98c75-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="98c75-135">Může být ukazatel `null`.</span><span class="sxs-lookup"><span data-stu-id="98c75-135">A pointer can be `null`.</span></span> <span data-ttu-id="98c75-136">Použití operátoru dereference na ukazatele null způsobí chování definované implementací.</span><span class="sxs-lookup"><span data-stu-id="98c75-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="98c75-137">Předávání ukazatelů mezi metodami může způsobit nedefinované chování.</span><span class="sxs-lookup"><span data-stu-id="98c75-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="98c75-138">Příklady vrací ukazatele místní proměnné prostřednictvím parametru Ref nebo Out, nebo jako výsledek funkce.</span><span class="sxs-lookup"><span data-stu-id="98c75-138">Examples are returning a pointer to a local variable through an Out or Ref parameter or as the function result.</span></span> <span data-ttu-id="98c75-139">Pokud byl ukazatel nastaven v pevném bloku, pak proměnná, na kterou odkazuje, již nemusí být pevně stanovená.</span><span class="sxs-lookup"><span data-stu-id="98c75-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="98c75-140">V následující tabulce je uveden seznam operátorů a příkazů, které mohou fungovat u ukazatelů v nezabezpečeném kontextu:</span><span class="sxs-lookup"><span data-stu-id="98c75-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="98c75-141">Operátor/Příkaz</span><span class="sxs-lookup"><span data-stu-id="98c75-141">Operator/Statement</span></span>|<span data-ttu-id="98c75-142">Použití</span><span class="sxs-lookup"><span data-stu-id="98c75-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="98c75-143">Provádí dereferenci ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="98c75-144">Zpřístupňuje člen struktury prostřednictvím ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="98c75-145">[]</span><span class="sxs-lookup"><span data-stu-id="98c75-145">[]</span></span>|<span data-ttu-id="98c75-146">Indexuje ukazatel.</span><span class="sxs-lookup"><span data-stu-id="98c75-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="98c75-147">Získá adresu proměnné.</span><span class="sxs-lookup"><span data-stu-id="98c75-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="98c75-148">++ a --</span><span class="sxs-lookup"><span data-stu-id="98c75-148">++ and --</span></span>|<span data-ttu-id="98c75-149">Zvýší a sníží ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="98c75-150">+ a -</span><span class="sxs-lookup"><span data-stu-id="98c75-150">+ and -</span></span>|<span data-ttu-id="98c75-151">Provádí aritmetické operace ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="98c75-152">==,! =, \<, >, \<=, a > =</span><span class="sxs-lookup"><span data-stu-id="98c75-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="98c75-153">Porovnává ukazatele.</span><span class="sxs-lookup"><span data-stu-id="98c75-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="98c75-154">Přidělí paměť v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="98c75-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="98c75-155">`fixed`příkaz</span><span class="sxs-lookup"><span data-stu-id="98c75-155">`fixed` statement</span></span>|<span data-ttu-id="98c75-156">Dočasně pevně stanoví proměnnou tak, aby bylo možné vyhledat její adresu.</span><span class="sxs-lookup"><span data-stu-id="98c75-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="98c75-157">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98c75-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="98c75-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="98c75-158">See Also</span></span>  
 [<span data-ttu-id="98c75-159">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="98c75-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="98c75-160">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="98c75-160">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="98c75-161">Převody ukazatele</span><span class="sxs-lookup"><span data-stu-id="98c75-161">Pointer Conversions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [<span data-ttu-id="98c75-162">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="98c75-162">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="98c75-163">Typy</span><span class="sxs-lookup"><span data-stu-id="98c75-163">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="98c75-164">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="98c75-164">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="98c75-165">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="98c75-165">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="98c75-166">stackalloc</span><span class="sxs-lookup"><span data-stu-id="98c75-166">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)  
 [<span data-ttu-id="98c75-167">Zabalení a rozbalení</span><span class="sxs-lookup"><span data-stu-id="98c75-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
