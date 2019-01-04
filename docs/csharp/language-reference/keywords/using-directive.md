---
title: Using – direktiva - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 3e8daf24929339e31cda81a726ec11fdcffc687a
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029499"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="70655-102">Using – direktiva (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="70655-102">using directive (C# Reference)</span></span>

<span data-ttu-id="70655-103">`using` – Direktiva má tři používá:</span><span class="sxs-lookup"><span data-stu-id="70655-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="70655-104">Chcete-li povolit použití typů v oboru názvů, takže není potřeba kvalifikovat použití typu v tomto oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="70655-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="70655-105">Aby bylo možné přistupovat ke statické členy a vnořené typy typu bez nutnosti kvalifikovat přístup k s názvem typu.</span><span class="sxs-lookup"><span data-stu-id="70655-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="70655-106">Další informace najdete v tématu [using static – direktiva](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="70655-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="70655-107">Chcete-li vytvořit alias pro obor názvů nebo typu.</span><span class="sxs-lookup"><span data-stu-id="70655-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="70655-108">Tento postup se nazývá *alias direktiva using*.</span><span class="sxs-lookup"><span data-stu-id="70655-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="70655-109">`using` – Klíčové slovo se také používá k vytvoření *příkazy using*, které pomáhají zajistit, aby <xref:System.IDisposable> objekty, jako jsou soubory a písma jsou správně zpracovány.</span><span class="sxs-lookup"><span data-stu-id="70655-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="70655-110">Zobrazit [příkaz using](using-statement.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="70655-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="70655-111">Pomocí statického typu</span><span class="sxs-lookup"><span data-stu-id="70655-111">Using static type</span></span>

<span data-ttu-id="70655-112">Statické členy typu přístupné bez nutnosti kvalifikovat přístup k s názvem typu:</span><span class="sxs-lookup"><span data-stu-id="70655-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="70655-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70655-113">Remarks</span></span>

<span data-ttu-id="70655-114">Rozsah `using` – direktiva je omezená na soubor, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="70655-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="70655-115">`using` – Direktiva se může objevit:</span><span class="sxs-lookup"><span data-stu-id="70655-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="70655-116">Na začátku souboru zdrojového kódu, než všechny obor názvů nebo typ definice.</span><span class="sxs-lookup"><span data-stu-id="70655-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="70655-117">V jakékoli obor názvů, ale před jakoukoli oboru názvů nebo typy deklarované v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="70655-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="70655-118">Jinak Chyba kompilátoru [CS1529](../../misc/cs1529.md) je generován.</span><span class="sxs-lookup"><span data-stu-id="70655-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="70655-119">Vytvoření `using` alias – direktiva zjednodušit zařadit do oboru názvů nebo typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="70655-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="70655-120">V žádném `using` direktiv, plně kvalifikovaný obor názvů nebo typ musí být použita bez ohledu na to `using` direktivy, které jej předcházejí.</span><span class="sxs-lookup"><span data-stu-id="70655-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="70655-121">Ne `using` alias lze použít v deklaraci `using` směrnice.</span><span class="sxs-lookup"><span data-stu-id="70655-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="70655-122">Následující příklad vygeneruje chybu kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="70655-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="70655-123">Vytvoření `using` směrnice použít typy v oboru názvů, aniž byste museli zadat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="70655-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="70655-124">A `using` – direktiva není poskytují přístup k žádné obory názvů, které jsou vnořené v oboru názvů, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="70655-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="70655-125">Obory názvů se dělí na dvou kategorií: uživatelem definované a definovaná systémem.</span><span class="sxs-lookup"><span data-stu-id="70655-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="70655-126">Uživatelem definované obory názvů jsou obory názvů definované ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="70655-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="70655-127">Seznam oborů názvů definovaných systémem najdete v tématu [.NET API Browseru](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="70655-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

<span data-ttu-id="70655-128">Odkazující metody v jiných sestaveních příklady najdete v tématu [vytvoření a použití sestavení pomocí příkazového řádku](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="70655-128">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="70655-129">Příklad 1</span><span class="sxs-lookup"><span data-stu-id="70655-129">Example 1</span></span>

<span data-ttu-id="70655-130">Následující příklad ukazuje, jak definovat a používat `using` alias pro obor názvů:</span><span class="sxs-lookup"><span data-stu-id="70655-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="70655-131">Using – direktiva alias nemůže mít otevřený obecný typ. na pravé straně.</span><span class="sxs-lookup"><span data-stu-id="70655-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="70655-132">Například nemůžete vytvořit alias using pro `List<T>`, ale můžete ho vytvořit `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="70655-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="70655-133">Příklad 2</span><span class="sxs-lookup"><span data-stu-id="70655-133">Example 2</span></span>

<span data-ttu-id="70655-134">Následující příklad ukazuje, jak definovat `using` směrnice a `using` alias pro třídu:</span><span class="sxs-lookup"><span data-stu-id="70655-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="70655-135">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70655-135">C# language specification</span></span>

<span data-ttu-id="70655-136">Další informace najdete v tématu [direktiv Using](~/_csharplang/spec/namespaces.md#using-directives) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="70655-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="70655-137">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="70655-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="70655-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70655-138">See also</span></span>

- [<span data-ttu-id="70655-139">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70655-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="70655-140">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="70655-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="70655-141">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="70655-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="70655-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70655-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="70655-143">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="70655-143">Namespace Keywords</span></span>](namespace-keywords.md)
- [<span data-ttu-id="70655-144">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="70655-144">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="70655-145">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="70655-145">using Statement</span></span>](using-statement.md)
