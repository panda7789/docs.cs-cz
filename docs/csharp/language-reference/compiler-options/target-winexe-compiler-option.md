---
description: '-target: winexe (možnosti kompilátoru C#)'
title: '-target: winexe (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 8a1be07455b54b375106fef1fb480d7abd2f1ca4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124718"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="714de-103">-target: winexe (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="714de-103">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="714de-104">Možnost **-target: winexe** způsobí, že kompilátor vytvoří spustitelný soubor (exe), program systému Windows.</span><span class="sxs-lookup"><span data-stu-id="714de-104">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="714de-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="714de-105">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="714de-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="714de-106">Remarks</span></span>  
 <span data-ttu-id="714de-107">Spustitelný soubor se vytvoří s příponou. exe.</span><span class="sxs-lookup"><span data-stu-id="714de-107">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="714de-108">Program systému Windows je jeden, který poskytuje uživatelské rozhraní z knihovny .NET Framework nebo pomocí rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="714de-108">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="714de-109">Pro vytvoření konzolové aplikace použijte [příkaz-target: exe](./target-exe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="714de-109">Use [-target:exe](./target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="714de-110">Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru převezme název vstupního souboru, který obsahuje metodu [Main](../../programming-guide/main-and-command-args/index.md) .</span><span class="sxs-lookup"><span data-stu-id="714de-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="714de-111">Je-li parametr zadán na příkazovém řádku, všechny soubory, dokud není použita možnost Next **-out** nebo [-target](./target-compiler-option.md) pro vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="714de-111">When specified at the command line, all files until the next **-out** or [-target](./target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="714de-112">V souborech zdrojového kódu, které jsou zkompilovány do souboru. exe, je vyžadována jedna a pouze jedna metoda **Main** .</span><span class="sxs-lookup"><span data-stu-id="714de-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="714de-113">Možnost [-Main](./main-compiler-option.md) umožňuje určit, která třída obsahuje metodu **Main** , v případech, kdy váš kód má více než jednu třídu s metodou **Main** .</span><span class="sxs-lookup"><span data-stu-id="714de-113">The [-main](./main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="714de-114">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="714de-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="714de-115">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="714de-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="714de-116">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="714de-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="714de-117">Upravte vlastnost **Typ výstupu** .</span><span class="sxs-lookup"><span data-stu-id="714de-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="714de-118">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="714de-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="714de-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="714de-119">Example</span></span>  
 <span data-ttu-id="714de-120">Kompilovat `in.cs` do programu systému Windows:</span><span class="sxs-lookup"><span data-stu-id="714de-120">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="714de-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="714de-121">See also</span></span>

- [<span data-ttu-id="714de-122">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="714de-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="714de-123">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="714de-123">C# Compiler Options</span></span>](./index.md)
