---
title: použití direktivy – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 4f7ddad8c3dc12391ef6bf345a73ebb384400b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093146"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="0822b-102">pomocí směrnice (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="0822b-102">using directive (C# Reference)</span></span>

<span data-ttu-id="0822b-103">Směrnice `using` má tři použití:</span><span class="sxs-lookup"><span data-stu-id="0822b-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="0822b-104">Chcete-li povolit použití typů v oboru názvů, abyste nemuseli kvalifikovat použití typu v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="0822b-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="0822b-105">Chcete-li povolit přístup ke statickým členům a vnořeným typům, aniž byste museli kvalifikovat přístup s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="0822b-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="0822b-106">Další informace naleznete v [tématu using static directive](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="0822b-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="0822b-107">Vytvoření aliasu pro obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="0822b-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="0822b-108">To se nazývá *using alias směrnice*.</span><span class="sxs-lookup"><span data-stu-id="0822b-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="0822b-109">Klíčové `using` slovo se také používá k vytvoření <xref:System.IDisposable> pomocí *příkazů*, které pomáhají zajistit, že objekty, jako jsou soubory a písma jsou zpracovány správně.</span><span class="sxs-lookup"><span data-stu-id="0822b-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="0822b-110">Další informace najdete [v tématu použití příkazu.](using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0822b-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="0822b-111">Použití statického typu</span><span class="sxs-lookup"><span data-stu-id="0822b-111">Using static type</span></span>

<span data-ttu-id="0822b-112">Můžete přistupovat ke statickým členům typu, aniž byste museli kvalifikovat přístup s názvem typu:</span><span class="sxs-lookup"><span data-stu-id="0822b-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="0822b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0822b-113">Remarks</span></span>

<span data-ttu-id="0822b-114">Oblast působnosti `using` směrnice je omezena na soubor, ve kterém se objevuje.</span><span class="sxs-lookup"><span data-stu-id="0822b-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="0822b-115">Směrnice `using` se může objevit:</span><span class="sxs-lookup"><span data-stu-id="0822b-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="0822b-116">Na začátku souboru zdrojového kódu před všemi definicemi oboru názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="0822b-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="0822b-117">V libovolném oboru názvů, ale před libovolným oborem názvů nebo typy deklarovanými v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0822b-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="0822b-118">V opačném případě je generována chyba kompilátoru [CS1529.](../../misc/cs1529.md)</span><span class="sxs-lookup"><span data-stu-id="0822b-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="0822b-119">Vytvořte `using` direktivu aliasu, která usnadní kvalifikaci identifikátoru do oboru názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="0822b-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="0822b-120">V `using` každé direktivě musí být použit plně kvalifikovaný `using` obor názvů nebo typ bez ohledu na direktivy, které jsou před ním.</span><span class="sxs-lookup"><span data-stu-id="0822b-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="0822b-121">V `using` deklaraci `using` směrnice nelze použít žádný alias.</span><span class="sxs-lookup"><span data-stu-id="0822b-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="0822b-122">Například následující generuje chybu kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="0822b-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="0822b-123">Vytvořte `using` direktivu pro použití typů v oboru názvů bez nutnosti zadávat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0822b-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="0822b-124">Direktiva `using` neposkytuje přístup k žádným oborům názvů, které jsou vnořeny do zadaného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0822b-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="0822b-125">Obory názvů jsou dodávány ve dvou kategoriích: uživatelem definované a definované systémem.</span><span class="sxs-lookup"><span data-stu-id="0822b-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="0822b-126">Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="0822b-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="0822b-127">Seznam systémově definovaných oborů názvů naleznete v [tématu .NET API Browser](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="0822b-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="0822b-128">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="0822b-128">Example 1</span></span>

<span data-ttu-id="0822b-129">Následující příklad ukazuje, jak definovat `using` a používat alias pro obor názvů:</span><span class="sxs-lookup"><span data-stu-id="0822b-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="0822b-130">Direktiva using alias nemůže mít otevřený obecný typ na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="0822b-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="0822b-131">Nemůžete například vytvořit using alias `List<T>`pro , ale můžete `List<int>`jej vytvořit pro .</span><span class="sxs-lookup"><span data-stu-id="0822b-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="0822b-132">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="0822b-132">Example 2</span></span>

<span data-ttu-id="0822b-133">Následující příklad ukazuje, jak `using` definovat `using` direktivu a alias pro třídu:</span><span class="sxs-lookup"><span data-stu-id="0822b-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="0822b-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0822b-134">C# language specification</span></span>

<span data-ttu-id="0822b-135">Další informace naleznete v [tématu Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="0822b-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0822b-136">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="0822b-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="0822b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="0822b-137">See also</span></span>

- [<span data-ttu-id="0822b-138">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0822b-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0822b-139">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0822b-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0822b-140">Použití oborů názvů</span><span class="sxs-lookup"><span data-stu-id="0822b-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="0822b-141">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0822b-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0822b-142">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="0822b-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="0822b-143">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="0822b-143">using Statement</span></span>](using-statement.md)
