---
title: "-target: winexe (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b13af4e665a2bf5a75472bc8f4a501e90c59281a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="9a6d9-102">-target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="9a6d9-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="9a6d9-103">**-Target: winexe** možnost způsobí, že kompilátor vytvoří spustitelný soubor (EXE), programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a6d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a6d9-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a6d9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a6d9-105">Remarks</span></span>  
 <span data-ttu-id="9a6d9-106">Vytvoří se spustitelný soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="9a6d9-107">Windows program je ten, který poskytuje uživatelské rozhraní z knihovny rozhraní .NET Framework nebo s rozhraními API Win32.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="9a6d9-108">Použití [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="9a6d9-109">Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="9a6d9-110">Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možnost slouží k vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="9a6d9-111">Pouze jeden **hlavní** metoda je vyžadována v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="9a6d9-112">[– Hlavní](../../../csharp/language-reference/compiler-options/main-compiler-option.md) možnost umožňuje zadat, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje více než jednu třídu s **hlavní** metoda.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9a6d9-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a6d9-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="9a6d9-114">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="9a6d9-115">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="9a6d9-116">Změnit **výstupní typ** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="9a6d9-117">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a6d9-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a6d9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a6d9-118">Example</span></span>  
 <span data-ttu-id="9a6d9-119">Kompilace `in.cs` do programu systému Windows:</span><span class="sxs-lookup"><span data-stu-id="9a6d9-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a6d9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a6d9-120">See Also</span></span>  
 [<span data-ttu-id="9a6d9-121">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="9a6d9-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="9a6d9-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a6d9-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
