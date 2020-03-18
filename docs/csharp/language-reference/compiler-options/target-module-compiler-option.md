---
title: -target:modul (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602438"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="d0074-102">-target:modul (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="d0074-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="d0074-103">Tato možnost způsobí, že kompilátor negeneruje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="d0074-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0074-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0074-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="d0074-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0074-105">Remarks</span></span>  
 <span data-ttu-id="d0074-106">Ve výchozím nastavení bude mít výstupní soubor vytvořený kompilací s touto možností příponu .netmodule.</span><span class="sxs-lookup"><span data-stu-id="d0074-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="d0074-107">Soubor, který nemá manifest sestavení, nelze načíst běžným jazykem rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0074-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="d0074-108">Takový soubor však může být začleněn do manifestu sestavení sestavení pomocí [-addmodule](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d0074-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="d0074-109">Pokud je v jedné kompilaci vytvořeno více než jeden modul, budou [interní](../keywords/internal.md) typy v jednom modulu k dispozici ostatním modulům v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="d0074-109">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="d0074-110">Když kód v jednom `internal` modulu odkazuje na typy v jiném modulu, pak musí být oba moduly začleněny do manifestu sestavení pomocí **-addmodule**.</span><span class="sxs-lookup"><span data-stu-id="d0074-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="d0074-111">Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d0074-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="d0074-112">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="d0074-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0074-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="d0074-113">Example</span></span>  
 <span data-ttu-id="d0074-114">Kompilace `in.cs` `in.netmodule`, vytváření :</span><span class="sxs-lookup"><span data-stu-id="d0074-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0074-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0074-115">See also</span></span>

- [<span data-ttu-id="d0074-116">-target (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d0074-116">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="d0074-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d0074-117">C# Compiler Options</span></span>](./index.md)
