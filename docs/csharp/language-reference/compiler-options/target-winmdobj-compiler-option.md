---
description: '-target: winmdobj (možnosti kompilátoru C#)'
title: '-target: winmdobj (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 66a4bddb34832705ad4779829e561afd9442be8f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139083"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="d2b76-103">-target: winmdobj (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d2b76-103">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="d2b76-104">Použijete-li možnost kompilátoru **-target: winmdobj** , kompilátor vytvoří zprostředkující soubor. winmdobj, který lze převést na soubor prostředí Windows Runtime binárního souboru (. winmd).</span><span class="sxs-lookup"><span data-stu-id="d2b76-104">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="d2b76-105">Soubor. winmd pak může používat programy JavaScript a C++ kromě spravovaných jazykových programů.</span><span class="sxs-lookup"><span data-stu-id="d2b76-105">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2b76-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2b76-106">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="d2b76-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2b76-107">Remarks</span></span>  
 <span data-ttu-id="d2b76-108">Nastavení **winmdobj** signalizuje kompilátoru, že je vyžadován zprostředkující modul.</span><span class="sxs-lookup"><span data-stu-id="d2b76-108">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="d2b76-109">V reakci Visual Studio zkompiluje knihovnu tříd C# jako soubor. winmdobj.</span><span class="sxs-lookup"><span data-stu-id="d2b76-109">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="d2b76-110">Soubor. winmdobj lze následně dodávat prostřednictvím <xref:Microsoft.Build.Tasks.WinMDExp> Nástroje pro export a vytvořit tak soubor metadat Windows (. winmd).</span><span class="sxs-lookup"><span data-stu-id="d2b76-110">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="d2b76-111">Soubor. winmd obsahuje kód z původní knihovny i metadata WinMD, která jsou používána v jazyce JavaScript nebo C++ a prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="d2b76-111">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="d2b76-112">Výstup souboru, který je zkompilován pomocí volby kompilátoru **-target: winmdobj** , je navržen tak, aby se pro nástroj pro export WimMDExp používal jenom jako vstup. na samotný soubor. winmdobj se neodkazuje přímo.</span><span class="sxs-lookup"><span data-stu-id="d2b76-112">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="d2b76-113">Pokud nepoužijete možnost [-out](./out-compiler-option.md) , název výstupního souboru vezme název prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="d2b76-113">Unless you use the [-out](./out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="d2b76-114">Metoda [Main](../../programming-guide/main-and-command-args/index.md) se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="d2b76-114">A [Main](../../programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="d2b76-115">Zadáte-li možnost-target: winmdobj na příkazovém řádku, budou pro vytvoření programu systému Windows použity všechny soubory, dokud nebude použita možnost Další **-mimo** [cíl: modul](./target-module-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="d2b76-115">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](./target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="d2b76-116">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="d2b76-116">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="d2b76-117">V **Průzkumník řešení**otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d2b76-117">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="d2b76-118">Vyberte kartu **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="d2b76-118">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="d2b76-119">V seznamu **Typ výstupu** vyberte **soubor winmd**.</span><span class="sxs-lookup"><span data-stu-id="d2b76-119">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="d2b76-120">Možnost **soubor winmd** je k dispozici pouze pro šablony aplikací Windows 8. x Store.</span><span class="sxs-lookup"><span data-stu-id="d2b76-120">The **WinMD File** option is available only for Windows 8.x Store app templates.</span></span>  
  
 <span data-ttu-id="d2b76-121">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A> .</span><span class="sxs-lookup"><span data-stu-id="d2b76-121">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2b76-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2b76-122">Example</span></span>  
 <span data-ttu-id="d2b76-123">Následující příkaz se zkompiluje `filename.cs` do zprostředkujícího souboru. winmdobj.</span><span class="sxs-lookup"><span data-stu-id="d2b76-123">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d2b76-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2b76-124">See also</span></span>

- [<span data-ttu-id="d2b76-125">-Target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d2b76-125">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="d2b76-126">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="d2b76-126">C# Compiler Options</span></span>](./index.md)
