---
title: C#Program strukturu – připravuje C# jazyka
description: Přečtěte si základní stavební bloky C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: de10cd000b4028a66ce6dd6f21e39c013e38ecd2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131024"
---
# <a name="program-structure"></a><span data-ttu-id="0bb90-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="0bb90-103">Program Structure</span></span>

<span data-ttu-id="0bb90-104">Klíčové koncepty organizace v jazyce C# jsou ***programy***, ***obory názvů***, ***typy***, ***členy***, a ***sestavení***.</span><span class="sxs-lookup"><span data-stu-id="0bb90-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="0bb90-105">Programy jazyka C# se skládají z jednoho nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="0bb90-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="0bb90-106">Programy deklarovat typy, které obsahují členy a mohou být uspořádány do oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="0bb90-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="0bb90-107">Třídy a rozhraní jsou příklady typů.</span><span class="sxs-lookup"><span data-stu-id="0bb90-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="0bb90-108">Pole, metody, vlastnosti a události jsou příklady členů.</span><span class="sxs-lookup"><span data-stu-id="0bb90-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="0bb90-109">Když jsou kompilovány programy jazyka C#, jsou fyzicky zabaleny do sestavení.</span><span class="sxs-lookup"><span data-stu-id="0bb90-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="0bb90-110">Sestavení obvykle mít příponu souboru `.exe` nebo `.dll`, v závislosti na tom, jestli je implementovat ***aplikací*** nebo ***knihovny***v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0bb90-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="0bb90-111">Příklad deklaruje třídu s názvem `Stack` v obor názvů s názvem `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="0bb90-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="0bb90-112">Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="0bb90-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="0bb90-113">Třída obsahuje několik členů: pole s názvem `top`, dvě metody s názvem `Push` a `Pop`a vnořené třídy s názvem `Entry`.</span><span class="sxs-lookup"><span data-stu-id="0bb90-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="0bb90-114">`Entry` Další třídy obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="0bb90-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="0bb90-115">Za předpokladu, že zdrojový kód v příkladu je uložen v souboru `acme.cs`, příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="0bb90-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```
csc /t:library acme.cs
```

<span data-ttu-id="0bb90-116">zkompiluje v příkladu jako knihovna (bez kódu `Main` vstupního bodu) a vytváří sestavení s názvem `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="0bb90-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0bb90-117">Příklady nad použití `csc` jako příkazového řádku C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0bb90-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="0bb90-118">Tento kompilátor je spustitelný soubor Windows.</span><span class="sxs-lookup"><span data-stu-id="0bb90-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="0bb90-119">Chcete-li použít C# na jiných platformách, by měly použít nástroje pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bb90-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="0bb90-120">Používá ekosystému .NET Core `dotnet` CLI ke správě sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0bb90-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="0bb90-121">To zahrnuje správu závislostí a vyvolání C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0bb90-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="0bb90-122">Zobrazit [v tomto kurzu](../../core/tutorials/using-with-xplat-cli.md) úplný popis těchto nástrojů na platformách podporovaných aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bb90-122">See [this tutorial](../../core/tutorials/using-with-xplat-cli.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="0bb90-123">Sestavení obsahují spustitelného kódu v podobě pokynů Intermediate Language (IL) a symbolické informace ve formě metadat.</span><span class="sxs-lookup"><span data-stu-id="0bb90-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="0bb90-124">Předtím, než se spustí, kód IL v sestavení automaticky převést do kódu specifického pro procesor kompilátorem za běhu (JIT) modulu .NET Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="0bb90-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="0bb90-125">Protože sestavení je jednotka funkce obsahující kód a metadata popisující samy sebe, není nutné pro `#include` direktivy a soubory hlaviček v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="0bb90-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="0bb90-126">Veřejné typy a členy, které jsou obsažené v konkrétní sestavení jsou k dispozici v programu v jazyce C# jednoduše tak, že odkazující na toto sestavení při kompilaci programu.</span><span class="sxs-lookup"><span data-stu-id="0bb90-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="0bb90-127">Například používá tento program `Acme.Collections.Stack` třídy z `acme.dll` sestavení:</span><span class="sxs-lookup"><span data-stu-id="0bb90-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="0bb90-128">Pokud program je uložený v souboru `example.cs`, když `example.cs` je zkompilován, acme.dll sestavení lze odkazovat pomocí /r – možnost kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="0bb90-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```
csc /r:acme.dll example.cs
```

<span data-ttu-id="0bb90-129">Tím se vytvoří sestavení spustitelného souboru s názvem `example.exe`, který při spuštění vytvoří výstup:</span><span class="sxs-lookup"><span data-stu-id="0bb90-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```
100
10
1
```

<span data-ttu-id="0bb90-130">C# umožňuje text zdrojového programu, který bude uložen do několika zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="0bb90-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="0bb90-131">Když je zkompilován více soubory programu v C#, jsou společně zpracovány všechny zdrojové soubory a zdrojové soubory můžete odkazovat na volně mezi sebou, koncepčně, je, jako kdyby byly všechny zdrojové soubory zřetězeny do jednoho velkého souboru před zpracováním.</span><span class="sxs-lookup"><span data-stu-id="0bb90-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="0bb90-132">Dopředné deklarace jsou potřeba nikdy v jazyce C#, protože s několika málo výjimkami je deklarace pořadí je neplatné.</span><span class="sxs-lookup"><span data-stu-id="0bb90-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="0bb90-133">C# neomezuje zdrojový soubor k deklarování pouze jeden veřejný typ taky je potřeba, aby název zdrojového souboru tak, aby odpovídaly typu deklarovaného ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="0bb90-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0bb90-134">[Předchozí](index.md)
>[další](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="0bb90-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>