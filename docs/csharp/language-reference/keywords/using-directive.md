---
title: Direktiva using C# – referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: a2028ccce47de54b59323194a0ffab3a643d878c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712972"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="b633a-102">using – direktiva (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="b633a-102">using directive (C# Reference)</span></span>

<span data-ttu-id="b633a-103">Direktiva `using` má tři použití:</span><span class="sxs-lookup"><span data-stu-id="b633a-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="b633a-104">Aby bylo možné povolit použití typů v oboru názvů, takže nemusíte kvalifikovat použití typu v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="b633a-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="b633a-105">Aby bylo možné přistupovat ke statickým členům a vnořeným typům typu bez nutnosti kvalifikovat přístup s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="b633a-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="b633a-106">Další informace naleznete v [direktivě using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="b633a-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="b633a-107">Pro vytvoření aliasu pro obor názvů nebo typ.</span><span class="sxs-lookup"><span data-stu-id="b633a-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="b633a-108">Tato *direktiva se nazývá using alias*.</span><span class="sxs-lookup"><span data-stu-id="b633a-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="b633a-109">Klíčové slovo `using` slouží také k vytváření *příkazů using*, které umožňují zajistit správné zpracování objektů <xref:System.IDisposable>, jako jsou soubory a písma.</span><span class="sxs-lookup"><span data-stu-id="b633a-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="b633a-110">Další informace najdete v tématu [použití příkazu Using](using-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="b633a-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="b633a-111">Použití statického typu</span><span class="sxs-lookup"><span data-stu-id="b633a-111">Using static type</span></span>

<span data-ttu-id="b633a-112">Můžete přistupovat ke statickým členům typu bez nutnosti kvalifikovat přístup s názvem typu:</span><span class="sxs-lookup"><span data-stu-id="b633a-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b633a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b633a-113">Remarks</span></span>

<span data-ttu-id="b633a-114">Rozsah direktivy `using` je omezený na soubor, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b633a-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="b633a-115">Může se zobrazit direktiva `using`:</span><span class="sxs-lookup"><span data-stu-id="b633a-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="b633a-116">Na začátku souboru zdrojového kódu před libovolným oborem názvů nebo definicí typu.</span><span class="sxs-lookup"><span data-stu-id="b633a-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="b633a-117">V jakémkoli oboru názvů, ale před libovolným oborem názvů nebo typy deklarovanými v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b633a-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="b633a-118">V opačném případě se generuje chyba kompilátoru [CS1529](../../misc/cs1529.md) .</span><span class="sxs-lookup"><span data-stu-id="b633a-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="b633a-119">Vytvořte direktivu `using` alias, aby bylo snazší kvalifikovat identifikátor oboru názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="b633a-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="b633a-120">V jakékoli `using` direktivě musí být plně kvalifikovaný obor názvů nebo typ použit bez ohledu na direktivy `using`, které jsou před ním.</span><span class="sxs-lookup"><span data-stu-id="b633a-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="b633a-121">V deklaraci direktivy `using` nelze použít žádný alias `using`.</span><span class="sxs-lookup"><span data-stu-id="b633a-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="b633a-122">Například následující příkaz vygeneruje chybu kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="b633a-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="b633a-123">Vytvořte direktivu `using` pro použití typů v oboru názvů bez nutnosti zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b633a-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="b633a-124">Direktiva `using` neposkytuje přístup k žádným oborům názvů, které jsou vnořené v oboru názvů, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="b633a-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="b633a-125">Obory názvů přicházejí ve dvou kategoriích: definované uživatelem a systémem.</span><span class="sxs-lookup"><span data-stu-id="b633a-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="b633a-126">Uživatelsky definované obory názvů jsou obory názvů definované ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="b633a-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="b633a-127">Seznam oborů názvů definovaných systémem naleznete v tématu [.NET API Browser](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="b633a-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="b633a-128">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="b633a-128">Example 1</span></span>

<span data-ttu-id="b633a-129">Následující příklad ukazuje, jak definovat a použít alias `using` pro obor názvů:</span><span class="sxs-lookup"><span data-stu-id="b633a-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="b633a-130">Direktiva using alias nemůže mít otevřený obecný typ na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="b633a-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="b633a-131">Například nemůžete vytvořit alias alias pro `List<T>`, ale můžete ho vytvořit pro `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="b633a-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="b633a-132">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="b633a-132">Example 2</span></span>

<span data-ttu-id="b633a-133">Následující příklad ukazuje, jak definovat direktivu `using` a alias `using` pro třídu:</span><span class="sxs-lookup"><span data-stu-id="b633a-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="b633a-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b633a-134">C# language specification</span></span>

<span data-ttu-id="b633a-135">Další informace najdete v tématu [direktivy using](~/_csharplang/spec/namespaces.md#using-directives) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b633a-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b633a-136">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="b633a-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="b633a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b633a-137">See also</span></span>

- [<span data-ttu-id="b633a-138">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b633a-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b633a-139">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b633a-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b633a-140">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="b633a-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="b633a-141">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b633a-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b633a-142">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="b633a-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="b633a-143">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="b633a-143">using Statement</span></span>](using-statement.md)
