---
description: -lib (možnosti kompilátoru C#)
title: -lib (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: e53c54dc446d9fea87a9b7a336a38ffaa31704e9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125446"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="578e8-103">-lib (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="578e8-103">-lib (C# Compiler Options)</span></span>
<span data-ttu-id="578e8-104">Možnost **-lib** určuje umístění sestavení, na která odkazuje, prostřednictvím možnosti [-Reference (možnosti kompilátoru C#)](./reference-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="578e8-104">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578e8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="578e8-105">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="578e8-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="578e8-106">Arguments</span></span>  
 `dir1`  
 <span data-ttu-id="578e8-107">Adresář, ve kterém se má kompilátor hledat, pokud odkazované sestavení není nalezeno v aktuálním pracovním adresáři (adresář, ze kterého vyvoláváte kompilátor), nebo v adresáři systému společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="578e8-107">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="578e8-108">Jeden nebo více dalších adresářů, ve kterých se má hledat odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="578e8-108">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="578e8-109">Další názvy adresářů oddělujte čárkami a bez mezer mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="578e8-109">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="578e8-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="578e8-110">Remarks</span></span>  
 <span data-ttu-id="578e8-111">Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="578e8-111">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="578e8-112">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="578e8-112">Current working directory.</span></span> <span data-ttu-id="578e8-113">Toto je adresář, ze kterého je kompilátor vyvolán.</span><span class="sxs-lookup"><span data-stu-id="578e8-113">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="578e8-114">Systémový adresář společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="578e8-114">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="578e8-115">Adresáře určené parametrem **-lib**.</span><span class="sxs-lookup"><span data-stu-id="578e8-115">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="578e8-116">Adresáře určené proměnnou prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="578e8-116">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="578e8-117">Použijte **– odkaz** k určení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="578e8-117">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="578e8-118">**-lib** je doplňková; zadáním více než jednou se připojí k jakýmkoli předchozím hodnotám.</span><span class="sxs-lookup"><span data-stu-id="578e8-118">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="578e8-119">Alternativou k použití **-lib** je zkopírovat do pracovního adresáře všechna požadovaná sestavení; To vám umožní jednoduše předat název sestavení **odkazem**.</span><span class="sxs-lookup"><span data-stu-id="578e8-119">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="578e8-120">Pak můžete sestavení odstranit z pracovního adresáře.</span><span class="sxs-lookup"><span data-stu-id="578e8-120">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="578e8-121">Vzhledem k tomu, že cesta k závislému sestavení není zadána v manifestu sestavení, lze aplikaci spustit v cílovém počítači a vyhledat a použít sestavení v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="578e8-121">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="578e8-122">Vzhledem k tomu, že kompilátor může odkazovat na sestavení, neznamená, že modul CLR (Common Language Runtime) bude moci najít a načíst sestavení za běhu.</span><span class="sxs-lookup"><span data-stu-id="578e8-122">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="578e8-123">Podívejte [se, jak modul runtime vyhledává sestavení](../../../framework/deployment/how-the-runtime-locates-assemblies.md) pro podrobnosti o tom, jak modul runtime vyhledává odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="578e8-123">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="578e8-124">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="578e8-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="578e8-125">Otevřete dialogové okno **stránky vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="578e8-125">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="578e8-126">Klikněte na stránku vlastností **cesta k odkazům** .</span><span class="sxs-lookup"><span data-stu-id="578e8-126">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="578e8-127">Úprava obsahu pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="578e8-127">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="578e8-128">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A> .</span><span class="sxs-lookup"><span data-stu-id="578e8-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="578e8-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="578e8-129">Example</span></span>  
 <span data-ttu-id="578e8-130">Zkompilujte t2.cs a vytvořte soubor. exe.</span><span class="sxs-lookup"><span data-stu-id="578e8-130">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="578e8-131">Kompilátor bude hledat odkazy na sestavení v pracovním adresáři a v kořenovém adresáři jednotky C.</span><span class="sxs-lookup"><span data-stu-id="578e8-131">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="578e8-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="578e8-132">See also</span></span>

- [<span data-ttu-id="578e8-133">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="578e8-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="578e8-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="578e8-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
