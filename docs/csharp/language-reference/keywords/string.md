---
title: string (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
ms.openlocfilehash: 66b1729363878f69f868b8b8fd6e9e7011426f27
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153121"
---
# <a name="string-c-reference"></a><span data-ttu-id="35e5e-102">string (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="35e5e-102">string (C# Reference)</span></span>

<span data-ttu-id="35e5e-103">`string` Typ představuje posloupnost nula nebo více znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="35e5e-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="35e5e-104">`string` je alias pro <xref:System.String> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="35e5e-104">`string` is an alias for <xref:System.String> in .NET.</span></span>

<span data-ttu-id="35e5e-105">I když `string` je typem odkazu, operátory rovnosti (`==` a `!=`) jsou definovány pro porovnání hodnoty `string` objekty, ne odkazuje.</span><span class="sxs-lookup"><span data-stu-id="35e5e-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="35e5e-106">Tím je testování rovnosti řetězců intuitivnější.</span><span class="sxs-lookup"><span data-stu-id="35e5e-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="35e5e-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="35e5e-107">For example:</span></span>

```csharp
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine((object)a == (object)b);
```

<span data-ttu-id="35e5e-108">Zobrazí "hodnotu True" a potom "False" protože obsah řetězce jsou ekvivalentní, ale `a` a `b` neodkazují na stejné instanci řetězce.</span><span class="sxs-lookup"><span data-stu-id="35e5e-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>

<span data-ttu-id="35e5e-109">+ – Operátor zřetězí řetězce:</span><span class="sxs-lookup"><span data-stu-id="35e5e-109">The + operator concatenates strings:</span></span>

```csharp
string a = "good " + "morning";
```

<span data-ttu-id="35e5e-110">Tím se vytvoří objekt string obsahující "good morning".</span><span class="sxs-lookup"><span data-stu-id="35e5e-110">This creates a string object that contains "good morning".</span></span>

<span data-ttu-id="35e5e-111">Řetězce jsou *neměnné*– obsah řetězce objektu nelze změnit po vytvoření objektu, přestože je syntaxe zobrazí jako by tomu.</span><span class="sxs-lookup"><span data-stu-id="35e5e-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="35e5e-112">Při psaní tohoto kódu kompilátor ve skutečnosti vytváří nový objekt řetězce pro uchování nového pořadí znaků a tento nový objekt je přiřazen b.</span><span class="sxs-lookup"><span data-stu-id="35e5e-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="35e5e-113">Řetězec "h" je pak nárok uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="35e5e-113">The string "h" is then eligible for garbage collection.</span></span>

```csharp
string b = "h";
b += "ello";
```

<span data-ttu-id="35e5e-114">[] – Operátor slouží pro přístup jen pro čtení k jednotlivé znaky `string`:</span><span class="sxs-lookup"><span data-stu-id="35e5e-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

<span data-ttu-id="35e5e-115">Řetězcové literály jsou typu `string` a může být zapsaný ve dvou formách, v uvozovkách a @-quoted.</span><span class="sxs-lookup"><span data-stu-id="35e5e-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="35e5e-116">Citovaný řetězec, který literály jsou uzavřeny v dvojitých uvozovkách ("):</span><span class="sxs-lookup"><span data-stu-id="35e5e-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>

```csharp
"good morning"  // a string literal
```

<span data-ttu-id="35e5e-117">Řetězcové literály může obsahovat libovolný znak literálu.</span><span class="sxs-lookup"><span data-stu-id="35e5e-117">String literals can contain any character literal.</span></span> <span data-ttu-id="35e5e-118">Řídicí sekvence jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="35e5e-118">Escape sequences are included.</span></span> <span data-ttu-id="35e5e-119">Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` písmenem f, a `\n` pro nový řádek.</span><span class="sxs-lookup"><span data-stu-id="35e5e-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>

```csharp
string a = "\\\u0066\n";
Console.WriteLine(a);
```

> [!NOTE]
> <span data-ttu-id="35e5e-120">Řídicí kód `\udddd` (kde `dddd` je čtyřmístné číslo) představuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="35e5e-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="35e5e-121">Osm číslice sady Unicode řídícími kódy jsou také rozpoznána: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="35e5e-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>

<span data-ttu-id="35e5e-122">Literály doslovný řetězec začínat `@` a jsou také uzavřen do dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="35e5e-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="35e5e-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="35e5e-123">For example:</span></span>

```csharp
@"good morning"  // a string literal
```

<span data-ttu-id="35e5e-124">Výhodou doslovném řetězci je, že řídicí sekvence jsou *není* zpracování, což usnadňuje zapsat, například plně kvalifikovaný název:</span><span class="sxs-lookup"><span data-stu-id="35e5e-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

<span data-ttu-id="35e5e-125">Zahrnout dvojitých uvozovek na @-quoted řetězec, uveďte ji dvakrát:</span><span class="sxs-lookup"><span data-stu-id="35e5e-125">To include a double quotation mark in an @-quoted string, double it:</span></span>

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

<span data-ttu-id="35e5e-126">Pro další použití `@` speciální znak, naleznete v tématu [@ – Doslovný identifikátor](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="35e5e-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>

<span data-ttu-id="35e5e-127">Další informace o řetězcích v jazyce C# najdete v tématu [řetězce](../../programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="35e5e-127">For more information about strings in C#, see [Strings](../../programming-guide/strings/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="35e5e-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="35e5e-128">Example</span></span>

[!code-csharp[csrefKeywordsTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#17)]  

## <a name="c-language-specification"></a><span data-ttu-id="35e5e-129">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35e5e-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="35e5e-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35e5e-130">See also</span></span>

- [<span data-ttu-id="35e5e-131">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35e5e-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="35e5e-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="35e5e-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="35e5e-133">Doporučené postupy pro používání řetězců</span><span class="sxs-lookup"><span data-stu-id="35e5e-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)
- [<span data-ttu-id="35e5e-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="35e5e-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="35e5e-135">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="35e5e-135">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="35e5e-136">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="35e5e-136">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="35e5e-137">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="35e5e-137">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="35e5e-138">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="35e5e-138">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="35e5e-139">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="35e5e-139">Formatting Numeric Results Table</span></span>](formatting-numeric-results-table.md)
