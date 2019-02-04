---
title: 'Postupy: Zobrazení obsahu sestavení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72778f769c2c3f030de0cd31d087e0a90ba6f508
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675033"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="63c52-102">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="63c52-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="63c52-103">Můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací Microsoft intermediate language (MSIL) v souboru.</span><span class="sxs-lookup"><span data-stu-id="63c52-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="63c52-104">Pokud je soubor zkoumají sestavení, můžete tyto informace zahrnout sestavení atributy, jakož i odkazy na jiných modulů a sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="63c52-105">Tyto informace mohou být užitečné při určování, zda je soubor sestavení nebo součástí sestavení, a zda soubor obsahuje odkazy na další moduly nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="63c52-106">K zobrazení obsahu sestavení pomocí Ildasm.exe</span><span class="sxs-lookup"><span data-stu-id="63c52-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="63c52-107">Typ **ildasm** \< *název sestavení*> na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="63c52-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="63c52-108">Například následující příkaz zpětně přeloží `Hello.exe` sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="63c52-109">Chcete-li zobrazit informace o manifestu sestavení</span><span class="sxs-lookup"><span data-stu-id="63c52-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="63c52-110">Dvakrát klikněte na ikonu MANIFESTU v okně MSIL Disassembler.</span><span class="sxs-lookup"><span data-stu-id="63c52-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c52-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="63c52-111">Example</span></span>  
 <span data-ttu-id="63c52-112">Následující příklad začíná základní program "Hello, World".</span><span class="sxs-lookup"><span data-stu-id="63c52-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="63c52-113">Po kompilaci programu, použijte Ildasm.exe pro převod ze strojového kódu Hello.exe sestavení a v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="63c52-114">Spuštění příkazu ildasm.exe Hello.exe sestavení a dvojitým kliknutím na ikonu MANIFESTU v okně IL DASM vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="63c52-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="63c52-115">Následující tabulka popisuje jednotlivé direktivy v manifestu sestavení ze sestavení Hello.exe použitých v příkladu.</span><span class="sxs-lookup"><span data-stu-id="63c52-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="63c52-116">– Direktiva</span><span class="sxs-lookup"><span data-stu-id="63c52-116">Directive</span></span>|<span data-ttu-id="63c52-117">Popis</span><span class="sxs-lookup"><span data-stu-id="63c52-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63c52-118">**.Assembly extern \<**  *název sestavení* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="63c52-119">Určuje další sestavení, který obsahuje položky, které odkazuje aktuální modul (v tomto příkladu `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="63c52-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="63c52-120">**.PublicKeyToken \<**  *tokenu* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="63c52-121">Určuje token skutečného klíče odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="63c52-122">**ver \<**  *číslo verze* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="63c52-123">Určuje číslo verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="63c52-124">**.Assembly \<**  *název sestavení* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="63c52-125">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="63c52-126">**algoritmus .hash \<**  *hodnotu int32* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="63c52-127">Určuje použitý algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="63c52-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="63c52-128">**ver \<**  *číslo verze* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="63c52-129">Určuje číslo verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="63c52-130">**.Module \<**  *název souboru* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="63c52-131">Určuje název moduly, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="63c52-132">V tomto příkladu se sestavení skládá pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="63c52-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="63c52-133">**.Subsystem \<**  *hodnota* **>**</span><span class="sxs-lookup"><span data-stu-id="63c52-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="63c52-134">Určuje prostředí aplikace, které jsou potřebné pro program.</span><span class="sxs-lookup"><span data-stu-id="63c52-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="63c52-135">V tomto příkladu hodnota 3 označuje, že je tento spustitelný soubor spustit z konzoly.</span><span class="sxs-lookup"><span data-stu-id="63c52-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="63c52-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="63c52-136">**.corflags**</span></span>|<span data-ttu-id="63c52-137">Aktuálně vyhrazené pole v metadatech.</span><span class="sxs-lookup"><span data-stu-id="63c52-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="63c52-138">Manifest sestavení může obsahovat několik různých direktivy, v závislosti na obsah sestavení.</span><span class="sxs-lookup"><span data-stu-id="63c52-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="63c52-139">Rozsáhlý seznam direktivy v manifestu sestavení, naleznete v dokumentaci ECMA zejména "oddíl II: Definice metadat a sémantika"a" oddílu III: Sada instrukcí soubor CIL se NAČTE".</span><span class="sxs-lookup"><span data-stu-id="63c52-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="63c52-140">Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.</span><span class="sxs-lookup"><span data-stu-id="63c52-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c52-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63c52-141">See also</span></span>
- [<span data-ttu-id="63c52-142">Doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="63c52-142">Application domains and assemblies</span></span>](application-domains.md#application-domains-and-assemblies)
- [<span data-ttu-id="63c52-143">Témata s návody k doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="63c52-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="63c52-144">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="63c52-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
