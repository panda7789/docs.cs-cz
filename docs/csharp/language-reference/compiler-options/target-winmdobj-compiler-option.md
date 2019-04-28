---
title: -target:winmdobj (C# Compiler Options)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 9cc85bf582d737114bc0e621a9568bbb9acb791b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662384"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="921d4-102">-target:winmdobj (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="921d4-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="921d4-103">Pokud používáte **-target: winmdobj** – možnost kompilátoru, kompilátor vytvoří přechodný soubor .winmdobj, který lze převést do binárního souboru (.winmd) souboru Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="921d4-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="921d4-104">Soubor .winmd může být potom používán programy JavaScript a C++, kromě programů spravovaného jazyka.</span><span class="sxs-lookup"><span data-stu-id="921d4-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="921d4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="921d4-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="921d4-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="921d4-106">Remarks</span></span>  
 <span data-ttu-id="921d4-107">**Winmdobj** nastavení signály na kompilátoru, že přechodný modul je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="921d4-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="921d4-108">V reakci Visual Studio zkompiluje knihovnu tříd C# jako soubor .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="921d4-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="921d4-109">Soubor .winmdobj pak lze vkládat až <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru Windows metadata (.winmd).</span><span class="sxs-lookup"><span data-stu-id="921d4-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="921d4-110">Soubor .winmd obsahuje kód z původní knihovny i metadata WinMD, který se používá jazyk JavaScript nebo C++ a modulem Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="921d4-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="921d4-111">Výstupní soubor, který je zkompilován s použitím **-target: winmdobj** – možnost kompilátoru je určen k použití pouze jako vstup pro nástroj pro export WimMDExp; samotný soubor .winmdobj není přímo odkazován.</span><span class="sxs-lookup"><span data-stu-id="921d4-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="921d4-112">Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá názvu prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="921d4-112">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="921d4-113">A [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda není vyžadována.</span><span class="sxs-lookup"><span data-stu-id="921d4-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="921d4-114">Pokud zadáte možnost / target: winmdobj na příkazovém řádku, všechny soubory až do další **-out** nebo [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) slouží k vytvoření programu Windows.</span><span class="sxs-lookup"><span data-stu-id="921d4-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="921d4-115">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="921d4-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1. <span data-ttu-id="921d4-116">V **Průzkumníka řešení**, otevřete místní nabídku pro váš projekt a klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="921d4-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="921d4-117">Zvolte **aplikace** kartu.</span><span class="sxs-lookup"><span data-stu-id="921d4-117">Choose the **Application** tab.</span></span>  
  
3. <span data-ttu-id="921d4-118">V **typ výstupu** klikněte na položku **soubor WinMD**.</span><span class="sxs-lookup"><span data-stu-id="921d4-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="921d4-119">**Soubor WinMD** možnost je dostupná jenom pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikací.</span><span class="sxs-lookup"><span data-stu-id="921d4-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="921d4-120">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="921d4-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="921d4-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="921d4-121">Example</span></span>  
 <span data-ttu-id="921d4-122">Následující příkaz kompiluje `filename.cs` do přechodného souboru .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="921d4-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="921d4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="921d4-123">See also</span></span>

- [<span data-ttu-id="921d4-124">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="921d4-124">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="921d4-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="921d4-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
