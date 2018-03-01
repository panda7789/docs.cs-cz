---
title: "-target: library (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 242f8ada7cbffc4a6986339d28c4284b50afca25
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="4aed3-102">-target: library (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="4aed3-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="4aed3-103">**-Target: library** možnost způsobí, že kompilátor vytvoří dynamická knihovna (DLL) namísto spustitelného souboru (EXE).</span><span class="sxs-lookup"><span data-stu-id="4aed3-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aed3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aed3-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="4aed3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4aed3-105">Remarks</span></span>  
 <span data-ttu-id="4aed3-106">Knihovnu DLL, bude vytvořena s příponou .dll.</span><span class="sxs-lookup"><span data-stu-id="4aed3-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="4aed3-107">Pokud není uvedeno jinak s [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="4aed3-107">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="4aed3-108">Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **-out** nebo **-target: module** možnost slouží k vytvoření souboru .dll.</span><span class="sxs-lookup"><span data-stu-id="4aed3-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="4aed3-109">Při vytváření souboru .dll [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4aed3-109">When building a .dll file, a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4aed3-110">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4aed3-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4aed3-111">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="4aed3-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="4aed3-112">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="4aed3-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="4aed3-113">Změnit **výstupní typ** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4aed3-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="4aed3-114">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="4aed3-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aed3-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="4aed3-115">Example</span></span>  
 <span data-ttu-id="4aed3-116">Kompilace `in.cs`, vytváření `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="4aed3-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aed3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4aed3-117">See Also</span></span>  
 [<span data-ttu-id="4aed3-118">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="4aed3-118">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="4aed3-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4aed3-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
