---
title: -target:exe (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606464"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="ff96b-102">-target:exe (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ff96b-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="ff96b-103">Možnost **-target:exe** způsobí, že kompilátor vytvoří spustitelný soubor (EXE), konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ff96b-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff96b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff96b-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="ff96b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff96b-105">Remarks</span></span>  
 <span data-ttu-id="ff96b-106">Možnost **-target:exe** je ve výchozím nastavení účinná.</span><span class="sxs-lookup"><span data-stu-id="ff96b-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="ff96b-107">Spustitelný soubor bude vytvořen s příponou EXE.</span><span class="sxs-lookup"><span data-stu-id="ff96b-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="ff96b-108">Použijte [-target:winexe](./target-winexe-compiler-option.md) k vytvoření spustitelného souboru programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ff96b-108">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="ff96b-109">Pokud není uvedeno jinak s volbou [-out,](./out-compiler-option.md) název výstupního souboru přebírá název vstupního souboru, který obsahuje [metodu Main.](../../programming-guide/main-and-command-args/index.md)</span><span class="sxs-lookup"><span data-stu-id="ff96b-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="ff96b-110">Pokud jsou zadány na příkazovém řádku, všechny soubory až do další **volby -out** nebo **-target:module** se používají k vytvoření souboru EXE</span><span class="sxs-lookup"><span data-stu-id="ff96b-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="ff96b-111">V souborech zdrojového kódu, které jsou zkompilovány do souboru EXE, je vyžadována jedna metoda **Main.**</span><span class="sxs-lookup"><span data-stu-id="ff96b-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="ff96b-112">[-main](./main-compiler-option.md) kompilátor možnost umožňuje určit, která třída obsahuje **Main** metoda, v případech, kdy váš kód má více než jednu třídu s **Main** metoda.</span><span class="sxs-lookup"><span data-stu-id="ff96b-112">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ff96b-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ff96b-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ff96b-114">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="ff96b-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ff96b-115">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="ff96b-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="ff96b-116">Upravte vlastnost **Output type.**</span><span class="sxs-lookup"><span data-stu-id="ff96b-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="ff96b-117">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="ff96b-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff96b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff96b-118">Example</span></span>  
 <span data-ttu-id="ff96b-119">Každý z následujících příkazových řádků se zkompiluje `in.cs`a vytvoří `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="ff96b-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff96b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff96b-120">See also</span></span>

- [<span data-ttu-id="ff96b-121">-target (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ff96b-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="ff96b-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff96b-122">C# Compiler Options</span></span>](./index.md)
