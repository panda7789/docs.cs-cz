---
title: '-target: module (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 7cc0e48a7a4a3ec3f28c89e80fadf6aa7e1130f2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865059"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="127e7-102">-target: module (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="127e7-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="127e7-103">Tato možnost způsobí, že kompilátor nevygeneruje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="127e7-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="127e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="127e7-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="127e7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="127e7-105">Remarks</span></span>  
 <span data-ttu-id="127e7-106">Ve výchozím nastavení bude mít výstupní soubor vytvořil kompilaci s touto možností rozšíření .netmodule.</span><span class="sxs-lookup"><span data-stu-id="127e7-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="127e7-107">Soubor, který nemá manifest sestavení nelze načíst pomocí rozhraní .NET Framework common language runtime.</span><span class="sxs-lookup"><span data-stu-id="127e7-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="127e7-108">Však takový soubor může být součástí sestavení manifestu sestavení prostřednictvím [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="127e7-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="127e7-109">Pokud se v jedné kompilace vytvoří více než jeden modul [interní](../../../csharp/language-reference/keywords/internal.md) typy v jeden modul bude k dispozici pro ostatní moduly v sestavení.</span><span class="sxs-lookup"><span data-stu-id="127e7-109">If more than one module is created in a single compilation, [internal](../../../csharp/language-reference/keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="127e7-110">Pokud kód v odkazech na jeden modul `internal` typy v jiném modulu, pak oba moduly musí být začleněny do manifestu sestavení pomocí **- addmodule**.</span><span class="sxs-lookup"><span data-stu-id="127e7-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="127e7-111">Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="127e7-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="127e7-112">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="127e7-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="127e7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="127e7-113">Example</span></span>  
 <span data-ttu-id="127e7-114">Kompilace `in.cs`, vytváření `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="127e7-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="127e7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="127e7-115">See Also</span></span>  

- [<span data-ttu-id="127e7-116">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="127e7-116">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="127e7-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="127e7-117">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
