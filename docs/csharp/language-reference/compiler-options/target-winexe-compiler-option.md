---
title: -target:winexe (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606379"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="d28d4-102">-target:winexe (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d28d4-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="d28d4-103">Možnost **-target:winexe** způsobí, že kompilátor vytvoří spustitelný soubor (EXE), program systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d28d4-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d28d4-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d28d4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d28d4-105">Remarks</span></span>  
 <span data-ttu-id="d28d4-106">Spustitelný soubor bude vytvořen s příponou EXE.</span><span class="sxs-lookup"><span data-stu-id="d28d4-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="d28d4-107">Program systému Windows je program, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo s rozhraními API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d28d4-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="d28d4-108">Použijte [-target:exe](./target-exe-compiler-option.md) k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="d28d4-108">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="d28d4-109">Pokud není uvedeno jinak s volbou [-out,](./out-compiler-option.md) název výstupního souboru přebírá název vstupního souboru, který obsahuje [metodu Main.](../../programming-guide/main-and-command-args/index.md)</span><span class="sxs-lookup"><span data-stu-id="d28d4-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="d28d4-110">Pokud jsou zadány na příkazovém řádku, všechny soubory až do další **-out** nebo [-target](./target-compiler-option.md) možnost jsou použity k vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d28d4-110">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="d28d4-111">V souborech zdrojového kódu, které jsou zkompilovány do souboru EXE, je vyžadována jedna metoda **Main.**</span><span class="sxs-lookup"><span data-stu-id="d28d4-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="d28d4-112">[-main](./main-compiler-option.md) Možnost umožňuje určit, která třída obsahuje **Main** metoda, v případech, kdy váš kód má více než jednu třídu s **Main** metoda.</span><span class="sxs-lookup"><span data-stu-id="d28d4-112">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d28d4-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d28d4-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d28d4-114">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="d28d4-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d28d4-115">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="d28d4-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="d28d4-116">Upravte vlastnost **Output type.**</span><span class="sxs-lookup"><span data-stu-id="d28d4-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="d28d4-117">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="d28d4-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d28d4-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d28d4-118">Example</span></span>  
 <span data-ttu-id="d28d4-119">Kompilace `in.cs` do programu systému Windows:</span><span class="sxs-lookup"><span data-stu-id="d28d4-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d28d4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d28d4-120">See also</span></span>

- [<span data-ttu-id="d28d4-121">-target (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d28d4-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="d28d4-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d28d4-122">C# Compiler Options</span></span>](./index.md)
