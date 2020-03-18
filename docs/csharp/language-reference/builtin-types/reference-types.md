---
title: Předdefinované typy odkazů – odkaz jazyka C#
description: Další informace o typy odkazů, které mají C# klíčová slova, které můžete použít k jejich deklarování.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399642"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="3e1b8-103">Předdefinované typy odkazů (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="3e1b8-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="3e1b8-104">C# má řadu předdefinovaných typů odkazů.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="3e1b8-105">Mají klíčová slova nebo operátory, které jsou synonyma pro typ v knihovně .NET.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span>

## <a name="the-object-type"></a><span data-ttu-id="3e1b8-106">Typ objektu</span><span class="sxs-lookup"><span data-stu-id="3e1b8-106">The object type</span></span>

<span data-ttu-id="3e1b8-107">Tento `object` typ je <xref:System.Object?displayProperty=nameWithType> alias pro v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="3e1b8-108">V systému sjednoceného typu jazyka C# všechny typy, předdefinované a uživatelem definované, <xref:System.Object?displayProperty=nameWithType>typy odkazů a typy hodnot, dědí přímo nebo nepřímo z .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e1b8-109">Proměnným typu `object`můžete přiřadit hodnoty libovolného typu .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="3e1b8-110">Libovolnou `object` proměnnou lze přiřadit k výchozí `null`hodnotě pomocí literálu .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="3e1b8-111">Když je proměnná typu hodnoty převedena na objekt, říká se, že je *zabalená*.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="3e1b8-112">Pokud je proměnná typu `object` převedena na typ hodnoty, říká se, že je *rozbalena*.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-112">When a variable of type `object` is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="3e1b8-113">Další informace naleznete v [tématu Box a rozbalení](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="3e1b8-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="the-string-type"></a><span data-ttu-id="3e1b8-114">Typ řetězce</span><span class="sxs-lookup"><span data-stu-id="3e1b8-114">The string type</span></span>

<span data-ttu-id="3e1b8-115">Typ `string` představuje posloupnost nula nebo více znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="3e1b8-116">`string`je alias <xref:System.String?displayProperty=nameWithType> pro v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="3e1b8-117">Ačkoli `string` je typ odkazu, [operátory `==` rovnosti a `!=` ](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnot `string` objektů, nikoli odkazů.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="3e1b8-118">To umožňuje testování rovnosti řetězců intuitivnější.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="3e1b8-119">Například:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="3e1b8-120">Zobrazí se "True" a pak "False", protože obsah `a` řetězců `b` jsou ekvivalentní, ale neodkazují na stejnou instanci řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="3e1b8-121">[Operátor +](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="3e1b8-122">Tím se vytvoří objekt řetězce, který obsahuje "dobré ráno".</span><span class="sxs-lookup"><span data-stu-id="3e1b8-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="3e1b8-123">Řetězce jsou *neměnné*-- obsah objektu řetězce nelze po vytvoření objektu změnit, i když syntaxe způsobí, že se zobrazí, jako byste to mohli udělat.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="3e1b8-124">Například při psaní tohoto kódu kompilátor ve skutečnosti vytvoří nový objekt řetězce pro uložení nové `b`sekvence znaků a tento nový objekt je přiřazen .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="3e1b8-125">Paměť, která byla přidělena pro `b` (pokud obsahuje řetězec "h") je pak způsobilé pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="3e1b8-126">`[]` [Operátor](../operators/member-access-operators.md#indexer-operator-) lze použít pro přístup jen pro čtení k jednotlivým znakům řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a string.</span></span> <span data-ttu-id="3e1b8-127">Platné hodnoty indexu `0` začínají na a musí být menší než délka řetězce:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-127">Valid index values start at `0` and must be less than the length of the string:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="3e1b8-128">Podobným způsobem může `[]` být operátor také použit pro iterace nad každým znakem v řetězci:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a string:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

<span data-ttu-id="3e1b8-129">Řetězcové literály `string` jsou typu a mohou být `@`zapsány ve dvou formách, citovány a citovány.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="3e1b8-130">Literály řetězce v uvozovkách jsou uzavřeny v uvozovkách ("):</span><span class="sxs-lookup"><span data-stu-id="3e1b8-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="3e1b8-131">Řetězcové literály mohou obsahovat libovolný literál znaku.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-131">String literals can contain any character literal.</span></span> <span data-ttu-id="3e1b8-132">Jsou zahrnuty únikové sekvence.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-132">Escape sequences are included.</span></span> <span data-ttu-id="3e1b8-133">Následující příklad používá `\\` sekvenci `\u0066` escape pro zpětné `\n` lomítko, pro písmeno f a pro nový řádek.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> <span data-ttu-id="3e1b8-134">Řídicí kód `\udddd` (kde `dddd` je čtyřmístné číslo) představuje znak`dddd`Unicode U+ .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="3e1b8-135">Osmmístné únikové kódy Unicode jsou také rozpoznány: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="3e1b8-136">[Literály řetězce doslovný](../tokens/verbatim.md) začíná `@` a jsou také uzavřeny v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="3e1b8-137">Například:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="3e1b8-138">Výhodou doslovných řetězců je, že únikové sekvence *nejsou* zpracovány, což usnadňuje psaní, například plně kvalifikovaný název souboru systému Windows:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="3e1b8-139">Chcete-li do @-quoted řetězce zahrnout dvojité uvozovky, zdvojnásobte je:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="3e1b8-140">Typ delegáta</span><span class="sxs-lookup"><span data-stu-id="3e1b8-140">The delegate type</span></span>

<span data-ttu-id="3e1b8-141">Deklarace typu delegáta je podobná podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="3e1b8-142">Má vrácenou hodnotu a libovolný počet parametrů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="3e1b8-143">V rozhraní `System.Action` .NET a `System.Func` typy poskytují obecné definice pro mnoho běžných delegátů.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="3e1b8-144">Pravděpodobně nebudete muset definovat nové typy vlastních delegátů.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="3e1b8-145">Místo toho můžete vytvořit instance poskytnutých obecných typů.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="3e1b8-146">A `delegate` je typ odkazu, který lze použít k zapouzdření pojmenované nebo anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="3e1b8-147">Delegáti jsou podobné ukazatele funkce v jazyce C++; delegáti jsou však typově bezpečné a zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="3e1b8-148">Aplikace delegátů naleznete v tématu [Delegáti](../../programming-guide/delegates/index.md) a [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3e1b8-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="3e1b8-149">Delegáti jsou základem pro [události](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e1b8-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="3e1b8-150">Delegát může být vytvořena instance tím, že jej přisuzuje buď s pojmenovanou nebo anonymní metodou.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="3e1b8-151">Delegát musí být vytvořena instance s metodou nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="3e1b8-152">Další informace o stupni odchylky, která je povolena v podpisu metody, naleznete [v tématu Odchylka v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3e1b8-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="3e1b8-153">Pro použití s anonymní metody, delegát a kód, který má být přidružen y jsou deklarovány společně.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span>

## <a name="the-dynamic-type"></a><span data-ttu-id="3e1b8-154">Dynamický typ</span><span class="sxs-lookup"><span data-stu-id="3e1b8-154">The dynamic type</span></span>

<span data-ttu-id="3e1b8-155">Typ `dynamic` označuje, že použití proměnné a odkazy na jeho členy obejít kontrolu typu kompilace.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="3e1b8-156">Místo toho jsou tyto operace vyřešeny v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="3e1b8-157">Typ `dynamic` zjednodušuje přístup k rozhraní API modelu COM, jako jsou rozhraní API automatizace sady Office, k dynamickým rozhraním API, jako jsou knihovny IronPython, a k objektovému modelu dokumentu HTML (DOM).</span><span class="sxs-lookup"><span data-stu-id="3e1b8-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="3e1b8-158">Typ `dynamic` se ve `object` většině případů chová jako typ.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="3e1b8-159">Zejména všechny non-null výraz lze převést `dynamic` na typ.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="3e1b8-160">Typ `dynamic` se liší `object` od v tom, že `dynamic` operace, které obsahují výrazy typu nejsou vyřešeny nebo typ kontrolovánkompilátorem.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="3e1b8-161">Kompilátor balíčky společně informace o operaci a tyto informace se později používá k vyhodnocení operace za běhu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="3e1b8-162">Jako součást procesu jsou proměnné `dynamic` typu kompilovány do `object`proměnných typu .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="3e1b8-163">Proto typ `dynamic` existuje pouze v době kompilace, nikoli v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="3e1b8-164">Následující příklad kontrastuje proměnnou `dynamic` typu s `object`proměnnou typu .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="3e1b8-165">Chcete-li ověřit typ každé proměnné v době `dyn` kompilace, umístěte ukazatel myši nad nebo `obj` v příkazech. `WriteLine`</span><span class="sxs-lookup"><span data-stu-id="3e1b8-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="3e1b8-166">Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="3e1b8-167">Technologie IntelliSense `dyn` zobrazuje **dynamické** funkce pro a **objekt** pro . `obj`</span><span class="sxs-lookup"><span data-stu-id="3e1b8-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="3e1b8-168">Příkazy <xref:System.Console.WriteLine%2A> zobrazují typy za `dyn` běhu `obj`a .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="3e1b8-169">V tomto okamžiku mají oba stejný typ, celé číslo.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="3e1b8-170">Vytvoří se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3e1b8-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="3e1b8-171">Chcete-li zobrazit `dyn` `obj` rozdíl mezi a v době kompilace, přidejte následující dva řádky mezi deklarace a `WriteLine` příkazy v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="3e1b8-172">Chyba kompilátoru je hlášena pro pokus o přidání celého čísla a objektu ve výrazu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="3e1b8-173">Pro soubor však `dyn + 3`není hlášena žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="3e1b8-174">Výraz, který `dyn` obsahuje není zaškrtnuto v době `dyn` `dynamic`kompilace, protože typ je .</span><span class="sxs-lookup"><span data-stu-id="3e1b8-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="3e1b8-175">Následující příklad `dynamic` používá v několika deklaracích.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="3e1b8-176">Metoda `Main` také kontrastuje kontrolu typu kompilace s kontrolou typu run-time.</span><span class="sxs-lookup"><span data-stu-id="3e1b8-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="3e1b8-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e1b8-177">See also</span></span>

- [<span data-ttu-id="3e1b8-178">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e1b8-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3e1b8-179">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3e1b8-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="3e1b8-180">Akce</span><span class="sxs-lookup"><span data-stu-id="3e1b8-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="3e1b8-181">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="3e1b8-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="3e1b8-182">Doporučené postupy pro používání řetězců</span><span class="sxs-lookup"><span data-stu-id="3e1b8-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="3e1b8-183">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="3e1b8-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="3e1b8-184">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="3e1b8-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="3e1b8-185">Operátory pro testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="3e1b8-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="3e1b8-186">Jak bezpečně obsazení pomocí porovnávání vzorů a as a je operátory</span><span class="sxs-lookup"><span data-stu-id="3e1b8-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="3e1b8-187">Návod: vytváření a používání dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="3e1b8-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
