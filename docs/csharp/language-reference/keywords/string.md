---
title: "string (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8899eb75b1b7c556a1e92f173a4d0ca4135014c8
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="string-c-reference"></a><span data-ttu-id="3d7ba-102">string (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3d7ba-102">string (C# Reference)</span></span>
<span data-ttu-id="3d7ba-103">`string` Typ reprezentuje posloupnosti nula nebo více znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-103">The `string` type represents a sequence of zero or more Unicode characters.</span></span> <span data-ttu-id="3d7ba-104">`string` je alias <xref:System.String> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-104">`string` is an alias for <xref:System.String> in .NET.</span></span>  
  
 <span data-ttu-id="3d7ba-105">I když `string` typem je odkaz, operátory rovnosti (`==` a `!=`) jsou definovány pro porovnání hodnot `string` objekty, není odkazuje.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-105">Although `string` is a reference type, the equality operators (`==` and `!=`) are defined to compare the values of `string` objects, not references.</span></span> <span data-ttu-id="3d7ba-106">Díky tomu bude testování rovnosti řetězec intuitivnější.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-106">This makes testing for string equality more intuitive.</span></span> <span data-ttu-id="3d7ba-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3d7ba-107">For example:</span></span>  
  
```csharp  
string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 <span data-ttu-id="3d7ba-108">Zobrazí "hodnotu True" a potom "False" vzhledem k tomu, že obsah řetězce jsou ekvivalentní, ale `a` a `b` neměly by konce odkazovat na stejnou instanci řetězec.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-108">This displays "True" and then "False" because the content of the strings are equivalent, but `a` and `b` do not refer to the same string instance.</span></span>  
  
 <span data-ttu-id="3d7ba-109">+ – Operátor zřetězí řetězec:</span><span class="sxs-lookup"><span data-stu-id="3d7ba-109">The + operator concatenates strings:</span></span>  
  
```csharp  
string a = "good " + "morning";  
```  
  
 <span data-ttu-id="3d7ba-110">Tím se vytvoří objekt řetězec, který obsahuje "Dobré ráno".</span><span class="sxs-lookup"><span data-stu-id="3d7ba-110">This creates a string object that contains "good morning".</span></span>  
  
 <span data-ttu-id="3d7ba-111">Řetězce jsou *neměnné*– obsah objektu řetězce nelze změnit po vytvoření objektu, i když je syntaxe se objevit, jako kdyby to provedete.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-111">Strings are *immutable*--the contents of a string object cannot be changed after the object is created, although the syntax makes it appear as if you can do this.</span></span> <span data-ttu-id="3d7ba-112">Když píšete tento kód, kompilátor ve skutečnosti vytvoří nový objekt řetězec k uložení nové pořadí znaků a tento nový objekt je přiřazen k b.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-112">For example, when you write this code, the compiler actually creates a new string object to hold the new sequence of characters, and that new object is assigned to b.</span></span> <span data-ttu-id="3d7ba-113">Řetězec "h" je pak vhodné pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-113">The string "h" is then eligible for garbage collection.</span></span>  
  
```csharp
string b = "h";  
b += "ello";  
```  
  
 <span data-ttu-id="3d7ba-114">[] – Operátor lze použít pro přístup jen pro čtení k jednotlivé znaky `string`:</span><span class="sxs-lookup"><span data-stu-id="3d7ba-114">The [] operator can be used for readonly access to individual characters of a `string`:</span></span>  
  
```csharp  
string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 <span data-ttu-id="3d7ba-115">Textové literály jsou typu `string` a může být napsán ve dvou formách, v uvozovkách a @-quoted.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-115">String literals are of type `string` and can be written in two forms, quoted and @-quoted.</span></span> <span data-ttu-id="3d7ba-116">V uvozovkách řetězec, který literály jsou uzavřené v uvozovkách ("):</span><span class="sxs-lookup"><span data-stu-id="3d7ba-116">Quoted string literals are enclosed in double quotation marks ("):</span></span>  
  
```csharp  
"good morning"  // a string literal  
```  
  
 <span data-ttu-id="3d7ba-117">Textové literály může obsahovat libovolný znak literálu.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-117">String literals can contain any character literal.</span></span> <span data-ttu-id="3d7ba-118">Řídicí sekvence jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-118">Escape sequences are included.</span></span> <span data-ttu-id="3d7ba-119">Následující příklad používá řídicí sekvence `\\` pro zpětné lomítko, `\u0066` pro písmenem f, a `\n` pro nový řádek.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-119">The following example uses escape sequence `\\` for backslash, `\u0066` for the letter f, and `\n` for newline.</span></span>  
  
```  
string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  <span data-ttu-id="3d7ba-120">Řídicí kód `\udddd` (kde `dddd` čtyři číslice) představuje znak Unicode U +`dddd`.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-120">The escape code `\udddd` (where `dddd` is a four-digit number) represents the Unicode character U+`dddd`.</span></span> <span data-ttu-id="3d7ba-121">Kódy řídicí Unicode číslice osm jsou také rozpoznána: `\Udddddddd`.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-121">Eight-digit Unicode escape codes are also recognized: `\Udddddddd`.</span></span>  
  
 <span data-ttu-id="3d7ba-122">Začínat typu verbatim textové literály `@` a jsou také uzavřena v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="3d7ba-122">Verbatim string literals start with `@` and are also enclosed in double quotation marks.</span></span> <span data-ttu-id="3d7ba-123">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3d7ba-123">For example:</span></span>  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 <span data-ttu-id="3d7ba-124">Výhodou typu verbatim řetězce je, že jsou řídicí sekvence *není* zpracovat, což usnadňuje zápisu, například plně kvalifikovaný název souboru:</span><span class="sxs-lookup"><span data-stu-id="3d7ba-124">The advantage of verbatim strings is that escape sequences are *not* processed, which makes it easy to write, for example, a fully qualified file name:</span></span>  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 <span data-ttu-id="3d7ba-125">Zahrnout uvozovky v @-quoted řetězce, dvakrát ho:</span><span class="sxs-lookup"><span data-stu-id="3d7ba-125">To include a double quotation mark in an @-quoted string, double it:</span></span>  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 <span data-ttu-id="3d7ba-126">Pro další použití `@` speciální znak, najdete v části [@ – typu verbatim identifikátor](../tokens/verbatim.md).</span><span class="sxs-lookup"><span data-stu-id="3d7ba-126">For other uses of the `@` special character, see [@ -- verbatim identifier](../tokens/verbatim.md).</span></span>  
  
 <span data-ttu-id="3d7ba-127">Další informace o řetězcích v jazyce C# najdete v tématu [řetězce](../../../csharp/programming-guide/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d7ba-127">For more information about strings in C#, see [Strings](../../../csharp/programming-guide/strings/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d7ba-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d7ba-128">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3d7ba-129">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d7ba-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3d7ba-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d7ba-130">See Also</span></span>  
 [<span data-ttu-id="3d7ba-131">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d7ba-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3d7ba-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3d7ba-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d7ba-133">Doporučené postupy pro používání řetězců</span><span class="sxs-lookup"><span data-stu-id="3d7ba-133">Best Practices for Using Strings</span></span>](../../../standard/base-types/best-practices-strings.md)  
 [<span data-ttu-id="3d7ba-134">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d7ba-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3d7ba-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3d7ba-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3d7ba-136">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="3d7ba-136">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="3d7ba-137">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="3d7ba-137">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="3d7ba-138">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="3d7ba-138">Basic String Operations</span></span>](../../../standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="3d7ba-139">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="3d7ba-139">Creating New Strings</span></span>](../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="3d7ba-140">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="3d7ba-140">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
