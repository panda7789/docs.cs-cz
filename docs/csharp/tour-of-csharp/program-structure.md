---
title: "C# Program strukturu – přehled používání jazyka C#"
description: "Další základní stavební bloky programu v C#"
keywords: "Rozhraní .NET .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="program-structure"></a><span data-ttu-id="80642-104">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="80642-104">Program Structure</span></span>

<span data-ttu-id="80642-105">Klíčové koncepty organizace v jazyce C# jsou ***programy***, ***obory názvů***, ***typy***, ***členy***, a ***sestavení***.</span><span class="sxs-lookup"><span data-stu-id="80642-105">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="80642-106">Programy C# obsahovat jeden nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="80642-106">C# programs consist of one or more source files.</span></span> <span data-ttu-id="80642-107">Programy deklarovat typy, které obsahují členy a mohou být uspořádány do oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="80642-107">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="80642-108">Třídy a rozhraní jsou příklady typů.</span><span class="sxs-lookup"><span data-stu-id="80642-108">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="80642-109">Pole, metody, vlastnosti a události jsou příklady členů.</span><span class="sxs-lookup"><span data-stu-id="80642-109">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="80642-110">Když jsou kompilované programy C#, jsou fyzicky zabalené do sestavení.</span><span class="sxs-lookup"><span data-stu-id="80642-110">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="80642-111">Sestavení obvykle mají příponu souboru `.exe` nebo `.dll`, v závislosti na tom, jestli implementace ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="80642-111">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="80642-112">V příkladu deklaruje třídy s názvem `Stack` v oboru názvů názvem `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="80642-112">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="80642-113">Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="80642-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="80642-114">Třída obsahuje několik členů: pole s názvem `top`, dvě metody s názvem `Push` a `Pop`a vnořené třídy s názvem `Entry`.</span><span class="sxs-lookup"><span data-stu-id="80642-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="80642-115">`Entry` Další třída obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="80642-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="80642-116">Za předpokladu, že zdrojový kód v příkladu je uložené v souboru `acme.cs`, příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="80642-116">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="80642-117">zkompiluje v příkladu jako knihovny (code bez `Main` vstupního bodu) a vytvoří sestavení s názvem `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="80642-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80642-118">Příklady výše použití `csc` jako kompilátoru příkazového řádku jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="80642-118">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="80642-119">Tato kompilátoru je spustitelný soubor windows.</span><span class="sxs-lookup"><span data-stu-id="80642-119">This compiler is a windows executable.</span></span> <span data-ttu-id="80642-120">Pokud chcete používat C# na jiných platformách, by měl pomocí nástrojů pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80642-120">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="80642-121">Používá ekosystému .NET Core `dotnet` rozhraní příkazového řádku pro správu sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="80642-121">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="80642-122">To zahrnuje správu závislosti a volání do kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="80642-122">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="80642-123">V tématu [v tomto kurzu](../../core/tutorials/using-with-xplat-cli.md) úplný popis těchto nástrojů na platformách podporovaných aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="80642-123">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="80642-124">Sestavení obsahovat spustitelného kódu ve formě pokyny Intermediate Language (IL) a symbolické informace ve formě metadat.</span><span class="sxs-lookup"><span data-stu-id="80642-124">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="80642-125">Před provedením, kód IL v sestavení automaticky převeden na specifické pro procesor kód kompilátorem JIT (JIT) Common Language Runtime rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="80642-125">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="80642-126">Protože sestavení je popisující samy sebe jednotka funkce obsahující kód a metadata, není nutné pro `#include` direktivy a hlavičkových souborů v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="80642-126">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="80642-127">Veřejné typy a členy obsažené v určitém sestavení jsou k dispozici v programu v C# jednoduše tak, že odkazování na sestavení při kompilaci programu.</span><span class="sxs-lookup"><span data-stu-id="80642-127">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="80642-128">Například používá tento program `Acme.Collections.Stack` třídy z `acme.dll` sestavení:</span><span class="sxs-lookup"><span data-stu-id="80642-128">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="80642-129">Pokud je program uložen v souboru `example.cs`, když `example.cs` je kompilovat, sestavení acme.dll můžete odkazovat pomocí /r – možnost kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="80642-129">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="80642-130">Tím se vytvoří spustitelný soubor sestavení s názvem `example.exe`, které, když se spustí, vytvoří výstup:</span><span class="sxs-lookup"><span data-stu-id="80642-130">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="80642-131">C# umožňuje zdrojový text programu, který má být uložen v několika zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="80642-131">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="80642-132">Při kompilaci více soubory programu v C#, všechny zdrojové soubory jsou zpracovávány společně, a zdrojové soubory můžete volně odkazovat navzájem – koncepčně, je jako kdyby byly všechny zdrojové soubory zřetězen do jednoho velkého souboru před zpracováním.</span><span class="sxs-lookup"><span data-stu-id="80642-132">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="80642-133">Předat dál deklarace jsou nikdy potřeba v jazyce C#, protože s počtu výjimek je zanedbatelný deklarace pořadí.</span><span class="sxs-lookup"><span data-stu-id="80642-133">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="80642-134">C# neomezuje zdrojového souboru do deklarace pouze jeden typ veřejné ani nevyžaduje název zdrojového souboru tak, aby odpovídaly typu deklarovaného v souboru zdroje.</span><span class="sxs-lookup"><span data-stu-id="80642-134">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="80642-135">[Předchozí](index.md)
[další](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="80642-135">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
