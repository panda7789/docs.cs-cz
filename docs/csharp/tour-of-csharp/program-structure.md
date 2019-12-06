---
title: C#Struktura programu – prohlídka C# jazyka
description: Seznamte se se základními stavebními bloky C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5e095e71549ed3eec6c73e6a134fdb5a64fb63c0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884381"
---
# <a name="program-structure"></a><span data-ttu-id="30c61-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="30c61-103">Program Structure</span></span>

<span data-ttu-id="30c61-104">Klíčovou organizační koncepcí v C# nástroji jsou ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.</span><span class="sxs-lookup"><span data-stu-id="30c61-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="30c61-105">C#programy se skládají z jednoho nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="30c61-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="30c61-106">Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="30c61-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="30c61-107">Příklady typů jsou třídy a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="30c61-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="30c61-108">Příklady členů jsou pole, metody, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="30c61-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="30c61-109">Když C# jsou programy kompilovány, jsou fyzicky zabaleny do sestavení.</span><span class="sxs-lookup"><span data-stu-id="30c61-109">When C# programs are compiled, they are physically packaged into assemblies.</span></span> <span data-ttu-id="30c61-110">Sestavení mají obvykle příponu souboru `.exe` nebo `.dll`, v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="30c61-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="30c61-111">Příklad deklaruje třídu s názvem `Stack` v oboru názvů s názvem `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="30c61-111">The example declares a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="30c61-112">Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="30c61-112">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="30c61-113">Třída obsahuje několik členů: pole s názvem `top`, dvě metody pojmenované `Push` a `Pop`a vnořená třída s názvem `Entry`.</span><span class="sxs-lookup"><span data-stu-id="30c61-113">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="30c61-114">Třída `Entry` dále obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="30c61-114">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="30c61-115">Za předpokladu, že zdrojový kód příkladu je uložen v souboru `acme.cs`, příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="30c61-115">Assuming that the source code of the example is stored in the file `acme.cs`, the command line</span></span>

```console
csc /t:library acme.cs
```

<span data-ttu-id="30c61-116">zkompiluje příklad jako knihovnu (kód bez `Main` vstupní bod) a vytvoří sestavení s názvem `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="30c61-116">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30c61-117">Výše uvedené příklady používají `csc` jako kompilátor příkazového C# řádku.</span><span class="sxs-lookup"><span data-stu-id="30c61-117">The examples above use `csc` as the command line C# compiler.</span></span> <span data-ttu-id="30c61-118">Tento kompilátor je spustitelný soubor systému Windows.</span><span class="sxs-lookup"><span data-stu-id="30c61-118">This compiler is a Windows executable.</span></span> <span data-ttu-id="30c61-119">Chcete- C# li používat na jiných platformách, měli byste použít nástroje pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="30c61-119">To use C# across other platforms, you should use the tools for .NET Core.</span></span> <span data-ttu-id="30c61-120">Ekosystém .NET Core používá `dotnet` CLI ke správě sestavení příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="30c61-120">The .NET Core ecosystem uses the `dotnet` CLI to manage command line builds.</span></span> <span data-ttu-id="30c61-121">To zahrnuje správu závislostí a vyvolávání C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="30c61-121">This includes managing dependencies, and invoking the C# compiler.</span></span> <span data-ttu-id="30c61-122">Úplný popis těchto nástrojů na platformách, které podporuje .NET Core, najdete v [tomto kurzu](../../core/tutorials/cli-create-console-app.md) .</span><span class="sxs-lookup"><span data-stu-id="30c61-122">See [this tutorial](../../core/tutorials/cli-create-console-app.md) for a full description of those tools on the platforms supported by .NET Core.</span></span>

<span data-ttu-id="30c61-123">Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat.</span><span class="sxs-lookup"><span data-stu-id="30c61-123">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="30c61-124">Před provedením je kód IL v sestavení automaticky převeden na kód specifický pro procesor pomocí kompilátoru JIT (just-in-time) modulu CLR (Common Language Runtime) .NET.</span><span class="sxs-lookup"><span data-stu-id="30c61-124">Before it is executed, the IL code in an assembly is automatically converted to processor-specific code by the Just-In-Time (JIT) compiler of .NET Common Language Runtime.</span></span>

<span data-ttu-id="30c61-125">Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktiv a hlavičkových souborů v C#.</span><span class="sxs-lookup"><span data-stu-id="30c61-125">Because an assembly is a self-describing unit of functionality containing both code and metadata, there is no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="30c61-126">Veřejné typy a členy, které jsou obsaženy v konkrétním sestavení, jsou v C# programu k dispozici jednoduše odkazem na toto sestavení při kompilování programu.</span><span class="sxs-lookup"><span data-stu-id="30c61-126">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="30c61-127">Například tento program používá třídu `Acme.Collections.Stack` ze sestavení `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="30c61-127">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="30c61-128">Pokud je program uložen v souboru `example.cs`, když je `example.cs` kompilováno, může být sestavení Acme. dll odkazováno pomocí možnosti kompilátoru '/r:</span><span class="sxs-lookup"><span data-stu-id="30c61-128">If the program is stored in the file `example.cs`, when `example.cs` is compiled, the acme.dll assembly can be referenced using the compiler’s /r option:</span></span>

```console
csc /r:acme.dll example.cs
```

<span data-ttu-id="30c61-129">Tím se vytvoří spustitelné sestavení s názvem `example.exe`, které při spuštění vytvoří výstup:</span><span class="sxs-lookup"><span data-stu-id="30c61-129">This creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="30c61-130">C#umožňuje, aby byl zdrojový text programu uložen v několika zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="30c61-130">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="30c61-131">Když je zkompilován program pro C# více souborů, všechny zdrojové soubory jsou zpracovávány společně a zdrojové soubory mohou volně odkazovat, a to koncepční, protože všechny zdrojové soubory byly před zpracováním sloučeny do jednoho velkého souboru.</span><span class="sxs-lookup"><span data-stu-id="30c61-131">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="30c61-132">Dopředné deklarace nejsou nikdy C# potřeba v důsledku nedostatečných výjimek, pořadí deklarací je nedůležité.</span><span class="sxs-lookup"><span data-stu-id="30c61-132">Forward declarations are never needed in C# because, with very few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="30c61-133">C#neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="30c61-133">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="30c61-134">[Předchozí](index.md)
>[Další](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="30c61-134">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
