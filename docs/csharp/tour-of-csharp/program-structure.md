---
title: C# Struktura programu - Prohlídka jazyka C#
description: Naučte se základní stavební kameny programu C#
ms.date: 02/25/2020
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: c09c11a4dd957b29b2adb7aaa8d68a50f30620b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156828"
---
# <a name="program-structure"></a><span data-ttu-id="d091b-103">Struktura programu</span><span class="sxs-lookup"><span data-stu-id="d091b-103">Program Structure</span></span>

<span data-ttu-id="d091b-104">Klíčovými organizačními koncepty v c# jsou ***programy***, ***obory názvů***, ***typy***, ***členové***a ***sestavení***.</span><span class="sxs-lookup"><span data-stu-id="d091b-104">The key organizational concepts in C# are ***programs***, ***namespaces***, ***types***, ***members***, and ***assemblies***.</span></span> <span data-ttu-id="d091b-105">Programy jazyka C# se skládají z jednoho nebo více zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="d091b-105">C# programs consist of one or more source files.</span></span> <span data-ttu-id="d091b-106">Programy deklarují typy, které obsahují členy a mohou být uspořádány do oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="d091b-106">Programs declare types, which contain members and can be organized into namespaces.</span></span> <span data-ttu-id="d091b-107">Třídy a rozhraní jsou příklady typů.</span><span class="sxs-lookup"><span data-stu-id="d091b-107">Classes and interfaces are examples of types.</span></span> <span data-ttu-id="d091b-108">Pole, metody, vlastnosti a události jsou příklady členů.</span><span class="sxs-lookup"><span data-stu-id="d091b-108">Fields, methods, properties, and events are examples of members.</span></span> <span data-ttu-id="d091b-109">Při kompilaci c# programy jsou fyzicky zabaleny do sestavení.</span><span class="sxs-lookup"><span data-stu-id="d091b-109">When C# programs are compiled, they're physically packaged into assemblies.</span></span> <span data-ttu-id="d091b-110">Sestavení mají obvykle `.exe` příponu `.dll`souboru nebo v závislosti na tom, zda implementují ***aplikace*** nebo ***knihovny***.</span><span class="sxs-lookup"><span data-stu-id="d091b-110">Assemblies typically have the file extension `.exe` or `.dll`, depending on whether they implement ***applications*** or ***libraries***, respectively.</span></span>

<span data-ttu-id="d091b-111">Pomocí příkazu můžete vytvořit projekt knihovny `dotnet new` s názvem *acme:*</span><span class="sxs-lookup"><span data-stu-id="d091b-111">You can create a library project named *acme* using the `dotnet new` command:</span></span>

```console
dotnet new classlib -o acme
```

<span data-ttu-id="d091b-112">V tomto projektu deklarujte třídu pojmenovanou `Stack` v oboru názvů s názvem `Acme.Collections`:</span><span class="sxs-lookup"><span data-stu-id="d091b-112">In that project, declare a class named `Stack` in a namespace called `Acme.Collections`:</span></span>

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

<span data-ttu-id="d091b-113">Plně kvalifikovaný název této `Acme.Collections.Stack`třídy je .</span><span class="sxs-lookup"><span data-stu-id="d091b-113">The fully qualified name of this class is `Acme.Collections.Stack`.</span></span> <span data-ttu-id="d091b-114">Třída obsahuje několik členů: `top`pole s `Push` názvem `Pop`, dvě metody `Entry`s názvem a , a vnořenou třídu s názvem .</span><span class="sxs-lookup"><span data-stu-id="d091b-114">The class contains several members: a field named `top`, two methods named `Push` and `Pop`, and a nested class named `Entry`.</span></span> <span data-ttu-id="d091b-115">Třída `Entry` dále obsahuje tři členy: `next`pole s `data`názvem , pole s názvem a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d091b-115">The `Entry` class further contains three members: a field named `next`, a field named `data`, and a constructor.</span></span> <span data-ttu-id="d091b-116">Příkaz:</span><span class="sxs-lookup"><span data-stu-id="d091b-116">The command:</span></span>

```console
dotnet build
```

<span data-ttu-id="d091b-117">zkompiluje příklad jako knihovnu (kód bez `Main` vstupního `acme.dll`bodu) a vytvoří sestavení s názvem .</span><span class="sxs-lookup"><span data-stu-id="d091b-117">compiles the example as a library (code without a `Main` entry point) and produces an assembly named `acme.dll`.</span></span>

<span data-ttu-id="d091b-118">Sestavení obsahují spustitelný kód ve formě pokynů zprostředkujícího jazyka (IL) a symbolické informace ve formě metadat.</span><span class="sxs-lookup"><span data-stu-id="d091b-118">Assemblies contain executable code in the form of Intermediate Language (IL) instructions, and symbolic information in the form of metadata.</span></span> <span data-ttu-id="d091b-119">Před jeho spuštěním převede kompilátor Just-In-Time (JIT) rozhraní .NET Common Language Runtime kód IL v sestavení na kód specifický pro procesor.</span><span class="sxs-lookup"><span data-stu-id="d091b-119">Before it's executed, the Just-In-Time (JIT) compiler of .NET Common Language Runtime converts the IL code in an assembly to processor-specific code.</span></span>

<span data-ttu-id="d091b-120">Vzhledem k tomu, že sestavení je vlastní popisující jednotka funkcí obsahující kód i `#include` metadata, není potřeba direktiv y a souborů hlaviček v systému C#.</span><span class="sxs-lookup"><span data-stu-id="d091b-120">Because an assembly is a self-describing unit of functionality containing both code and metadata, there's no need for `#include` directives and header files in C#.</span></span> <span data-ttu-id="d091b-121">Veřejné typy a členy obsažené v určitém sestavení jsou k dispozici v programu Jazyka C# jednoduše odkazováním na toto sestavení při kompilaci programu.</span><span class="sxs-lookup"><span data-stu-id="d091b-121">The public types and members contained in a particular assembly are made available in a C# program simply by referencing that assembly when compiling the program.</span></span> <span data-ttu-id="d091b-122">Tento program například `Acme.Collections.Stack` používá třídu ze `acme.dll` sestavení:</span><span class="sxs-lookup"><span data-stu-id="d091b-122">For example, this program uses the `Acme.Collections.Stack` class from the `acme.dll` assembly:</span></span>

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

<span data-ttu-id="d091b-123">Soubor *csproj* pro předchozí program projektu musí obsahovat referenční uzel pro kompilátor Jazyka C#, `acme.dll` aby bylo možné vyřešit odkazy na třídy v sestavení:</span><span class="sxs-lookup"><span data-stu-id="d091b-123">The *csproj* file for the preceding program's project must include a reference node for the C# compiler to resolve references to the classes in the `acme.dll` assembly:</span></span>

```xml
  <ItemGroup>
    <ProjectReference Include="..\acme\acme.csproj" />
  </ItemGroup>
```

<span data-ttu-id="d091b-124">Po tomto `dotnet build` přidání vytvoří spustitelný `example.exe`sestavení s názvem , který při spuštění vytvoří výstup:</span><span class="sxs-lookup"><span data-stu-id="d091b-124">After that addition, `dotnet build` creates an executable assembly named `example.exe`, which, when run, produces the output:</span></span>

```console
100
10
1
```

<span data-ttu-id="d091b-125">C# umožňuje zdrojový text programu, které mají být uloženy v několika zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="d091b-125">C# permits the source text of a program to be stored in several source files.</span></span> <span data-ttu-id="d091b-126">Při kompilaci vícesouborového programu Jazyka C# jsou všechny zdrojové soubory zpracovány společně a zdrojové soubory mohou volně odkazovat na sebe – koncepčně, je to, jako by všechny zdrojové soubory byly před zpracováním zřetězeny do jednoho velkého souboru.</span><span class="sxs-lookup"><span data-stu-id="d091b-126">When a multi-file C# program is compiled, all of the source files are processed together, and the source files can freely reference each other—conceptually, it is as if all the source files were concatenated into one large file before being processed.</span></span> <span data-ttu-id="d091b-127">Forward deklarace jsou nikdy potřeba v C# protože s několika výjimkami pořadí deklarace je nevýznamné.</span><span class="sxs-lookup"><span data-stu-id="d091b-127">Forward declarations are never needed in C# because, with few exceptions, declaration order is insignificant.</span></span> <span data-ttu-id="d091b-128">C# neomezuje zdrojový soubor na deklarování pouze jednoho veřejného typu ani nevyžaduje název zdrojového souboru tak, aby odpovídal typu deklarovanému ve zdrojovém souboru.</span><span class="sxs-lookup"><span data-stu-id="d091b-128">C# does not limit a source file to declaring only one public type nor does it require the name of the source file to match a type declared in the source file.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d091b-129">[Předchozí](index.md)
>[další](types-and-variables.md)</span><span class="sxs-lookup"><span data-stu-id="d091b-129">[Previous](index.md)
[Next](types-and-variables.md)</span></span>
