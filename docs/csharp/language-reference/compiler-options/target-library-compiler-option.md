---
title: -target:library (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606390"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="70a8b-102">-target:library (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="70a8b-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="70a8b-103">Možnost **-target:library** způsobí, že kompilátor vytvoří knihovnu dynamických vazeb (DLL) spíše než spustitelný soubor (EXE).</span><span class="sxs-lookup"><span data-stu-id="70a8b-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70a8b-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="70a8b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70a8b-105">Remarks</span></span>  
 <span data-ttu-id="70a8b-106">DLL bude vytvořena s rozšířením .dll.</span><span class="sxs-lookup"><span data-stu-id="70a8b-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="70a8b-107">Pokud není u možnosti [-out](./out-compiler-option.md) uvedeno jinak, název výstupního souboru převezme název prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="70a8b-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="70a8b-108">Pokud je zadán na příkazovém řádku, všechny soubory až do další **-out** nebo **-target:module** možnost se používají k vytvoření souboru DLL.</span><span class="sxs-lookup"><span data-stu-id="70a8b-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="70a8b-109">Při vytváření souboru DLL není vyžadována metoda [Main.](../../programming-guide/main-and-command-args/index.md)</span><span class="sxs-lookup"><span data-stu-id="70a8b-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="70a8b-110">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="70a8b-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="70a8b-111">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="70a8b-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="70a8b-112">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="70a8b-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="70a8b-113">Upravte vlastnost **Output type.**</span><span class="sxs-lookup"><span data-stu-id="70a8b-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="70a8b-114">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="70a8b-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70a8b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="70a8b-115">Example</span></span>  
 <span data-ttu-id="70a8b-116">Kompilace `in.cs` `in.dll`, vytváření :</span><span class="sxs-lookup"><span data-stu-id="70a8b-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="70a8b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="70a8b-117">See also</span></span>

- [<span data-ttu-id="70a8b-118">-target (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="70a8b-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="70a8b-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70a8b-119">C# Compiler Options</span></span>](./index.md)
