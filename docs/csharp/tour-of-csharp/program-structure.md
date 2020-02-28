---
title: C#Struktura programu – prohlídka C# jazyka
description: Seznamte se se základními stavebními bloky C# programu
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 828146ba509daf9427e6dd1a4ebf3ad747ac7c39
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159114"
---
# <a name="program-structure"></a><span data-ttu-id="674e8-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="674e8-103">Program Structure</span></span>

<span data-ttu-id="674e8-104">Klíčovou organizační koncepcí v C# nástroji jsou ***programy***, ***obory názvů***, ***typy***, ***členy***a ***sestavení***.</span><span class="sxs-lookup"><span data-stu-id="674e8-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="674e8-105">C#programy se skládají z jednoho nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="674e8-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="674e8-106">Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="674e8-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="674e8-107">Příklady typů jsou třídy a rozhraní.</span><span class="sxs-lookup"><span data-stu-id="674e8-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="674e8-108">Příklady členů jsou pole, metody, vlastnosti a události.</span><span class="sxs-lookup"><span data-stu-id="674e8-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="674e8-109">Když C# jsou programy kompilovány, jsou fyzicky zabaleny do sestavení.</span><span class="sxs-lookup"><span data-stu-id="674e8-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="674e8-110">Sestavení mají obvykle příponu souboru `.exe` nebo `.dll`, v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="674e8-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="674e8-111">Projekt knihovny s názvem *ACME* můžete vytvořit pomocí příkazu `dotnet new`:</span><span class="sxs-lookup"><span data-stu-id="674e8-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="674e8-112">V tomto projektu Deklarujte třídu s názvem `Stack` v oboru názvů s názvem `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="674e8-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="674e8-113">Plně kvalifikovaný název této třídy je `Acme.Collections.Stack`.</span><span class="sxs-lookup"><span data-stu-id="674e8-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="674e8-114">Třída obsahuje několik členů: pole s názvem `top`, dvě metody pojmenované `Push` a `Pop`a vnořená třída s názvem `Entry`.</span><span class="sxs-lookup"><span data-stu-id="674e8-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="674e8-115">Třída `Entry` dále obsahuje tři členy: pole s názvem `next`, pole s názvem `data`a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="674e8-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="674e8-116">Příkaz:</span><span class="sxs-lookup"><span data-stu-id="674e8-116">The command:</span></span>

```console
dotnet build 
```

<span data-ttu-id="674e8-117">zkompiluje příklad jako knihovnu (kód bez `Main` vstupní bod) a vytvoří sestavení s názvem `acme.dll`.</span><span class="sxs-lookup"><span data-stu-id="674e8-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="674e8-118">Sestavení obsahují spustitelný kód ve formě instrukcí pro převodní jazyk (IL) a symbolické informace ve formě metadat.</span><span class="sxs-lookup"><span data-stu-id="674e8-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="674e8-119">Předtím, než se spustí, kompilátor JIT (just-in-time) prostředí .NET Common Language Runtime převede kód IL v sestavení na kód specifický pro procesor.</span><span class="sxs-lookup"><span data-stu-id="674e8-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="674e8-120">Vzhledem k tomu, že sestavení je samo-popisující jednotku funkcí obsahující kód i metadata, není nutné `#include` direktiv a hlavičkových souborů v C#.</span><span class="sxs-lookup"><span data-stu-id="674e8-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="674e8-121">Veřejné typy a členy, které jsou obsaženy v konkrétním sestavení, jsou v C# programu k dispozici jednoduše odkazem na toto sestavení při kompilování programu.</span><span class="sxs-lookup"><span data-stu-id="674e8-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="674e8-122">Například tento program používá třídu `Acme.Collections.Stack` ze sestavení `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="674e8-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="674e8-123">Soubor *csproj* pro projekt předchozí aplikace musí zahrnovat uzel odkazu pro C# kompilátor, aby vyřešil odkazy na třídy v sestavení `acme.dll`:</span><span class="sxs-lookup"><span data-stu-id="674e8-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="674e8-124">Po přidání `dotnet build` vytvoří spustitelné sestavení s názvem `example.exe`, které při spuštění vytvoří výstup:</span><span class="sxs-lookup"><span data-stu-id="674e8-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="674e8-125">C#umožňuje, aby byl zdrojový text programu uložen v několika zdrojových souborech.</span><span class="sxs-lookup"><span data-stu-id="674e8-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="674e8-126">Když je zkompilován program pro C# více souborů, všechny zdrojové soubory jsou zpracovávány společně a zdrojové soubory mohou volně odkazovat, a to koncepční, protože všechny zdrojové soubory byly před zpracováním sloučeny do jednoho velkého souboru.</span><span class="sxs-lookup"><span data-stu-id="674e8-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="674e8-127">Předávací deklarace nejsou nikdy potřeba v C# rámci, protože s malým počtem výjimek je pořadí deklarací nedůležité.</span><span class="sxs-lookup"><span data-stu-id="674e8-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="674e8-128">C#neomezuje zdrojový soubor na deklaraci pouze jednoho veřejného typu, ani nevyžaduje název zdrojového souboru, aby odpovídal typu deklarovanému ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="674e8-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="674e8-129">[Předchozí](index.md)
>[Další](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="674e8-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
