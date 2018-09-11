---
title: '-target: winexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: f77137e3cc2f734435d3b1d391a303fcd3e16332
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44273317"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="e668f-102">-target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="e668f-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="e668f-103">**-Target: winexe** možnost způsobí, že kompilátor vytvoří spustitelný soubor (EXE), Windows program.</span><span class="sxs-lookup"><span data-stu-id="e668f-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e668f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e668f-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="e668f-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e668f-105">Remarks</span></span>  
 <span data-ttu-id="e668f-106">Vytvoří se spustitelný soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="e668f-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="e668f-107">Windows program je ten, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo pomocí rozhraní API systému Win32.</span><span class="sxs-lookup"><span data-stu-id="e668f-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="e668f-108">Použití [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="e668f-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="e668f-109">Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru přebírá název vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) – metoda.</span><span class="sxs-lookup"><span data-stu-id="e668f-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="e668f-110">Pokud je zadán v příkazovém řádku, všechny soubory až do další **-out** nebo [– cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) slouží k vytvoření programu Windows.</span><span class="sxs-lookup"><span data-stu-id="e668f-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="e668f-111">Pouze jeden **hlavní** metoda je vyžadována v souborech zdrojového kódu, které jsou kompilovány do souboru s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="e668f-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="e668f-112">[– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) možnost umožňuje zadat, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje víc než jedna třída s **hlavní** – metoda.</span><span class="sxs-lookup"><span data-stu-id="e668f-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e668f-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e668f-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e668f-114">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="e668f-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="e668f-115">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="e668f-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="e668f-116">Upravit **typ výstupu** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e668f-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="e668f-117">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="e668f-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e668f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e668f-118">Example</span></span>  
 <span data-ttu-id="e668f-119">Kompilace `in.cs` do aplikace Windows:</span><span class="sxs-lookup"><span data-stu-id="e668f-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e668f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e668f-120">See Also</span></span>  

- [<span data-ttu-id="e668f-121">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="e668f-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [<span data-ttu-id="e668f-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e668f-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
