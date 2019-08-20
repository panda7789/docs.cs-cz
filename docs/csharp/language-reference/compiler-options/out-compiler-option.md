---
title: -out (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 51c66d6bc2064d8051415de2ac083da478355a99
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602592"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="744a6-102">-out (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="744a6-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="744a6-103">Možnost **-out** Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="744a6-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="744a6-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="744a6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="744a6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="744a6-106">Název výstupního souboru vytvořeného kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="744a6-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="744a6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="744a6-107">Remarks</span></span>  
 <span data-ttu-id="744a6-108">Na příkazovém řádku je možné zadat více výstupních souborů pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="744a6-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="744a6-109">Kompilátor očekává najít jeden nebo více souborů zdrojového kódu za možností **-out** .</span><span class="sxs-lookup"><span data-stu-id="744a6-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="744a6-110">Pak všechny soubory se zdrojovým kódem budou zkompilovány do výstupního souboru určeného parametrem.</span><span class="sxs-lookup"><span data-stu-id="744a6-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="744a6-111">Zadejte úplný název a příponu souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="744a6-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="744a6-112">Pokud nezadáte název výstupního souboru:</span><span class="sxs-lookup"><span data-stu-id="744a6-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="744a6-113">Soubor. exe převezme svůj název ze souboru zdrojového kódu, který obsahuje metodu **Main** .</span><span class="sxs-lookup"><span data-stu-id="744a6-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="744a6-114">Soubor. dll nebo. netmodule převezme svůj název z prvního souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="744a6-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="744a6-115">Soubor zdrojového kódu, který se používá k kompilování jednoho výstupního souboru, nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="744a6-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="744a6-116">Při vytváření více výstupních souborů v kompilaci příkazového řádku mějte na paměti, že pouze jeden z výstupních souborů může být sestavení a že pouze první výstupní soubor (implicitně nebo explicitně s parametrem **-out**) může být sestavení.</span><span class="sxs-lookup"><span data-stu-id="744a6-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="744a6-117">Všechny moduly, které jsou vytvořeny jako součást kompilace, se stanou soubory přidruženými k libovolnému sestavení, které je také vytvořeno v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="744a6-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="744a6-118">K zobrazení přidružených souborů použijte [Ildasm. exe](../../../framework/tools/ildasm-exe-il-disassembler.md) k zobrazení manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="744a6-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="744a6-119">Možnost kompilátoru-out je povinná, aby byl spustitelný soubor cílem sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="744a6-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="744a6-120">Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="744a6-120">For more information see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="744a6-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="744a6-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="744a6-122">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="744a6-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="744a6-123">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="744a6-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="744a6-124">Upravte vlastnost **název sestavení** .</span><span class="sxs-lookup"><span data-stu-id="744a6-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="744a6-125">Chcete-li nastavit tuto možnost kompilátoru programově <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> : je vlastnost jen pro čtení, která je určena kombinací typu projektu (exe, knihovna a tak dále) a názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="744a6-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="744a6-126">Úpravou jedné nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="744a6-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="744a6-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="744a6-127">Example</span></span>  
 <span data-ttu-id="744a6-128">Zkompilujte `t.cs` a vytvořte výstupní soubor `t.exe`a také `t2.cs` vytvořte a vytvořte výstupní soubor `mymodule.netmodule`modulu:</span><span class="sxs-lookup"><span data-stu-id="744a6-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="744a6-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="744a6-129">See also</span></span>

- [<span data-ttu-id="744a6-130">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="744a6-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="744a6-131">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="744a6-131">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="744a6-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="744a6-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
