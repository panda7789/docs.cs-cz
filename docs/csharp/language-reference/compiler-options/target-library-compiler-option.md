---
title: '-target: Library (C# možnosti kompilátoru)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606390"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="a525b-102">-target: Library (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="a525b-102">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="a525b-103">Možnost **-target: Library** způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL) místo spustitelného souboru (exe).</span><span class="sxs-lookup"><span data-stu-id="a525b-103">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a525b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a525b-104">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="a525b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a525b-105">Remarks</span></span>  
 <span data-ttu-id="a525b-106">Knihovna DLL bude vytvořena s příponou. dll.</span><span class="sxs-lookup"><span data-stu-id="a525b-106">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="a525b-107">Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru vezme název prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="a525b-107">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="a525b-108">Při zadání na příkazovém řádku všechny soubory až do možnosti další **-mimo** **cíl: modul** slouží k vytvoření souboru. dll.</span><span class="sxs-lookup"><span data-stu-id="a525b-108">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="a525b-109">Při sestavování souboru. dll není metoda [Main](../../programming-guide/main-and-command-args/index.md) nutná.</span><span class="sxs-lookup"><span data-stu-id="a525b-109">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a525b-110">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a525b-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="a525b-111">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="a525b-111">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="a525b-112">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="a525b-112">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="a525b-113">Upravte vlastnost **Typ výstupu** .</span><span class="sxs-lookup"><span data-stu-id="a525b-113">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="a525b-114">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.OutputType%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="a525b-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a525b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a525b-115">Example</span></span>  
 <span data-ttu-id="a525b-116">Kompilovat `in.cs`, vytvořit `in.dll`:</span><span class="sxs-lookup"><span data-stu-id="a525b-116">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="a525b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a525b-117">See also</span></span>

- [<span data-ttu-id="a525b-118">-Target (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="a525b-118">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="a525b-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a525b-119">C# Compiler Options</span></span>](./index.md)
