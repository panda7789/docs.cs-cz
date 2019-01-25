---
title: '-target: library (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0bdf8d95004ca11e3d6b9b27568f7310a802a28b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542441"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="726b7-102">-target: library (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="726b7-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="726b7-103">**-Target: library** možnost způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL) místo spustitelný soubor (EXE).</span><span class="sxs-lookup"><span data-stu-id="726b7-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="726b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="726b7-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="726b7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="726b7-105">Remarks</span></span>  
 <span data-ttu-id="726b7-106">Vytvoří se knihovna DLL s příponou .dll.</span><span class="sxs-lookup"><span data-stu-id="726b7-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="726b7-107">Pokud není stanoveno jinak pomocí [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá názvu prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="726b7-107">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="726b7-108">Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo **-target: module** slouží k vytvoření souboru .dll.</span><span class="sxs-lookup"><span data-stu-id="726b7-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="726b7-109">Při vytváření souboru .dll [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="726b7-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="726b7-110">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="726b7-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="726b7-111">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="726b7-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="726b7-112">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="726b7-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="726b7-113">Upravit **typ výstupu** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="726b7-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="726b7-114">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="726b7-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="726b7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="726b7-115">Example</span></span>  
 <span data-ttu-id="726b7-116">Kompilace `in.cs`, vytváření `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="726b7-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="726b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="726b7-117">See also</span></span>

- [<span data-ttu-id="726b7-118">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="726b7-118">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="726b7-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="726b7-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
