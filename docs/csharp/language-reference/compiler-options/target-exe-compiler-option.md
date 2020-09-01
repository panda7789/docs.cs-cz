---
description: '-target: exe (možnosti kompilátoru C#)'
title: '-target: exe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 3cea52fe872fcb407206ee2063b93dc81447a3b2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128501"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="a271d-103">-target: exe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a271d-103">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="a271d-104">Možnost **-target: exe** způsobí, že kompilátor vytvoří spustitelný soubor (exe), konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a271d-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a271d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a271d-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="a271d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a271d-106">Remarks</span></span>  
 <span data-ttu-id="a271d-107">Možnost **-target: exe** je ve výchozím nastavení platná.</span><span class="sxs-lookup"><span data-stu-id="a271d-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="a271d-108">Spustitelný soubor se vytvoří s příponou. exe.</span><span class="sxs-lookup"><span data-stu-id="a271d-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="a271d-109">Použití [-target: winexe](./target-winexe-compiler-option.md) k vytvoření spustitelného souboru programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a271d-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="a271d-110">Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru převezme název vstupního souboru, který obsahuje metodu [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="a271d-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="a271d-111">Při zadání na příkazovém řádku se pro vytvoření souboru. exe použijí všechny soubory až **na další nebo** na **cíl: možnost modul** .</span><span class="sxs-lookup"><span data-stu-id="a271d-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="a271d-112">V souborech zdrojového kódu, které jsou zkompilovány do souboru. exe, je vyžadována jedna a pouze jedna metoda **Main** .</span><span class="sxs-lookup"><span data-stu-id="a271d-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="a271d-113">Možnost [-Main](./main-compiler-option.md) kompilátoru umožňuje určit, která třída obsahuje metodu **Main** , v případech, kdy váš kód má více než jednu třídu s metodou **Main** .</span><span class="sxs-lookup"><span data-stu-id="a271d-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a271d-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a271d-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a271d-115">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="a271d-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a271d-116">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="a271d-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="a271d-117">Upravte vlastnost **Typ výstupu** .</span><span class="sxs-lookup"><span data-stu-id="a271d-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="a271d-118">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="a271d-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a271d-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="a271d-119">Example</span></span>  
 <span data-ttu-id="a271d-120">Každý z následujících příkazových řádků bude zkompilován `in.cs` , vytváření `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="a271d-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a271d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="a271d-121">See also</span></span>

- [<span data-ttu-id="a271d-122">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="a271d-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="a271d-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="a271d-123">C# Compiler Options</span></span>](./index.md)
