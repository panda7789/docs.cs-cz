---
title: "-out (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca85293086f8747cc4aaff02e7d9b5628b1e88a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="10658-102">-out (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="10658-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="10658-103">**-Out** možnost určuje název souboru výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="10658-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10658-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10658-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="10658-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="10658-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="10658-106">Název výstupního souboru vytvořené kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="10658-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10658-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10658-107">Remarks</span></span>  
 <span data-ttu-id="10658-108">Na příkazovém řádku je možné zadat více výstupní soubory pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="10658-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="10658-109">Kompilátor očekává, že jeden nebo více zdrojových souborů následující **-out** možnost.</span><span class="sxs-lookup"><span data-stu-id="10658-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="10658-110">Potom všechny soubory zdrojového kódu se zkompiluje do výstupního souboru, který určeného **-out** možnost.</span><span class="sxs-lookup"><span data-stu-id="10658-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="10658-111">Zadejte úplný název a příponu souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="10658-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="10658-112">Pokud nezadáte název výstupního souboru:</span><span class="sxs-lookup"><span data-stu-id="10658-112">If you do not specify the name of the output file:</span></span>  
  
-   <span data-ttu-id="10658-113">.exe bude trvat její název ze zdrojového souboru kódu, který obsahuje **hlavní** metoda.</span><span class="sxs-lookup"><span data-stu-id="10658-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
-   <span data-ttu-id="10658-114">.Dll nebo .netmodule převezme název z první souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="10658-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="10658-115">Soubor zdrojového kódu použít zkompilovat jednu výstupní soubor nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="10658-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="10658-116">Při vytváření více výstupních souborů v kompilaci příkazového řádku, mějte na paměti, že pouze jeden výstupních souborů může být sestavení a pouze první výstupní soubor zadaný (implicitně nebo explicitně s **-out**) může být sestavení .</span><span class="sxs-lookup"><span data-stu-id="10658-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="10658-117">Všechny moduly, vytvořené jako součást kompilace stát soubory přidružené k žádné sestavení také vytvořené ve kompilaci.</span><span class="sxs-lookup"><span data-stu-id="10658-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="10658-118">Použití [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) zobrazíte manifest sestavení zobrazíte přidružené soubory.</span><span class="sxs-lookup"><span data-stu-id="10658-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="10658-119">-Out – možnost kompilátoru je nutná pro exe jako cíl přátelského sestavení.</span><span class="sxs-lookup"><span data-stu-id="10658-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="10658-120">Další informace najdete v části [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="10658-120">For more information see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="10658-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="10658-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="10658-122">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="10658-122">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="10658-123">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="10658-123">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="10658-124">Změnit **název sestavení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="10658-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="10658-125">Nastavení této možnosti kompilátoru programu: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> je jen pro čtení vlastnost, která je určena kombinací typu projektu (exe, knihovny a tak dále) a název sestavení.</span><span class="sxs-lookup"><span data-stu-id="10658-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="10658-126">Úprava jednoho nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="10658-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10658-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="10658-127">Example</span></span>  
 <span data-ttu-id="10658-128">Kompilace `t.cs` a vytvoření výstupního souboru `t.exe`, a také sestavení `t2.cs` a vytvoření výstupního souboru modulu `mymodule.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="10658-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="10658-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="10658-129">See Also</span></span>  
 [<span data-ttu-id="10658-130">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="10658-130">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="10658-131">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="10658-131">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="10658-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="10658-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
