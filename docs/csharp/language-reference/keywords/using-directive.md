---
description: Direktiva using-reference jazyka C#
title: Direktiva using-reference jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: f22a67348b19b8c97513ca685b2b10b34b1fd6fd
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141943"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="8c985-103">using – direktiva (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8c985-103">using directive (C# Reference)</span></span>

<span data-ttu-id="8c985-104">`using`Direktiva má tři použití:</span><span class="sxs-lookup"><span data-stu-id="8c985-104">The `using` directive has three uses:</span></span>

- <span data-ttu-id="8c985-105">Aby bylo možné povolit použití typů v oboru názvů, takže nemusíte kvalifikovat použití typu v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="8c985-105">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="8c985-106">Aby bylo možné přistupovat ke statickým členům a vnořeným typům typu bez nutnosti kvalifikovat přístup s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="8c985-106">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="8c985-107">Další informace naleznete v [direktivě using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="8c985-107">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="8c985-108">Pro vytvoření aliasu pro obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="8c985-108">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="8c985-109">Tato *direktiva se nazývá using alias*.</span><span class="sxs-lookup"><span data-stu-id="8c985-109">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="8c985-110">`using`Klíčové slovo slouží také k vytváření *příkazů using*, které vám pomůžou zajistit, aby <xref:System.IDisposable> objekty, jako jsou soubory a písma, byly zpracovávány správně.</span><span class="sxs-lookup"><span data-stu-id="8c985-110">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="8c985-111">Další informace najdete v tématu [použití příkazu Using](using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="8c985-111">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="8c985-112">Použití statického typu</span><span class="sxs-lookup"><span data-stu-id="8c985-112">Using static type</span></span>

<span data-ttu-id="8c985-113">Můžete přistupovat ke statickým členům typu bez nutnosti kvalifikovat přístup s názvem typu:</span><span class="sxs-lookup"><span data-stu-id="8c985-113">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="8c985-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c985-114">Remarks</span></span>

<span data-ttu-id="8c985-115">Rozsah `using` direktivy je omezen na soubor, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="8c985-115">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="8c985-116">Tato `using` direktiva se může zobrazit:</span><span class="sxs-lookup"><span data-stu-id="8c985-116">The `using` directive can appear:</span></span>

- <span data-ttu-id="8c985-117">Na začátku souboru zdrojového kódu před libovolným oborem názvů nebo definicí typu.</span><span class="sxs-lookup"><span data-stu-id="8c985-117">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="8c985-118">V jakémkoli oboru názvů, ale před libovolným oborem názvů nebo typy deklarovanými v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8c985-118">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="8c985-119">V opačném případě se generuje chyba kompilátoru [CS1529](../../misc/cs1529.md) .</span><span class="sxs-lookup"><span data-stu-id="8c985-119">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="8c985-120">Vytvořte `using` direktivu alias pro snadnější zařazení identifikátoru do oboru názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="8c985-120">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="8c985-121">V jakékoli `using` direktivě musí být plně kvalifikovaný obor názvů nebo typ použit bez ohledu na `using` direktivy, které jsou před ním.</span><span class="sxs-lookup"><span data-stu-id="8c985-121">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="8c985-122">`using`V deklaraci direktivy nelze použít žádný alias `using` .</span><span class="sxs-lookup"><span data-stu-id="8c985-122">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="8c985-123">Například následující příkaz vygeneruje chybu kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="8c985-123">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="8c985-124">Vytvořte `using` direktivu pro použití typů v oboru názvů bez nutnosti zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8c985-124">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="8c985-125">`using`Direktiva neposkytuje přístup k žádným oborům názvů, které jsou vnořené v oboru názvů, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="8c985-125">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="8c985-126">Obory názvů přicházejí ve dvou kategoriích: definované uživatelem a systémem.</span><span class="sxs-lookup"><span data-stu-id="8c985-126">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="8c985-127">Uživatelsky definované obory názvů jsou obory názvů definované ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="8c985-127">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="8c985-128">Seznam oborů názvů definovaných systémem naleznete v tématu [.NET API Browser](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c985-128">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="8c985-129">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="8c985-129">Example 1</span></span>

<span data-ttu-id="8c985-130">Následující příklad ukazuje, jak definovat a použít `using` alias pro obor názvů:</span><span class="sxs-lookup"><span data-stu-id="8c985-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="8c985-131">Direktiva using alias nemůže mít otevřený obecný typ na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="8c985-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="8c985-132">Například nemůžete vytvořit alias s aliasem pro `List<T>` , ale můžete ho vytvořit pro `List<int>` .</span><span class="sxs-lookup"><span data-stu-id="8c985-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="8c985-133">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="8c985-133">Example 2</span></span>

<span data-ttu-id="8c985-134">Následující příklad ukazuje, jak definovat `using` direktivu a `using` alias pro třídu:</span><span class="sxs-lookup"><span data-stu-id="8c985-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="8c985-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8c985-135">C# language specification</span></span>

<span data-ttu-id="8c985-136">Další informace naleznete v tématu [direktivy using](~/_csharplang/spec/namespaces.md#using-directives) v [jazyce C# Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="8c985-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8c985-137">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8c985-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c985-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c985-138">See also</span></span>

- [<span data-ttu-id="8c985-139">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8c985-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8c985-140">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8c985-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8c985-141">Používání oborů názvů</span><span class="sxs-lookup"><span data-stu-id="8c985-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="8c985-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8c985-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8c985-143">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="8c985-143">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="8c985-144">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="8c985-144">using Statement</span></span>](using-statement.md)
