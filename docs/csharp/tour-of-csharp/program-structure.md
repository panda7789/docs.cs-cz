---
title: Struktura programu v jazyce c# – prohlídka jazyka C#
description: Seznamte se se základními stavebními bloky programu v jazyce C#.
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c0a4dcaed7b53a7da7008d6000b3bec2ffe3ee7b
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141016"
---
# <a name="program-structure"></a><span data-ttu-id="c1ce4-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="c1ce4-103">Program Structure</span></span>

<span data-ttu-id="c1ce4-104">Klíčovou organizační koncepcí v jazyce C# jsou ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="c1ce4-105">Programy v jazyce C# se skládají z jednoho nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="c1ce4-106">Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="c1ce4-107">Příklady typů jsou třídy a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="c1ce4-108">Příklady členů jsou pole, metody, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="c1ce4-109">Když jsou programy C# kompilovány, jsou fyzicky zabaleny do sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="c1ce4-110">Sestavení mají `.exe` obvykle příponu souboru nebo `.dll`v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="c1ce4-111">Projekt knihovny s názvem *ACME* můžete vytvořit pomocí `dotnet new` příkazu:</span><span class="sxs-lookup"><span data-stu-id="c1ce4-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```dotnetcli
dotnet new classlib -o acme
```

<span data-ttu-id="c1ce4-112">V tomto projektu Deklarujte třídu s názvem `Stack` v oboru názvů s `Acme.Collections`názvem:</span><span class="sxs-lookup"><span data-stu-id="c1ce4-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="c1ce4-113">Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="c1ce4-114">Třída obsahuje několik členů: pole s `top`názvem, dvě metody pojmenované `Push` a `Pop`a vnořená třída s názvem. `Entry`</span><span class="sxs-lookup"><span data-stu-id="c1ce4-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="c1ce4-115">`Entry` Třída dále obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="c1ce4-116">Příkaz:</span><span class="sxs-lookup"><span data-stu-id="c1ce4-116">The command:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="c1ce4-117">zkompiluje příklad jako knihovnu (kód bez `Main` vstupního bodu) a vytvoří sestavení s názvem. `acme.dll`</span><span class="sxs-lookup"><span data-stu-id="c1ce4-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="c1ce4-118">Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="c1ce4-119">Předtím, než se spustí, kompilátor JIT (just-in-time) prostředí .NET Common Language Runtime převede kód IL v sestavení na kód specifický pro procesor.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="c1ce4-120">Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktivy a hlavičkové soubory v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="c1ce4-121">Veřejné typy a členy obsažené v konkrétním sestavení jsou zpřístupněny v programu v jazyce C# pouhým odkazováním na toto sestavení při kompilování programu.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="c1ce4-122">Například tento program používá `Acme.Collections.Stack` třídu ze `acme.dll` sestavení:</span><span class="sxs-lookup"><span data-stu-id="c1ce4-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="c1ce4-123">Soubor *csproj* pro projekt předchozí aplikace musí obsahovat referenční uzel pro kompilátor jazyka C#, který bude překládat odkazy na třídy v `acme.dll` sestavení:</span><span class="sxs-lookup"><span data-stu-id="c1ce4-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="c1ce4-124">Po tomto přidání `dotnet build` vytvoří spustitelné sestavení s názvem `example.exe`, které při spuštění vytvoří výstup:</span><span class="sxs-lookup"><span data-stu-id="c1ce4-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```dotnetcli
100
10
1
```

<span data-ttu-id="c1ce4-125">Jazyk C# umožňuje uložit zdrojový text programu do několika zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="c1ce4-126">Když je zkompilován program pro více souborů C#, všechny zdrojové soubory jsou zpracovávány společně a zdrojové soubory mohou volně odkazovat – koncepčně, je to tak, aby byly všechny zdrojové soubory zřetězeny do jednoho velkého souboru před zpracováním.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="c1ce4-127">Předávací deklarace nejsou v jazyce C# nikdy potřeba, protože s malým počtem výjimek je pořadí deklarací nedůležité.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="c1ce4-128">Jazyk C# neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="c1ce4-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c1ce4-129">[Předchozí](index.md)
>[Další](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="c1ce4-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
