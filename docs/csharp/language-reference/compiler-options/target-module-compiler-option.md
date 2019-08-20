---
title: -target:module (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 25421df2e9306071ce3506aaf7affd1b259d1c32
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602438"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="52504-102">-target:module (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="52504-102">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="52504-103">Tato možnost způsobí, že kompilátor negeneruje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="52504-103">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52504-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52504-104">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="52504-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52504-105">Remarks</span></span>  
 <span data-ttu-id="52504-106">Ve výchozím nastavení bude mít výstupní soubor vytvořený kompilací s touto možností rozšíření. netmodule.</span><span class="sxs-lookup"><span data-stu-id="52504-106">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="52504-107">Soubor, který nemá manifest sestavení, nelze načíst pomocí .NET Framework modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="52504-107">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="52504-108">Takový soubor však lze začlenit do manifestu sestavení sestavení pomocí [addmodule –](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="52504-108">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="52504-109">Je-li v jedné kompilaci vytvořen více než jeden modul, [interní](../keywords/internal.md) typy v jednom modulu budou k dispozici pro ostatní moduly v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="52504-109">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="52504-110">V případě, že kód v `internal` jednom modulu odkazuje na typy v jiném modulu, musí být oba moduly začleněny do manifestu sestavení, a to pomocí **-addmodule –** .</span><span class="sxs-lookup"><span data-stu-id="52504-110">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="52504-111">Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52504-111">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="52504-112">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.OutputType%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="52504-112">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52504-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="52504-113">Example</span></span>  
 <span data-ttu-id="52504-114">Kompilovat `in.cs`, vytvořit `in.netmodule`:</span><span class="sxs-lookup"><span data-stu-id="52504-114">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="52504-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52504-115">See also</span></span>

- [<span data-ttu-id="52504-116">-Target (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="52504-116">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="52504-117">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="52504-117">C# Compiler Options</span></span>](./index.md)
