---
title: "Postupy: Zobrazení obsahu sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddbbf9fda01328986bf586203116fdabbcd9b55e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="b959a-102">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="b959a-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="b959a-103">Můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pro zobrazení informací (MSIL intermediate language) Microsoft v souboru.</span><span class="sxs-lookup"><span data-stu-id="b959a-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="b959a-104">Pokud se jedná o prohlížení je sestavení, můžete tyto informace zahrnují sestavení atributy, stejně jako odkazy na jiné moduly a sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="b959a-105">Tato informace může být užitečné při určování, zda je soubor sestavení nebo součástí sestavení, a zda má soubor odkazy na další moduly nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="b959a-106">K zobrazení obsahu sestavení pomocí Ildasm.exe</span><span class="sxs-lookup"><span data-stu-id="b959a-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="b959a-107">Typ **ildasm** \< *název sestavení*> na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="b959a-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="b959a-108">Například následující příkaz provede zpětný `Hello.exe` sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="b959a-109">Chcete-li zobrazit informace o sestavení manifestu</span><span class="sxs-lookup"><span data-stu-id="b959a-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="b959a-110">Dvakrát klikněte na ikonu MANIFESTU v okně MSIL Disassembler.</span><span class="sxs-lookup"><span data-stu-id="b959a-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b959a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="b959a-111">Example</span></span>  
 <span data-ttu-id="b959a-112">Následující příklad spustí základní program "Hello, World".</span><span class="sxs-lookup"><span data-stu-id="b959a-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="b959a-113">Po kompilace programu, použijte Ildasm.exe pro zpětný překlad sestavení Hello.exe a manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="b959a-114">Spuštění příkazu ildasm.exe pro sestavení Hello.exe a dvakrát klikněte na ikonu MANIFESTU v okně IL DASM vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b959a-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="b959a-115">Následující tabulka popisuje každý – direktiva v manifestu sestavení Hello.exe použitého v příkladu.</span><span class="sxs-lookup"><span data-stu-id="b959a-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="b959a-116">– Direktiva</span><span class="sxs-lookup"><span data-stu-id="b959a-116">Directive</span></span>|<span data-ttu-id="b959a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b959a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b959a-118">**.Assembly extern \<**  *název sestavení***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="b959a-119">Určuje jiná sestavení, která obsahuje položky, které odkazuje aktuální modul (v tomto příkladu `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="b959a-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="b959a-120">**.PublicKeyToken \<**  *tokenu***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="b959a-121">Určuje token skutečný klíč odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="b959a-122">**ver \<**  *číslo verze***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="b959a-123">Určuje číslo verze odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="b959a-124">**.Assembly \<**  *název sestavení***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="b959a-125">Určuje název sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="b959a-126">**algoritmus .hash \<**  *hodnota int32***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="b959a-127">Určuje použitý algoritmus hash.</span><span class="sxs-lookup"><span data-stu-id="b959a-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="b959a-128">**ver \<**  *číslo verze***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="b959a-129">Určuje číslo verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="b959a-130">**.Module \<**  *název souboru***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="b959a-131">Určuje název modulů, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="b959a-132">V tomto příkladu se sestavení skládá z pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="b959a-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="b959a-133">**.Subsystem \<**  *hodnotu***>**</span><span class="sxs-lookup"><span data-stu-id="b959a-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="b959a-134">Určuje prostředí aplikace, které jsou potřebné pro program.</span><span class="sxs-lookup"><span data-stu-id="b959a-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="b959a-135">V tomto příkladu hodnota 3 značí, že se tento spustitelný soubor spustit z konzoly.</span><span class="sxs-lookup"><span data-stu-id="b959a-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="b959a-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="b959a-136">**.corflags**</span></span>|<span data-ttu-id="b959a-137">Aktuálně rezervované pole v metadatech.</span><span class="sxs-lookup"><span data-stu-id="b959a-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="b959a-138">Manifest sestavení může obsahovat několik různých direktivy, v závislosti na obsahu sestavení.</span><span class="sxs-lookup"><span data-stu-id="b959a-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="b959a-139">Rozsáhlého seznamu direktiv v manifestu sestavení najdete v dokumentaci ECMA, zejména "Oddílu II: Metadata definice a sémantiku" a "Oddílu III: soubor CIL instrukce nastavení".</span><span class="sxs-lookup"><span data-stu-id="b959a-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="b959a-140">Dokumentace je k dispozici online; v tématu [ECMA C# a společné jazykové infrastruktury normy](http://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [standardní standardy ECMA-335 - společné jazykové infrastruktury (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="b959a-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b959a-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="b959a-141">See Also</span></span>  
 [<span data-ttu-id="b959a-142">Aplikační domény a sestavení</span><span class="sxs-lookup"><span data-stu-id="b959a-142">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [<span data-ttu-id="b959a-143">Postupy: témata doménám a sestavením aplikací</span><span class="sxs-lookup"><span data-stu-id="b959a-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [<span data-ttu-id="b959a-144">Ildasm.exe (IL Disassembler)</span><span class="sxs-lookup"><span data-stu-id="b959a-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
