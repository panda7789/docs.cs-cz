---
title: -target:exe (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 7d34a25fd614a209761714e1f4eff3042ca240c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331309"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="422d5-102">-target:exe (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="422d5-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="422d5-103">**-Target: exe** možnost způsobí, že kompilátor vytvoří spustitelný soubor (EXE) konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="422d5-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="422d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="422d5-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="422d5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="422d5-105">Remarks</span></span>  
 <span data-ttu-id="422d5-106">**-Target: exe** možnost je v platnosti ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="422d5-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="422d5-107">Vytvoří se spustitelný soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="422d5-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="422d5-108">Použití [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) k vytvoření spustitelného programu Windows.</span><span class="sxs-lookup"><span data-stu-id="422d5-108">Use [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="422d5-109">Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) – metoda.</span><span class="sxs-lookup"><span data-stu-id="422d5-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="422d5-110">Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo **-target: module** slouží k vytvoření souboru .exe</span><span class="sxs-lookup"><span data-stu-id="422d5-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="422d5-111">Pouze jeden **hlavní** metoda je vyžadována v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="422d5-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="422d5-112">[– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) – možnost kompilátoru umožňuje určit, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje víc než jedna třída s **hlavní** metoda.</span><span class="sxs-lookup"><span data-stu-id="422d5-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="422d5-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="422d5-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="422d5-114">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="422d5-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="422d5-115">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="422d5-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="422d5-116">Upravit **typ výstupu** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="422d5-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="422d5-117">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="422d5-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="422d5-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="422d5-118">Example</span></span>  
 <span data-ttu-id="422d5-119">Každý z následujících příkazových řádků zkompiluje `in.cs`, vytváření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="422d5-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="422d5-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="422d5-120">See also</span></span>

- [<span data-ttu-id="422d5-121">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="422d5-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="422d5-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="422d5-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
