---
title: Předdefinované typy odkazů – C# referenční informace
description: Přečtěte si informace o typech C# odkazů, které mají klíčová slova, která můžete použít k jejich deklaraci.
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
ms.openlocfilehash: d5ca0593d802d331d980cf35c701e0a79d54abee
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163095"
---
# <a name="built-in-reference-types-c-reference"></a><span data-ttu-id="15b99-103">Předdefinované typy odkazů (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="15b99-103">Built-in reference types (C# reference)</span></span>

<span data-ttu-id="15b99-104">C#má několik předdefinovaných typů odkazů.</span><span class="sxs-lookup"><span data-stu-id="15b99-104">C# has a number of built-in reference types.</span></span> <span data-ttu-id="15b99-105">Mají klíčová slova nebo operátory, které jsou synonyma pro typ v knihovně .NET.</span><span class="sxs-lookup"><span data-stu-id="15b99-105">They have keywords or operators that are synonyms for a type in the .NET library.</span></span> 

## <a name="the-object-type"></a><span data-ttu-id="15b99-106">Typ objektu</span><span class="sxs-lookup"><span data-stu-id="15b99-106">The object type</span></span>

<span data-ttu-id="15b99-107">`object` typ je alias pro <xref:System.Object?displayProperty=nameWithType> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="15b99-107">The `object` type is an alias for <xref:System.Object?displayProperty=nameWithType> in .NET.</span></span> <span data-ttu-id="15b99-108">V rámci sjednoceného typu systému C#jsou všechny typy, předdefinované a uživatelsky definované typy odkazů a typy hodnot děděny přímo nebo nepřímo z <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15b99-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="15b99-109">K proměnným typu `object`můžete přiřadit hodnoty libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="15b99-109">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="15b99-110">K výchozí hodnotě lze pomocí `null`literálů přiřadit jakoukoli `object` proměnnou.</span><span class="sxs-lookup"><span data-stu-id="15b99-110">Any `object` variable can be assigned to its default value using the literal `null`.</span></span> <span data-ttu-id="15b99-111">Když je proměnná typu hodnoty převedena na typ Object, je označována jako *zabalená*.</span><span class="sxs-lookup"><span data-stu-id="15b99-111">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="15b99-112">Je-li proměnná typu `object` převedena na typ hodnoty, je označována jako *nezabaleno*.</span><span class="sxs-lookup"><span data-stu-id="15b99-112">When a variable of type `object` is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="15b99-113">Další informace naleznete v tématu [zabalení a rozbalení](../../programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="15b99-113">For more information, see [Boxing and Unboxing](../../programming-guide/types/boxing-and-unboxing.md).</span></span> 

## <a name="the-string-type"></a><span data-ttu-id="15b99-114">Typ řetězce</span><span class="sxs-lookup"><span data-stu-id="15b99-114">The string type</span></span>

<span data-ttu-id="15b99-115">Typ `string` představuje sekvenci nula nebo více znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="15b99-115">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="15b99-116">`string` je alias pro <xref:System.String?displayProperty=nameWithType> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="15b99-116">`string` is an alias for <xref:System.String?displayProperty=nameWithType> in .NET.</span></span>

<span data-ttu-id="15b99-117">I když je `string` odkazový typ, [operátory rovnosti `==` a `!=`](../operators/equality-operators.md#string-equality) jsou definovány pro porovnání hodnot `string` objektů, nikoli odkazů.</span><span class="sxs-lookup"><span data-stu-id="15b99-117">Although `string` is a reference type, the [equality operators `==` and `!=`](../operators/equality-operators.md#string-equality) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="15b99-118">Díky tomu je testování rovnosti řetězců intuitivnější.</span><span class="sxs-lookup"><span data-stu-id="15b99-118">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="15b99-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="15b99-119">For example:</span></span>

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

<span data-ttu-id="15b99-120">Zobrazí se hodnota "true" a potom "false", protože obsah řetězců je ekvivalentní, ale `a` a `b` neodkazují na stejnou instanci řetězce.</span><span class="sxs-lookup"><span data-stu-id="15b99-120">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="15b99-121">[Operátor +](../operators/addition-operator.md#string-concatenation) zřetězí řetězce:</span><span class="sxs-lookup"><span data-stu-id="15b99-121">The [+ operator](../operators/addition-operator.md#string-concatenation) concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="15b99-122">Tím se vytvoří objekt String, který obsahuje "Dobré ráno".</span><span class="sxs-lookup"><span data-stu-id="15b99-122">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="15b99-123">Řetězce jsou *neměnné*– obsah objektu String nelze po vytvoření objektu změnit, i když se syntaxe zobrazí jako v případě, že to můžete provést.</span><span class="sxs-lookup"><span data-stu-id="15b99-123">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="15b99-124">Například při psaní tohoto kódu kompilátor ve skutečnosti vytvoří nový objekt String pro uložení nové sekvence znaků a tento nový objekt je přiřazen `b`.</span><span class="sxs-lookup"><span data-stu-id="15b99-124">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to `b`.</span></span> <span data-ttu-id="15b99-125">Paměť, která byla přidělena pro `b` (je-li obsažena v řetězci "h"), je pak způsobila pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="15b99-125">The memory that had been allocated for `b` (when it contained the string "h") is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="15b99-126">[Operátor](../operators/member-access-operators.md#indexer-operator-) `[]` lze použít pro přístup jen pro čtení k jednotlivým znakům řetězce.</span><span class="sxs-lookup"><span data-stu-id="15b99-126">The `[]` [operator](../operators/member-access-operators.md#indexer-operator-) can be used for readonly access to individual characters of a string.</span></span> <span data-ttu-id="15b99-127">Platné hodnoty indexu začínají na `0` a musí být menší než délka řetězce:</span><span class="sxs-lookup"><span data-stu-id="15b99-127">Valid index values start at `0` and must be less than the length of the string:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="15b99-128">Podobným způsobem lze operátor `[]` použít také pro iteraci každého znaku v řetězci:</span><span class="sxs-lookup"><span data-stu-id="15b99-128">In similar fashion, the `[]` operator can also be used for iterating over each character in a string:</span></span>

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

<span data-ttu-id="15b99-129">Řetězcové literály jsou typu `string` a lze je zapsat ve dvou formulářích, v uvozovkách a `@`.</span><span class="sxs-lookup"><span data-stu-id="15b99-129">String literals are of type `string` and can be written in two forms, quoted and `@`-quoted.</span></span> <span data-ttu-id="15b99-130">Řetězcové literály v uvozovkách jsou uzavřeny v uvozovkách ("):</span><span class="sxs-lookup"><span data-stu-id="15b99-130">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="15b99-131">Řetězcové literály můžou obsahovat libovolný znakový literál.</span><span class="sxs-lookup"><span data-stu-id="15b99-131">String literals can contain any character literal.</span></span> <span data-ttu-id="15b99-132">K dispozici jsou řídicí sekvence.</span><span class="sxs-lookup"><span data-stu-id="15b99-132">Escape sequences are included.</span></span> <span data-ttu-id="15b99-133">Následující příklad používá řídicí sekvenci `\\` pro zpětné lomítko, `\u0066` pro písmeno f a `\n` pro nový řádek.</span><span class="sxs-lookup"><span data-stu-id="15b99-133">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> <span data-ttu-id="15b99-134">Řídicí kód `\udddd` (kde `dddd` je číslo se čtyřmi číslicemi) představuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="15b99-134">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="15b99-135">Rozpoznávají se také osmimístného kódů Escape Unicode: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="15b99-135">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="15b99-136">[Doslovné řetězce literálů](../tokens/verbatim.md) začínají `@` a jsou také uzavřeny v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="15b99-136">[Verbatim string literals](../tokens/verbatim.md) start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="15b99-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="15b99-137">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="15b99-138">Výhodou doslovného řetězce je, že řídicí sekvence *nejsou zpracovávány* , což usnadňuje psaní, například plně kvalifikovaného názvu souboru systému Windows:</span><span class="sxs-lookup"><span data-stu-id="15b99-138">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified Windows file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="15b99-139">Pokud chcete do řetězce @-quoted přidat dvojitou uvozovku, poklikejte na ni:</span><span class="sxs-lookup"><span data-stu-id="15b99-139">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a><span data-ttu-id="15b99-140">Typ delegáta</span><span class="sxs-lookup"><span data-stu-id="15b99-140">The delegate type</span></span>

<span data-ttu-id="15b99-141">Deklarace typu delegáta je podobná podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="15b99-141">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="15b99-142">Má návratovou hodnotu a libovolný počet parametrů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="15b99-142">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

<span data-ttu-id="15b99-143">V rozhraní .NET typy `System.Action` a `System.Func` poskytují obecné definice pro mnoho běžných delegátů.</span><span class="sxs-lookup"><span data-stu-id="15b99-143">In .NET, `System.Action` and `System.Func` types provide generic definitions for many common delegates.</span></span> <span data-ttu-id="15b99-144">Pravděpodobně nebudete muset definovat nové vlastní typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="15b99-144">You likely don't need to define new custom delegate types.</span></span> <span data-ttu-id="15b99-145">Místo toho můžete vytvořit instance poskytnutých obecných typů.</span><span class="sxs-lookup"><span data-stu-id="15b99-145">Instead, you can create instantiations of the provided generic types.</span></span>

<span data-ttu-id="15b99-146">`delegate` je odkazový typ, který lze použít k zapouzdření pojmenované nebo anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="15b99-146">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="15b99-147">Delegáti jsou podobní ukazatelům funkcí C++v nástroji; Delegáti jsou však typově bezpečné a zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="15b99-147">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="15b99-148">Pro aplikace delegátů, přečtěte si téma [Delegáti](../../programming-guide/delegates/index.md) a [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="15b99-148">For applications of delegates, see [Delegates](../../programming-guide/delegates/index.md) and [Generic Delegates](../../programming-guide/generics/generic-delegates.md).</span></span> <span data-ttu-id="15b99-149">Delegáti jsou základem pro [události](../../programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="15b99-149">Delegates are the basis for [Events](../../programming-guide/events/index.md).</span></span> <span data-ttu-id="15b99-150">Pro delegáta se dá vytvořit instance, a to tak, že ho přidružíte k pojmenované nebo anonymní metodě.</span><span class="sxs-lookup"><span data-stu-id="15b99-150">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span>

<span data-ttu-id="15b99-151">Pro delegáta musí být vytvořená metoda nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="15b99-151">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="15b99-152">Další informace o stupni odchylky, která je povolena v signatuře metody, naleznete v tématu [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="15b99-152">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="15b99-153">Pro použití s anonymními metodami, delegát a kód, který je k němu přidružen, jsou deklarovány společně.</span><span class="sxs-lookup"><span data-stu-id="15b99-153">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> 

## <a name="the-dynamic-type"></a><span data-ttu-id="15b99-154">Dynamický typ</span><span class="sxs-lookup"><span data-stu-id="15b99-154">The dynamic type</span></span>

<span data-ttu-id="15b99-155">Typ `dynamic` označuje, že použití proměnné a odkazů na její členy vynechává kontrolu typu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="15b99-155">The `dynamic` type indicates that use of the variable and references to its members bypass compile-time type checking.</span></span> <span data-ttu-id="15b99-156">Místo toho se tyto operace vyřeší za běhu.</span><span class="sxs-lookup"><span data-stu-id="15b99-156">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="15b99-157">Typ `dynamic` zjednodušuje přístup k rozhraním API modelu COM, jako jsou rozhraní API služby Office Automation, k dynamickým rozhraním API, jako jsou knihovny Ironpythonu, a k HTML model DOM (Document Object Model) (DOM).</span><span class="sxs-lookup"><span data-stu-id="15b99-157">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>

<span data-ttu-id="15b99-158">Typ `dynamic` se ve většině případů chová jako typ `object`.</span><span class="sxs-lookup"><span data-stu-id="15b99-158">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="15b99-159">Konkrétně libovolný výraz, který není null, lze převést na typ `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="15b99-159">In particular, any non-null expression can be converted to the `dynamic` type.</span></span> <span data-ttu-id="15b99-160">Typ `dynamic` se liší od `object` v tom, že operace obsahující výrazy typu `dynamic` nejsou vyřešeny nebo typu kontrolovaném kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="15b99-160">The `dynamic` type differs from `object` in that operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="15b99-161">Kompilátor balí informace o operaci a tyto informace jsou později použity k vyhodnocení operace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="15b99-161">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="15b99-162">Jako součást procesu jsou proměnné typu `dynamic` kompilovány do proměnných typu `object`.</span><span class="sxs-lookup"><span data-stu-id="15b99-162">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="15b99-163">Proto typ `dynamic` existuje pouze v době kompilace, nikoli v době běhu.</span><span class="sxs-lookup"><span data-stu-id="15b99-163">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>

<span data-ttu-id="15b99-164">Následující příklad kontrastuje proměnnou typu `dynamic` na proměnnou typu `object`.</span><span class="sxs-lookup"><span data-stu-id="15b99-164">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="15b99-165">Chcete-li ověřit typ každé proměnné v době kompilace, umístěte ukazatel myši nad `dyn` nebo `obj` v příkazech `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="15b99-165">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="15b99-166">Zkopírujte následující kód do editoru, kde je k dispozici technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="15b99-166">Copy the following code into an editor where IntelliSense is available.</span></span> <span data-ttu-id="15b99-167">IntelliSense zobrazí **dynamickou** pro `dyn` a **objekt** pro `obj`.</span><span class="sxs-lookup"><span data-stu-id="15b99-167">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<span data-ttu-id="15b99-168">Příkazy <xref:System.Console.WriteLine%2A> zobrazují běhové typy `dyn` a `obj`.</span><span class="sxs-lookup"><span data-stu-id="15b99-168">The <xref:System.Console.WriteLine%2A> statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="15b99-169">V tomto okamžiku oba mají stejný typ Integer.</span><span class="sxs-lookup"><span data-stu-id="15b99-169">At that point, both have the same type, integer.</span></span> <span data-ttu-id="15b99-170">Vytvoří se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="15b99-170">The following output is produced:</span></span>

```console
System.Int32
System.Int32
```

<span data-ttu-id="15b99-171">Chcete-li zobrazit rozdíl mezi `dyn` a `obj` v době kompilace, přidejte následující dva řádky mezi deklaracemi a příkazy `WriteLine` v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="15b99-171">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 <span data-ttu-id="15b99-172">Chyba kompilátoru je hlášena při pokusu o přidání celého čísla a objektu ve výrazu `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="15b99-172">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="15b99-173">Pro `dyn + 3`však není hlášena žádná chyba.</span><span class="sxs-lookup"><span data-stu-id="15b99-173">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="15b99-174">Výraz obsahující `dyn` není kontrolován v době kompilace, protože typ `dyn` je `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="15b99-174">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>

<span data-ttu-id="15b99-175">Následující příklad používá `dynamic` v několika deklaracích.</span><span class="sxs-lookup"><span data-stu-id="15b99-175">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="15b99-176">Metoda `Main` také kontrastí kontrolu typu při kompilaci s kontrolou typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="15b99-176">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a><span data-ttu-id="15b99-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15b99-177">See also</span></span>

- [<span data-ttu-id="15b99-178">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="15b99-178">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="15b99-179">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15b99-179">C# Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="15b99-180">Události</span><span class="sxs-lookup"><span data-stu-id="15b99-180">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="15b99-181">Použití typu dynamic</span><span class="sxs-lookup"><span data-stu-id="15b99-181">Using Type dynamic</span></span>](../../programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="15b99-182">Doporučené postupy pro používání řetězců</span><span class="sxs-lookup"><span data-stu-id="15b99-182">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="15b99-183">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="15b99-183">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="15b99-184">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="15b99-184">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="15b99-185">Operátory testování typů a přetypování</span><span class="sxs-lookup"><span data-stu-id="15b99-185">Type-testing and cast operators</span></span>](../operators/type-testing-and-cast.md)
- [<span data-ttu-id="15b99-186">Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů as a is</span><span class="sxs-lookup"><span data-stu-id="15b99-186">How to safely cast using pattern matching and the as and is operators</span></span>](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [<span data-ttu-id="15b99-187">Návod: vytváření a používání dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="15b99-187">Walkthrough: creating and using dynamic objects</span></span>](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
