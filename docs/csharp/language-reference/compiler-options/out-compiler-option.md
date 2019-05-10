---
title: -out (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 0cb0b78396731a9b8e127430cd06a9e71812d4fd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593038"
---
# <a name="-out-c-compiler-options"></a><span data-ttu-id="f91b3-102">-out (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f91b3-102">-out (C# Compiler Options)</span></span>
<span data-ttu-id="f91b3-103">**-Out** parametr určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="f91b3-103">The **-out** option specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f91b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f91b3-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="f91b3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f91b3-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="f91b3-106">Název výstupní soubor vytvořený kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="f91b3-106">The name of the output file created by the compiler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f91b3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f91b3-107">Remarks</span></span>  
 <span data-ttu-id="f91b3-108">Na příkazovém řádku je možné zadat víc výstupních souborů pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f91b3-108">On the command line, it is possible to specify multiple output files for your compilation.</span></span> <span data-ttu-id="f91b3-109">Kompilátor očekává, že jeden nebo více zdrojových souborů po **-out** možnost.</span><span class="sxs-lookup"><span data-stu-id="f91b3-109">The compiler expects to find one or more source code files following the **-out** option.</span></span> <span data-ttu-id="f91b3-110">Potom všechny soubory zdrojového kódu se zkompiluje do výstupní soubor určený parametrem, který **-out** možnost.</span><span class="sxs-lookup"><span data-stu-id="f91b3-110">Then, all source code files will be compiled into the output file specified by that **-out** option.</span></span>  
  
 <span data-ttu-id="f91b3-111">Zadejte úplný název a příponu souboru, který chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="f91b3-111">Specify the full name and extension of the file you want to create.</span></span>  
  
 <span data-ttu-id="f91b3-112">Pokud nezadáte název výstupního souboru:</span><span class="sxs-lookup"><span data-stu-id="f91b3-112">If you do not specify the name of the output file:</span></span>  
  
- <span data-ttu-id="f91b3-113">.Exe bude trvat, než jeho název souboru se zdrojovým kódem, který obsahuje **hlavní** metody.</span><span class="sxs-lookup"><span data-stu-id="f91b3-113">An .exe will take its name from the source code file that contains the **Main** method.</span></span>  
  
- <span data-ttu-id="f91b3-114">.Dll nebo .netmodule bude trvat, než jeho název prvního souboru se zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="f91b3-114">A .dll or .netmodule will take its name from the first source code file.</span></span>  
  
 <span data-ttu-id="f91b3-115">Soubor zdrojového kódu používá ke kompilaci jeden výstupní soubor nelze použít ve stejné kompilaci pro kompilaci jiné výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="f91b3-115">A source code file used to compile one output file cannot be used in the same compilation for the compilation of another output file.</span></span>  
  
 <span data-ttu-id="f91b3-116">Při vytváření několika výstupních souborů do příkazového řádku kompilace, mějte na paměti, kterou lze pouze jednu z výstupních souborů sestavení a pouze první výstupní soubor zadaný (implicitně nebo explicitně s **-out**) může být sestavení .</span><span class="sxs-lookup"><span data-stu-id="f91b3-116">When producing multiple output files in a command-line compilation, keep in mind that only one of the output files can be an assembly and that only the first output file specified (implicitly or explicitly with **-out**) can be the assembly.</span></span>  
  
 <span data-ttu-id="f91b3-117">Všechny moduly, které vytváří jako část kompilace stát soubory přidružené k žádné sestavení také vytvořit za kompilace.</span><span class="sxs-lookup"><span data-stu-id="f91b3-117">Any modules produced as part of a compilation become files associated with any assembly also produced in the compilation.</span></span> <span data-ttu-id="f91b3-118">Použití [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) zobrazíte zobrazit přidružené soubory v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="f91b3-118">Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the assembly manifest to see the associated files.</span></span>  
  
 <span data-ttu-id="f91b3-119">-Out – možnost kompilátoru je nutná pro exe cíl sestavení typu friend.</span><span class="sxs-lookup"><span data-stu-id="f91b3-119">The -out compiler option is required in order for an exe to be the target of a friend assembly.</span></span> <span data-ttu-id="f91b3-120">Další informace najdete v části [přátelských sestavení](../../../standard/assembly/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f91b3-120">For more information see [Friend Assemblies](../../../standard/assembly/friend-assemblies.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f91b3-121">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f91b3-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f91b3-122">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="f91b3-122">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="f91b3-123">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="f91b3-123">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="f91b3-124">Upravit **název sestavení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f91b3-124">Modify the **Assembly name** property.</span></span>  
  
     <span data-ttu-id="f91b3-125">Programové nastavení tohoto parametru kompilátoru: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> je vlastnost jen pro čtení, což je určeno ke kombinaci komponent typu projektu (exe, knihovny a tak dále) a název sestavení.</span><span class="sxs-lookup"><span data-stu-id="f91b3-125">To set this compiler option programmatically: the <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> is a read-only property, which is determined by a combination of the project type (exe, library, and so forth) and the assembly name.</span></span> <span data-ttu-id="f91b3-126">Úprava jeden nebo oba z těchto vlastností bude nutné nastavit název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="f91b3-126">Modifying one or both of these properties will be necessary to set the output file name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f91b3-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="f91b3-127">Example</span></span>  
 <span data-ttu-id="f91b3-128">Kompilace `t.cs` a vytvořit výstupní soubor `t.exe`, a také sestavení `t2.cs` a vytvoří výstupní soubor modulu `mymodule.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="f91b3-128">Compile `t.cs` and create output file `t.exe`, as well as build `t2.cs` and create module output file `mymodule.netmodule`:</span></span>  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f91b3-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f91b3-129">See also</span></span>

- [<span data-ttu-id="f91b3-130">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f91b3-130">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="f91b3-131">Přátelská sestavení</span><span class="sxs-lookup"><span data-stu-id="f91b3-131">Friend Assemblies</span></span>](../../../standard/assembly/friend-assemblies.md)
- [<span data-ttu-id="f91b3-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="f91b3-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
