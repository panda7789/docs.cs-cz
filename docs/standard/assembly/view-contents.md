---
title: 'Postup: Zobrazení obsahu sestavení'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187391"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="7cd1a-102">Postup: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="7cd1a-102">How to: View assembly contents</span></span>

<span data-ttu-id="7cd1a-103">[Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) můžete použít k zobrazení informací o zprostředkujícím jazyce Microsoft (MSIL) v souboru.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-103">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="7cd1a-104">Pokud je zkoumaný soubor sestavením, mohou tyto informace obsahovat atributy sestavení a odkazy na jiné moduly a sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-104">If the file being examined is an assembly, this information can include the assembly's attributes and references to other modules and assemblies.</span></span> <span data-ttu-id="7cd1a-105">Tyto informace mohou být užitečné při určování, zda je soubor sestavení nebo součástí sestavení a zda soubor obsahuje odkazy na jiné moduly nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-105">This information can be helpful in determining whether a file is an assembly or part of an assembly and whether the file has references to other modules or assemblies.</span></span>

<span data-ttu-id="7cd1a-106">Chcete-li zobrazit obsah sestavy pomocí *aplikace Ildasm.exe*, zadejte **název sestavy ildasmu \<>** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-106">To display the contents of an assembly using *Ildasm.exe*, enter **ildasm \<assembly name>** at a command prompt.</span></span> <span data-ttu-id="7cd1a-107">Například následující příkaz rozebírá sestavení *Hello.exe.*</span><span class="sxs-lookup"><span data-stu-id="7cd1a-107">For example, the following command disassembles the *Hello.exe* assembly.</span></span>

```cmd
ildasm Hello.exe
```

<span data-ttu-id="7cd1a-108">Chcete-li zobrazit informace o manifestu sestavení, poklepejte na ikonu **Manifest** u okna Disassembler msil.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-108">To view assembly manifest information, double-click the **Manifest** icon in the MSIL Disassembler window.</span></span>

## <a name="example"></a><span data-ttu-id="7cd1a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cd1a-109">Example</span></span>

<span data-ttu-id="7cd1a-110">Následující příklad začíná základním programem "Hello World".</span><span class="sxs-lookup"><span data-stu-id="7cd1a-110">The following example starts with a basic "Hello World" program.</span></span> <span data-ttu-id="7cd1a-111">Po kompilaci programu použijte *ildasm.exe* k demontáži sestavení *Hello.exe* a zobrazení manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-111">After compiling the program, use *Ildasm.exe* to disassemble the *Hello.exe* assembly and view the assembly manifest.</span></span>

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

<span data-ttu-id="7cd1a-112">Spuštění příkazu *ildasm.exe* v sestavení *Hello.exe* a poklepáním na ikonu **Manifest** v okně MSIL Disassembler vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7cd1a-112">Running the command *ildasm.exe* on the *Hello.exe* assembly and double-clicking the **Manifest** icon in the MSIL Disassembler window produces the following output:</span></span>

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

<span data-ttu-id="7cd1a-113">Následující tabulka popisuje každou direktivu v manifestu sestavení sestavení *Hello.exe* použitého v příkladu:</span><span class="sxs-lookup"><span data-stu-id="7cd1a-113">The following table describes each directive in the assembly manifest of the *Hello.exe* assembly used in the example:</span></span>

|<span data-ttu-id="7cd1a-114">Směrnice</span><span class="sxs-lookup"><span data-stu-id="7cd1a-114">Directive</span></span>|<span data-ttu-id="7cd1a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7cd1a-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7cd1a-116">**Název sestavení \<.assembly extern>**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-116">**.assembly extern \<assembly name>**</span></span>|<span data-ttu-id="7cd1a-117">Určuje jiné sestavení, které obsahuje položky odkazované aktuálním modulem (v tomto příkladu). `mscorlib`</span><span class="sxs-lookup"><span data-stu-id="7cd1a-117">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|
|<span data-ttu-id="7cd1a-118">**>tokenu \<tokenu .publickeytoken**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-118">**.publickeytoken \<token>**</span></span>|<span data-ttu-id="7cd1a-119">Určuje token skutečného klíče odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-119">Specifies the token of the actual key of the referenced assembly.</span></span>|
|<span data-ttu-id="7cd1a-120">**Číslo \<verze .ver>**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-120">**.ver \<version number>**</span></span>|<span data-ttu-id="7cd1a-121">Určuje číslo verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-121">Specifies the version number of the referenced assembly.</span></span>|
|<span data-ttu-id="7cd1a-122">**>\<názvu sestavení sestavení .assembly**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-122">**.assembly \<assembly name>**</span></span>|<span data-ttu-id="7cd1a-123">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-123">Specifies the assembly name.</span></span>|
|<span data-ttu-id="7cd1a-124">**hodnota algoritmu \<.hash int32>**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-124">**.hash algorithm \<int32 value>**</span></span>|<span data-ttu-id="7cd1a-125">Určuje použitý algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-125">Specifies the hash algorithm used.</span></span>|
|<span data-ttu-id="7cd1a-126">**Číslo \<verze .ver>**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-126">**.ver \<version number>**</span></span>|<span data-ttu-id="7cd1a-127">Určuje číslo verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-127">Specifies the version number of the assembly.</span></span>|
|<span data-ttu-id="7cd1a-128">**>\<názvu souboru modulu**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-128">**.module \<file name>**</span></span>|<span data-ttu-id="7cd1a-129">Určuje název modulů, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-129">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="7cd1a-130">V tomto příkladu se sestavení skládá pouze z jednoho souboru.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-130">In this example, the assembly consists of only one file.</span></span>|
|<span data-ttu-id="7cd1a-131">**Hodnota .subsystému \<>**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-131">**.subsystem \<value>**</span></span>|<span data-ttu-id="7cd1a-132">Určuje prostředí aplikace požadované pro program.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-132">Specifies the application environment required for the program.</span></span> <span data-ttu-id="7cd1a-133">V tomto příkladu hodnota 3 označuje, že tento spustitelný soubor je spuštěn z konzoly.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-133">In this example, the value 3 indicates that this executable is run from a console.</span></span>|
|<span data-ttu-id="7cd1a-134">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="7cd1a-134">**.corflags**</span></span>|<span data-ttu-id="7cd1a-135">Aktuálně vyhrazené pole v metadatech.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-135">Currently a reserved field in the metadata.</span></span>|

<span data-ttu-id="7cd1a-136">Manifest sestavení může obsahovat řadu různých směrnic v závislosti na obsahu sestavení.</span><span class="sxs-lookup"><span data-stu-id="7cd1a-136">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="7cd1a-137">Rozsáhlý seznam směrnic v manifestu sestavení naleznete v dokumentaci Ecma, zejména "Oddíl II: Definice metadat a sémantika" a "Oddíl III: SADA instrukcí CIL":</span><span class="sxs-lookup"><span data-stu-id="7cd1a-137">For an extensive list of the directives in the assembly manifest, see the Ecma documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set":</span></span>

- [<span data-ttu-id="7cd1a-138">Standardy ECMA C# a společné jazykové infrastruktury</span><span class="sxs-lookup"><span data-stu-id="7cd1a-138">ECMA C# and Common Language Infrastructure standards</span></span>](../components.md#applicable-standards)
- [<span data-ttu-id="7cd1a-139">Standardní ECMA-335 – společná jazyková infrastruktura (CLI)</span><span class="sxs-lookup"><span data-stu-id="7cd1a-139">Standard ECMA-335 - Common Language Infrastructure (CLI)</span></span>](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a><span data-ttu-id="7cd1a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cd1a-140">See also</span></span>

- [<span data-ttu-id="7cd1a-141">Aplikační domény a sestavení</span><span class="sxs-lookup"><span data-stu-id="7cd1a-141">Application domains and assemblies</span></span>](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="7cd1a-142">Aplikační domény a sestavení s tématy s postupy</span><span class="sxs-lookup"><span data-stu-id="7cd1a-142">Application domains and assemblies how-to topics</span></span>](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="7cd1a-143">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="7cd1a-143">Ildasm.exe (IL Disassembler)</span></span>](../../framework/tools/ildasm-exe-il-disassembler.md)
