---
description: '-target: Module (možnosti kompilátoru C#)'
title: '-target: Module (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: 2c592d2fe001bb0908a06a6eb3287a39040b8715
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128449"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="20c75-103">-target: Module (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="20c75-103">-target:module (C# Compiler Options)</span></span>
<span data-ttu-id="20c75-104">Tato možnost způsobí, že kompilátor negeneruje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="20c75-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c75-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="20c75-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="20c75-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20c75-106">Remarks</span></span>  
 <span data-ttu-id="20c75-107">Ve výchozím nastavení bude mít výstupní soubor vytvořený kompilací s touto možností rozšíření. netmodule.</span><span class="sxs-lookup"><span data-stu-id="20c75-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="20c75-108">Soubor, který nemá manifest sestavení, nelze načíst pomocí .NET Framework modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="20c75-108">A file that does not have an assembly manifest cannot be loaded by the .NET Framework common language runtime.</span></span> <span data-ttu-id="20c75-109">Takový soubor však lze začlenit do manifestu sestavení sestavení pomocí [addmodule –](./addmodule-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="20c75-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="20c75-110">Je-li v jedné kompilaci vytvořen více než jeden modul, [interní](../keywords/internal.md) typy v jednom modulu budou k dispozici pro ostatní moduly v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="20c75-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="20c75-111">V případě, že kód v jednom modulu odkazuje na `internal` typy v jiném modulu, musí být oba moduly začleněny do manifestu sestavení, a to pomocí **-addmodule –**.</span><span class="sxs-lookup"><span data-stu-id="20c75-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="20c75-112">Vytvoření modulu není podporováno ve vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20c75-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="20c75-113">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="20c75-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20c75-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="20c75-114">Example</span></span>  
 <span data-ttu-id="20c75-115">Kompilovat `in.cs` , vytvořit `in.netmodule` :</span><span class="sxs-lookup"><span data-stu-id="20c75-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="20c75-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="20c75-116">See also</span></span>

- [<span data-ttu-id="20c75-117">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="20c75-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="20c75-118">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="20c75-118">C# Compiler Options</span></span>](./index.md)
