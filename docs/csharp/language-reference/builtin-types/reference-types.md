---
title: Vestavěné typy odkazu - C# odkaz
description: Seznamte se s typy odkazů, které mají C# klíčových slov můžete použít k deklaraci.
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
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877195"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="4c1e5-103">Vestavěné typy odkazu (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="4c1e5-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="4c1e5-104">C#má řadu vestavěné typy odkazu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="4c1e5-105">Mají klíčových slov nebo operátorů, které jsou synonyma pro typy v knihovně .NET.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="4c1e5-106">Typ objektu</span><span class="sxs-lookup"><span data-stu-id="4c1e5-106">The object type</span></span>

<span data-ttu-id="4c1e5-107">`object` Typ je alias pro <xref:System.Object?displayProperty=nameWithType> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="4c1e5-108">V systému unified typů jazyka C#, všechny typy, typy odkazů předdefinovaných a definovaný uživatelem, a typů hodnot, dědí přímo nebo nepřímo <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4c1e5-109">Můžete přiřadit proměnné typu hodnoty libovolného typu `object`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="4c1e5-110">Žádné `object` proměnné je možné přiřadit k jeho výchozí hodnotu literálu `null`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="4c1e5-111">Když je proměnné typu hodnoty převeden na objekt, je označen jako *boxed*.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="4c1e5-112">Pokud proměnnou typu objektu je převeden na typ hodnoty, je označen jako *nezabalené*.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-112">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="4c1e5-113">Další informace najdete v tématu [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="4c1e5-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="4c1e5-114">Typ string</span><span class="sxs-lookup"><span data-stu-id="4c1e5-114">The string type</span></span>

<span data-ttu-id="4c1e5-115">`string` Typ představuje posloupnost nula nebo více znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="4c1e5-116">`string` je alias pro <xref:System.String?displayProperty=nameWithType> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="4c1e5-117">I když `string` je typem odkazu [operátory rovnosti `==` a `!=` ](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnoty `string` objekty, ne odkazuje.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="4c1e5-118">Tím je testování rovnosti řetězců intuitivnější.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="4c1e5-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="4c1e5-120">Zobrazí "hodnotu True" a potom "False" protože obsah řetězce jsou ekvivalentní, ale `a` a `b` neodkazují na stejné instanci řetězce.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="4c1e5-121">[+ – Operátor](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="4c1e5-122">Tím se vytvoří objekt string obsahující "good morning".</span><span class="sxs-lookup"><span data-stu-id="4c1e5-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="4c1e5-123">Řetězce jsou *neměnné*– obsah řetězce objektu nelze změnit po vytvoření objektu, přestože je syntaxe zobrazí jako by tomu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="4c1e5-124">Například při psaní tohoto kódu kompilátor ve skutečnosti vytváří nový objekt řetězce pro uchování nového posloupnost znaků, a tento nový objekt je přiřazen k `b`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="4c1e5-125">Paměť, která kdyby byly přiděleny pro `b` (Pokud obsahovala řetězec "h") je pak nárok uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="4c1e5-126">`[]` [Operátor](../operators/member-access-operators.md#indexer-operator-) lze použít pro přístup jen pro čtení k jednotlivé znaky `string`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a `string`.</span></span> <span data-ttu-id="4c1e5-127">Platné hodnoty začínají `0` a musí být menší než délka `string`:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-127">Valid values start at `0` and must be less than the length of the `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="4c1e5-128">Podobně `[]` také lze použít operátor pro iterace přes každý znak v `string`:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a `string`:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="4c1e5-129">Řetězcové literály jsou typu `string` a může být zapsaný ve dvou formách, v uvozovkách a `@`– v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="4c1e5-130">Citovaný řetězec, který literály jsou uzavřeny v dvojitých uvozovkách ("):</span><span class="sxs-lookup"><span data-stu-id="4c1e5-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="4c1e5-131">Řetězcové literály může obsahovat libovolný znak literálu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-131">String literals can contain any character literal.</span></span> <span data-ttu-id="4c1e5-132">Řídicí sekvence jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-132">Escape sequences are included.</span></span> <span data-ttu-id="4c1e5-133">Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` písmenem f, a `\n` pro nový řádek.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="4c1e5-134">Řídicí kód `\udddd` (kde `dddd` je čtyřmístné číslo) představuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="4c1e5-135">Osm číslice sady Unicode řídícími kódy jsou také rozpoznána: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="4c1e5-136">[Literály doslovném řetězci](../tokens/verbatim.md) začínat `@` a jsou také uzavřen do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="4c1e5-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="4c1e5-138">Výhodou doslovném řetězci je, že řídicí sekvence jsou *není* zpracování, což usnadňuje zapsat, například plně kvalifikovaný název souboru Windows:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="4c1e5-139">Zahrnout dvojitých uvozovek na @-quoted řetězec, uveďte ji dvakrát:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="4c1e5-140">Typ delegáta</span><span class="sxs-lookup"><span data-stu-id="4c1e5-140">The delegate type</span></span>

<span data-ttu-id="4c1e5-141">Deklarace typu delegáta je podobná signatuře metody.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="4c1e5-142">Nemá návratovou hodnotu a libovolný počet parametrů typu:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="4c1e5-143">V rozhraní .NET `System.Action` a `System.Func` typy poskytují obecné definice pro mnoho běžných delegátů.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="4c1e5-144">Pravděpodobně není nutné definovat nové typy vlastního delegáta.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="4c1e5-145">Místo toho můžete vytvořit konkretizací poskytnutých obecných typů.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="4c1e5-146">A `delegate` je typem odkazu, který můžete použít k zapouzdření pojmenovaná nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="4c1e5-147">Delegáti jsou podobní ukazatelům na funkci v jazyce C++; Delegáti jsou však typově bezpečné a zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="4c1e5-148">Aplikace delegátů viz [delegáti](../../programming-guide/delegates/index.md) a [obecných delegátů](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c1e5-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="4c1e5-149">Delegáti jsou základem [události](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c1e5-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="4c1e5-150">Delegát může být vytvořena tím, že přidružíte buď pomocí pojmenovaných nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="4c1e5-151">Delegát musí být vytvořena pomocí metody nebo lambda výraz, který je kompatibilní návratový typ a vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="4c1e5-152">Další informace o stupeň odchylky, který je povolen v podpisu metody, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="4c1e5-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="4c1e5-153">Pro použití s anonymní metody delegáta a kód k ní být přidruženo jsou deklarovány společně.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="4c1e5-154">Dynamický typ.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-154">The dynamic type</span></span>

<span data-ttu-id="4c1e5-155">`dynamic` Typ Určuje, které používají proměnné a odkazy na jeho kontrola typu v době kompilace členy jednorázové přihlášení.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="4c1e5-156">Tyto operace jsou místo toho přeložit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="4c1e5-157">`dynamic` Typ zjednodušuje přístup k rozhraní API modelu COM, jako je například rozhraní API Office automatizace, dynamické rozhraní API, například knihovny IronPython a do HTML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="4c1e5-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="4c1e5-158">Typ `dynamic` se chová jako typ `object` ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="4c1e5-159">Konkrétně lze převést libovolný výraz jinou hodnotu než null na `dynamic` typu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="4c1e5-160">`dynamic` Typ se liší od `object` v této operace, které obsahují výrazy typu `dynamic` se nevyřeší nebo typ zaškrtnutí kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="4c1e5-161">Čas spuštění kompilátoru balíčky, které společně informace o operaci a tyto informace se později používá k vyhodnocení operaci.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="4c1e5-162">Jako součást procesu proměnné typu `dynamic` jsou kompilovány do proměnné typu `object`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="4c1e5-163">Proto zadejte `dynamic` existuje pouze v době kompilace, ne za běhu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="4c1e5-164">V následujícím příkladu se liší od proměnné typu `dynamic` na proměnnou typu `object`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="4c1e5-165">Ověření typu každou proměnnou v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v `WriteLine` příkazy.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="4c1e5-166">Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="4c1e5-167">Technologie IntelliSense zobrazuje **dynamické** pro `dyn` a **objekt** pro `obj`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="4c1e5-168"><xref:System.Console.WriteLine%2A> Příkazy zobrazuje typy za běhu `dyn` a `obj`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="4c1e5-169">V tomto okamžiku mají stejný typ celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="4c1e5-170">Následující výstup je vytvořen:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="4c1e5-171">Pokud chcete zobrazit rozdíl mezi `dyn` a `obj` v době kompilace, přidejte následující dva řádky mezi prohlášení a `WriteLine` příkazů v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="4c1e5-172">Chyba kompilátoru hlášené pro pokus o přidání celého čísla a objekt ve výrazu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="4c1e5-173">Však žádná chybová zpráva pro `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="4c1e5-174">Výraz, který obsahuje `dyn` nepovolenou v době kompilace, protože typ `dyn` je `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="4c1e5-175">Následující příklad používá `dynamic` v několika deklarace.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="4c1e5-176">`Main` Metoda se také liší od typu v době kompilace kontroly s kontrolu typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="4c1e5-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="4c1e5-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c1e5-177">See also</span></span>

- [<span data-ttu-id="4c1e5-178">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c1e5-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c1e5-179">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c1e5-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="4c1e5-180">Události</span><span class="sxs-lookup"><span data-stu-id="4c1e5-180">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="4c1e5-181">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="4c1e5-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="4c1e5-182">Doporučené postupy pro používání řetězců</span><span class="sxs-lookup"><span data-stu-id="4c1e5-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="4c1e5-183">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="4c1e5-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="4c1e5-184">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="4c1e5-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="4c1e5-185">Typové zkoušky a převod operátorů</span><span class="sxs-lookup"><span data-stu-id="4c1e5-185">Type-testing and conversion operators</span></span>](../operators/type-testing-and-conversion-operators.md)
- [<span data-ttu-id="4c1e5-186">Postupy: bezpečné přetypování pomocí porovnávání vzorů a jako operátorů a is</span><span class="sxs-lookup"><span data-stu-id="4c1e5-186">How to: safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="4c1e5-187">Návod: vytváření a používání dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="4c1e5-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
