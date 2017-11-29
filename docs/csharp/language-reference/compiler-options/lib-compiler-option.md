---
title: "-lib (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 476bc43987b5ac8fa222b767b068a9ca14537bc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lib-c-compiler-options"></a><span data-ttu-id="946ca-102">/lib (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="946ca-102">/lib (C# Compiler Options)</span></span>
<span data-ttu-id="946ca-103">**/Lib** možnost určuje umístění sestavení odkazovaných pomocí možnosti [/Reference (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="946ca-103">The **/lib** option specifies the location of assemblies referenced by means of the [/reference (C# Compiler Options)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="946ca-104">Syntax</span></span>  
  
```console  
/lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="946ca-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="946ca-105">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="946ca-106">Adresář pro kompilátor hledat v případě odkazované sestavení nebyl nalezen v aktuální pracovní adresář (adresář, ze kterého je vyvolán kompilátor) nebo v adresáři systému modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="946ca-106">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="946ca-107">Jeden nebo více adresářů pro vyhledávání v odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="946ca-107">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="946ca-108">Další adresář názvy oddělte čárkou a bez mezer mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="946ca-108">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="946ca-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="946ca-109">Remarks</span></span>  
 <span data-ttu-id="946ca-110">Hledání kompilátoru pro odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="946ca-110">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="946ca-111">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="946ca-111">Current working directory.</span></span> <span data-ttu-id="946ca-112">Toto je adresář, ze kterého je vyvolán kompilátor.</span><span class="sxs-lookup"><span data-stu-id="946ca-112">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="946ca-113">Common language runtime systémového adresáře.</span><span class="sxs-lookup"><span data-stu-id="946ca-113">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="946ca-114">Adresáře určené **/lib**.</span><span class="sxs-lookup"><span data-stu-id="946ca-114">Directories specified by **/lib**.</span></span>  
  
4.  <span data-ttu-id="946ca-115">Adresáře určené proměnná prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="946ca-115">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="946ca-116">Použití **/reference** zadat odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="946ca-116">Use **/reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="946ca-117">**/ lib** je sčítání; zadání je více než jednou připojí k jakékoli předchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="946ca-117">**/lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="946ca-118">Alternativu k použití **/lib** je zkopírovat do pracovního adresáře potřebné sestavení; to vám umožní jednoduše předat název sestavení do **/reference**.</span><span class="sxs-lookup"><span data-stu-id="946ca-118">An alternative to using **/lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **/reference**.</span></span> <span data-ttu-id="946ca-119">Potom můžete odstranit sestavení z pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="946ca-119">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="946ca-120">Vzhledem k tomu, že cesta k závislého sestavení není zadané v manifestu sestavení, aplikaci lze spustit na cílovém počítači a vyhledá a použití sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="946ca-120">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="946ca-121">Protože kompilátor, můžete odkazovat sestavení neznamená, že modul CLR bude moct najít a načíst sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="946ca-121">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="946ca-122">V tématu [jak modul Runtime vyhledává sestavení](../../../framework/deployment/how-the-runtime-locates-assemblies.md) podrobnosti o vyhledávání odkazovaná sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="946ca-122">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="946ca-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="946ca-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="946ca-124">Otevření projektu **stránky vlastností** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="946ca-124">Open the project's **Property Pages** dialog box.</span></span>  
  
2.  <span data-ttu-id="946ca-125">Klikněte na tlačítko **odkazy cesta** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="946ca-125">Click the **References Path** property page.</span></span>  
  
3.  <span data-ttu-id="946ca-126">Upravte obsah pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="946ca-126">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="946ca-127">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span><span class="sxs-lookup"><span data-stu-id="946ca-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="946ca-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="946ca-128">Example</span></span>  
 <span data-ttu-id="946ca-129">Zkompiluje t2.cs a vytvoří soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="946ca-129">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="946ca-130">Kompilátor bude hledat v pracovní adresář a v kořenovém adresáři jednotky C odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="946ca-130">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc /lib:c:\ /reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="946ca-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="946ca-131">See Also</span></span>  
 [<span data-ttu-id="946ca-132">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="946ca-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="946ca-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="946ca-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
