---
title: "-target: exe (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b66ab51b30e17ab2f34f88158c3f6095e185468d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="targetexe-c-compiler-options"></a><span data-ttu-id="a1196-102">/target:exe (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a1196-102">/target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="a1196-103">**/Target: exe** možnost způsobí, že kompilátor vytvořit spustitelný soubor (EXE), konzolová aplikace.</span><span class="sxs-lookup"><span data-stu-id="a1196-103">The **/target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1196-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1196-104">Syntax</span></span>  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1196-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1196-105">Remarks</span></span>  
 <span data-ttu-id="a1196-106">**/Target: exe** možnost ve výchozím nastavení je v platnosti.</span><span class="sxs-lookup"><span data-stu-id="a1196-106">The **/target:exe** option is in effect by default.</span></span> <span data-ttu-id="a1196-107">Vytvoří se spustitelný soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="a1196-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="a1196-108">Použití [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) pro vytvoření spustitelného souboru programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a1196-108">Use [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="a1196-109">Pokud není uvedeno jinak s [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název souboru vstupního souboru, který obsahuje [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="a1196-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="a1196-110">Pokud je zadán v příkazovém řádku, všechny soubory až do dalšího **/out** nebo **/target: Module** možnost slouží k vytvoření souboru .exe</span><span class="sxs-lookup"><span data-stu-id="a1196-110">When specified at the command line, all files up to the next **/out** or **/target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="a1196-111">Pouze jeden **hlavní** metoda je vyžadována v soubory zdrojového kódu, které jsou zkompilovány do souboru s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="a1196-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="a1196-112">[/Main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) – možnost kompilátoru umožňuje určit, která třída obsahuje **hlavní** metoda v případech, kdy váš kód obsahuje více než jednu třídu s **hlavní** metoda.</span><span class="sxs-lookup"><span data-stu-id="a1196-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a1196-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1196-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a1196-114">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="a1196-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="a1196-115">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="a1196-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="a1196-116">Změnit **výstupní typ** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a1196-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="a1196-117">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1196-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1196-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1196-118">Example</span></span>  
 <span data-ttu-id="a1196-119">Každý z následujících příkazových řádků zkompiluje `in.cs`, vytváření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="a1196-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1196-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1196-120">See Also</span></span>  
 [<span data-ttu-id="a1196-121">/ target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a1196-121">/target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="a1196-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="a1196-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
