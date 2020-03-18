---
title: -out (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970383"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="02dff-102">-out (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="02dff-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="02dff-103">Volba **-out** určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="02dff-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02dff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02dff-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="02dff-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="02dff-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="02dff-106">Název výstupního souboru vytvořeného kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="02dff-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02dff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02dff-107">Remarks</span></span>  
 <span data-ttu-id="02dff-108">Na příkazovém řádku je možné zadat více výstupních souborů pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="02dff-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="02dff-109">Kompilátor očekává, že najít jeden nebo více souborů zdrojového kódu po **-out** možnost.</span><span class="sxs-lookup"><span data-stu-id="02dff-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="02dff-110">Poté budou všechny soubory zdrojového kódu zkompilovány do výstupního souboru určeného tímto volbou **-out.**</span><span class="sxs-lookup"><span data-stu-id="02dff-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="02dff-111">Zadejte úplný název a příponu souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="02dff-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="02dff-112">Pokud nezadáte název výstupního souboru:</span><span class="sxs-lookup"><span data-stu-id="02dff-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="02dff-113">A.exe přebere svůj název ze souboru zdrojového kódu, který obsahuje **Metodu Main.**</span><span class="sxs-lookup"><span data-stu-id="02dff-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="02dff-114">Modul .dll nebo .netmodule převezme svůj název z prvního souboru zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="02dff-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="02dff-115">Soubor zdrojového kódu použitý ke kompilaci jednoho výstupního souboru nelze použít ve stejné kompilaci pro kompilaci jiného výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="02dff-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="02dff-116">Při vytváření více výstupních souborů v kompilaci příkazového řádku mějte na paměti, že pouze jeden z výstupních souborů může být sestavení a že pouze první výstupní soubor zadaný (implicitně nebo explicitně s **-out)** může být sestavení.</span><span class="sxs-lookup"><span data-stu-id="02dff-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="02dff-117">Všechny moduly vytvořené jako součást kompilace se stanou soubory přidruženými k libovolnému sestavení, které je také vytvořeno v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="02dff-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="02dff-118">Pomocí [souboru ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) zobrazíte manifest sestavení a zobrazte přidružené soubory.</span><span class="sxs-lookup"><span data-stu-id="02dff-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="02dff-119">Možnost kompilátoru -out je vyžadována, aby exe bylo cílem sestavení přítele.</span><span class="sxs-lookup"><span data-stu-id="02dff-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="02dff-120">Další informace naleznete [v tématu Friend Assemblies](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="02dff-120">For more information see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="02dff-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="02dff-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="02dff-122">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="02dff-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="02dff-123">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="02dff-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="02dff-124">Upravte vlastnost **název sestavení.**</span><span class="sxs-lookup"><span data-stu-id="02dff-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="02dff-125">Chcete-li nastavit tuto možnost kompilátoru <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> programově: je vlastnost jen pro čtení, která je určena kombinací typu projektu (exe, knihovna a tak dále) a název sestavení.</span><span class="sxs-lookup"><span data-stu-id="02dff-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="02dff-126">Změna jedné nebo obou těchto vlastností bude nutné nastavit název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="02dff-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02dff-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="02dff-127">Example</span></span>  
 <span data-ttu-id="02dff-128">Kompilovat `t.cs` a `t.exe`vytvářet výstupní `t2.cs` soubor , `mymodule.netmodule`stejně jako vytvořit a vytvořit výstupní soubor modulu :</span><span class="sxs-lookup"><span data-stu-id="02dff-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="02dff-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="02dff-129">See also</span></span>

- [<span data-ttu-id="02dff-130">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="02dff-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="02dff-131">Přátelské sestavy</span><span class="sxs-lookup"><span data-stu-id="02dff-131">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
- [<span data-ttu-id="02dff-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="02dff-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
