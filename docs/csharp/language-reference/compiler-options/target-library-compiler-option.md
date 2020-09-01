---
description: '-target: Library (možnosti kompilátoru C#)'
title: '-target: Library (možnosti kompilátoru C#)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 953249c4d0168ed3d279d03a0b2fb63d8ff6d5f5
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128475"
---
# <a name="-targetlibrary-c-compiler-options"></a><span data-ttu-id="44646-103">-target: Library (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="44646-103">-target:library (C# Compiler Options)</span></span>
<span data-ttu-id="44646-104">Možnost **-target: Library** způsobí, že kompilátor vytvoří dynamickou knihovnu (DLL) místo spustitelného souboru (exe).</span><span class="sxs-lookup"><span data-stu-id="44646-104">The **-target:library** option causes the compiler to create a dynamic-link library (DLL) rather than an executable file (EXE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44646-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44646-105">Syntax</span></span>  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a><span data-ttu-id="44646-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44646-106">Remarks</span></span>  
 <span data-ttu-id="44646-107">Knihovna DLL bude vytvořena s příponou. dll.</span><span class="sxs-lookup"><span data-stu-id="44646-107">The DLL will be created with the .dll extension.</span></span>  
  
 <span data-ttu-id="44646-108">Pokud není uvedeno jinak s možností [-out](./out-compiler-option.md) , název výstupního souboru vezme název prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="44646-108">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span>  
  
 <span data-ttu-id="44646-109">Při zadání na příkazovém řádku všechny soubory až do možnosti další **-mimo** **cíl: modul** slouží k vytvoření souboru. dll.</span><span class="sxs-lookup"><span data-stu-id="44646-109">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .dll file.</span></span>  
  
 <span data-ttu-id="44646-110">Při sestavování souboru. dll není metoda [Main](../../programming-guide/main-and-command-args/index.md) nutná.</span><span class="sxs-lookup"><span data-stu-id="44646-110">When building a .dll file, a [Main](../../programming-guide/main-and-command-args/index.md) method is not required.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="44646-111">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="44646-111">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="44646-112">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="44646-112">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="44646-113">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="44646-113">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="44646-114">Upravte vlastnost **Typ výstupu** .</span><span class="sxs-lookup"><span data-stu-id="44646-114">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="44646-115">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="44646-115">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44646-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="44646-116">Example</span></span>  
 <span data-ttu-id="44646-117">Kompilovat `in.cs` , vytvořit `in.dll` :</span><span class="sxs-lookup"><span data-stu-id="44646-117">Compile `in.cs`, creating `in.dll`:</span></span>  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="44646-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="44646-118">See also</span></span>

- [<span data-ttu-id="44646-119">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="44646-119">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="44646-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="44646-120">C# Compiler Options</span></span>](./index.md)
