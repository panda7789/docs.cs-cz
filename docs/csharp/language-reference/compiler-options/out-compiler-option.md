---
description: -out (možnosti kompilátoru C#)
title: -out (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: d1b79879639e1cbdc3dc040977d9fcd0c3a73602
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125017"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="fa6e3-103">-out (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="fa6e3-103">-out (C# Compiler Options)</span></span>
<span data-ttu-id="fa6e3-104">Možnost **-out** Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-104">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa6e3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa6e3-105">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa6e3-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fa6e3-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="fa6e3-107">Název výstupního souboru vytvořeného kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-107">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa6e3-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa6e3-108">Remarks</span></span>  
 <span data-ttu-id="fa6e3-109">Na příkazovém řádku je možné zadat více výstupních souborů pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-109">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="fa6e3-110">Kompilátor očekává najít jeden nebo více souborů zdrojového kódu za možností **-out** .</span><span class="sxs-lookup"><span data-stu-id="fa6e3-110">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="fa6e3-111">Pak všechny soubory se zdrojovým kódem budou zkompilovány do výstupního souboru **určeného parametrem** .</span><span class="sxs-lookup"><span data-stu-id="fa6e3-111">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="fa6e3-112">Zadejte úplný název a příponu souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-112">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="fa6e3-113">Pokud nezadáte název výstupního souboru:</span><span class="sxs-lookup"><span data-stu-id="fa6e3-113">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="fa6e3-114">Soubor. exe převezme svůj název ze souboru zdrojového kódu, který obsahuje metodu **Main** .</span><span class="sxs-lookup"><span data-stu-id="fa6e3-114">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="fa6e3-115">Soubor. dll nebo. netmodule převezme svůj název z prvního souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-115">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="fa6e3-116">Soubor zdrojového kódu, který se používá k kompilování jednoho výstupního souboru, nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-116">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="fa6e3-117">Při vytváření více výstupních souborů v kompilaci příkazového řádku mějte na paměti, že pouze jeden z výstupních souborů může být sestavení a že pouze první výstupní soubor (implicitně nebo explicitně s parametrem **-out**) může být sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-117">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="fa6e3-118">Všechny moduly, které jsou vytvořeny jako součást kompilace, se stanou soubory přidruženými k libovolnému sestavení, které je také vytvořeno v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-118">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="fa6e3-119">Použijte [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) k zobrazení manifestu sestavení, aby se zobrazily přidružené soubory.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-119">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="fa6e3-120">Možnost kompilátoru-out je povinná, aby byl spustitelný soubor cílem sestavení typu Friend.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-120">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="fa6e3-121">Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="fa6e3-121">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fa6e3-122">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fa6e3-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="fa6e3-123">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="fa6e3-124">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="fa6e3-124">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="fa6e3-125">Upravte vlastnost **název sestavení** .</span><span class="sxs-lookup"><span data-stu-id="fa6e3-125">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="fa6e3-126">Chcete-li nastavit tuto možnost kompilátoru programově: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> je vlastnost jen pro čtení, která je určena kombinací typu projektu (exe, knihovna a tak dále) a názvu sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-126">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="fa6e3-127">Úpravou jedné nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="fa6e3-127">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa6e3-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa6e3-128">Example</span></span>  
 <span data-ttu-id="fa6e3-129">Zkompilujte `t.cs` a vytvořte výstupní soubor a `t.exe` také vytvořte `t2.cs` a vytvořte výstupní soubor modulu `mymodule.netmodule` :</span><span class="sxs-lookup"><span data-stu-id="fa6e3-129">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa6e3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa6e3-130">See also</span></span>

- [<span data-ttu-id="fa6e3-131">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="fa6e3-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="fa6e3-132">Friend – sestavení</span><span class="sxs-lookup"><span data-stu-id="fa6e3-132">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="fa6e3-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="fa6e3-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
