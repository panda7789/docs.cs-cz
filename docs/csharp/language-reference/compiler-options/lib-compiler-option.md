---
title: -lib (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606822"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="b55d5-102">-lib (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b55d5-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="b55d5-103">Možnost **-lib** určuje umístění sestavení odkazovaných pomocí možnosti [-reference (C# Compiler Options).](./reference-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="b55d5-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b55d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b55d5-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b55d5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b55d5-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="b55d5-106">Adresář pro kompilátor, ve kterém se má podívat, pokud odkazované sestavení není nalezeno v aktuálním pracovním adresáři (adresář, ze kterého se odvoláváte na kompilátor) nebo v systémovém adresáři běžného jazyka runtime.</span><span class="sxs-lookup"><span data-stu-id="b55d5-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="b55d5-107">Jeden nebo více dalších adresářů, které mají být vyhledány v odkazech na sestavení.</span><span class="sxs-lookup"><span data-stu-id="b55d5-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="b55d5-108">Oddělte další názvy adresářů čárkou a bez mezermezi nimi.</span><span class="sxs-lookup"><span data-stu-id="b55d5-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b55d5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b55d5-109">Remarks</span></span>  
 <span data-ttu-id="b55d5-110">Kompilátor hledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="b55d5-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="b55d5-111">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="b55d5-111">Current working directory.</span></span> <span data-ttu-id="b55d5-112">Toto je adresář, ze kterého je vyvolán kompilátor.</span><span class="sxs-lookup"><span data-stu-id="b55d5-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="b55d5-113">Systémový adresář běžného běhu runtime.</span><span class="sxs-lookup"><span data-stu-id="b55d5-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="b55d5-114">Adresáře určené **parametrem -lib**.</span><span class="sxs-lookup"><span data-stu-id="b55d5-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="b55d5-115">Adresáře určené proměnnou prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="b55d5-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="b55d5-116">Použijte **-reference** k určení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="b55d5-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="b55d5-117">**-lib** je doplňková látka; zadání více než jednou připojí k jakékoli předchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b55d5-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="b55d5-118">Alternativou k použití **-lib** je zkopírovat do pracovního adresáře všechna požadovaná sestavení; To vám umožní jednoduše předat název sestavení **-reference**.</span><span class="sxs-lookup"><span data-stu-id="b55d5-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="b55d5-119">Potom můžete odstranit sestavení z pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="b55d5-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="b55d5-120">Vzhledem k tomu, že cesta k závislému sestavení není zadána v manifestu sestavení, aplikace může být spuštěna v cílovém počítači a vyhledá a použije sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b55d5-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="b55d5-121">Vzhledem k tomu, že kompilátor může odkazovat na sestavení neznamená, že běžný jazyk runtime bude moci najít a načíst sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="b55d5-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="b55d5-122">Podrobnosti o tom, jak runtime vyhledává odkazovaná sestavení, naleznete v tématu [Jak runtime vyhledává sestavení.](../../../framework/deployment/how-the-runtime-locates-assemblies.md)</span><span class="sxs-lookup"><span data-stu-id="b55d5-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b55d5-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b55d5-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b55d5-124">Otevřete dialogové okno **Stránky vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="b55d5-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="b55d5-125">Klikněte na stránku **vlastností Cesta odkazů.**</span><span class="sxs-lookup"><span data-stu-id="b55d5-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="b55d5-126">Upravte obsah seznamu.</span><span class="sxs-lookup"><span data-stu-id="b55d5-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="b55d5-127">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="b55d5-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b55d5-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="b55d5-128">Example</span></span>  
 <span data-ttu-id="b55d5-129">Zkompilujte t2.cs a vytvořte soubor EXE.</span><span class="sxs-lookup"><span data-stu-id="b55d5-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="b55d5-130">Kompilátor bude hledat v pracovním adresáři a v kořenovém adresáři jednotky C pro odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="b55d5-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b55d5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b55d5-131">See also</span></span>

- [<span data-ttu-id="b55d5-132">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b55d5-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b55d5-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b55d5-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
