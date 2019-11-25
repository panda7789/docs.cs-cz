---
title: -target:winmdobj (C# Compiler Options)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204495"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="0cead-102">-target:winmdobj (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="0cead-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="0cead-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span><span class="sxs-lookup"><span data-stu-id="0cead-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="0cead-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span><span class="sxs-lookup"><span data-stu-id="0cead-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cead-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cead-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="0cead-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cead-106">Remarks</span></span>  
 <span data-ttu-id="0cead-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span><span class="sxs-lookup"><span data-stu-id="0cead-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="0cead-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span><span class="sxs-lookup"><span data-stu-id="0cead-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="0cead-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span><span class="sxs-lookup"><span data-stu-id="0cead-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="0cead-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="0cead-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="0cead-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span><span class="sxs-lookup"><span data-stu-id="0cead-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="0cead-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span><span class="sxs-lookup"><span data-stu-id="0cead-112">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="0cead-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span><span class="sxs-lookup"><span data-stu-id="0cead-113">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="0cead-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span><span class="sxs-lookup"><span data-stu-id="0cead-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="0cead-115">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="0cead-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="0cead-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span><span class="sxs-lookup"><span data-stu-id="0cead-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="0cead-117">Choose the **Application** tab.</span><span class="sxs-lookup"><span data-stu-id="0cead-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="0cead-118">In the **Output type** list, choose **WinMD File**.</span><span class="sxs-lookup"><span data-stu-id="0cead-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="0cead-119">The **WinMD File** option is available only for Windows 8.x Store app templates.</span><span class="sxs-lookup"><span data-stu-id="0cead-119">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="0cead-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cead-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cead-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cead-121">Example</span></span>  
 <span data-ttu-id="0cead-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span><span class="sxs-lookup"><span data-stu-id="0cead-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cead-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cead-123">See also</span></span>

- [<span data-ttu-id="0cead-124">-target (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="0cead-124">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="0cead-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0cead-125">C# Compiler Options</span></span>](./index.md)
