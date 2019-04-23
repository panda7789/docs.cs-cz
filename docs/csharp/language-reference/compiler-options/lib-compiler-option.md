---
title: -lib (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 49920a46f1d970c3f00025c3dc3eb384c937aa99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319401"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="1f27c-102">-lib (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="1f27c-102">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="1f27c-103">**-Lib** Určuje umístění sestavení odkazováno prostřednictvím [– referenční dokumentace (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="1f27c-103">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f27c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f27c-104">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f27c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f27c-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="1f27c-106">Adresář pro kompilátor hledat v případě odkazovaných sestavení nebyl nalezen v aktuálním pracovním adresáři (adresář, ze kterého je vyvolán kompilátor) nebo v adresáři systému common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1f27c-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="1f27c-107">Nejmíň jeden další adresáře pro v vyhledat odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f27c-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="1f27c-108">Další názvy adresářů oddělte čárkou a bez mezer mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="1f27c-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f27c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f27c-109">Remarks</span></span>  
 <span data-ttu-id="1f27c-110">Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="1f27c-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="1f27c-111">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="1f27c-111">Current working directory.</span></span> <span data-ttu-id="1f27c-112">Toto je adresář, ze kterého je vyvolán kompilátor.</span><span class="sxs-lookup"><span data-stu-id="1f27c-112">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="1f27c-113">Common language runtime systémový adresář.</span><span class="sxs-lookup"><span data-stu-id="1f27c-113">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="1f27c-114">Adresáře určeného **-lib**.</span><span class="sxs-lookup"><span data-stu-id="1f27c-114">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="1f27c-115">Adresáře určené proměnnou prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="1f27c-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="1f27c-116">Použití **– referenční dokumentace** zadat odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f27c-116">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="1f27c-117">**-lib** je sčítání; zadání více než jednou připojí k jakékoli předchozí hodnoty ho.</span><span class="sxs-lookup"><span data-stu-id="1f27c-117">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="1f27c-118">O alternativu k použití **-lib** je zkopírovat do pracovního adresáře veškeré požadované sestavení; to vám umožní jednoduše předat název sestavení k **– referenční dokumentace**.</span><span class="sxs-lookup"><span data-stu-id="1f27c-118">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="1f27c-119">Pak můžete odstranit sestavení z pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="1f27c-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="1f27c-120">Protože není zadána cesta k závislého sestavení v manifestu sestavení, aplikaci lze spustit na cílovém počítači a vyhledá a použití sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f27c-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="1f27c-121">Protože kompilátor může odkazovat sestavení, neznamená, že modul common language runtime bude moci najít a načíst sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="1f27c-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="1f27c-122">Zobrazit [jak modul Runtime vyhledává sestavení](../../../framework/deployment/how-the-runtime-locates-assemblies.md) podrobnosti o tom, jak modul runtime vyhledá odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f27c-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1f27c-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f27c-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1f27c-124">Otevřete v projektu **stránky vlastností** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="1f27c-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="1f27c-125">Klikněte na tlačítko **cesta k odkazům** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="1f27c-125">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="1f27c-126">Upravte obsah pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1f27c-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="1f27c-127">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f27c-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f27c-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f27c-128">Example</span></span>  
 <span data-ttu-id="1f27c-129">Zkompilujte t2.cs vytvořte soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="1f27c-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="1f27c-130">Kompilátor bude hledat v pracovním adresáři a v kořenovém adresáři jednotce C odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="1f27c-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f27c-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f27c-131">See also</span></span>

- [<span data-ttu-id="1f27c-132">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f27c-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="1f27c-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1f27c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
