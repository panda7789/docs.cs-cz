---
title: '-target: winmdobj (možnosti kompilátoru C#)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: b0b1ec0bed174484e9ed7b9ecddbe82b0c705325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218655"
---
# <a name="-targetwinmdobj-c-compiler-options"></a><span data-ttu-id="c91b6-102">-target: winmdobj (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c91b6-102">-target:winmdobj (C# Compiler Options)</span></span>
<span data-ttu-id="c91b6-103">Pokud použijete **-target: winmdobj** – možnost kompilátoru, kompilátor vytvoří zprostředkující .winmdobj soubor, který můžete převést do prostředí Windows Runtime binárního souboru (.winmd) souboru.</span><span class="sxs-lookup"><span data-stu-id="c91b6-103">If you use the **-target:winmdobj** compiler option, the compiler creates an intermediate .winmdobj file that you can convert to a Windows Runtime binary (.winmd) file.</span></span> <span data-ttu-id="c91b6-104">Soubor .winmd mohou být spotřebovávána pak JavaScript a C++ programy, kromě spravované jazyk programy.</span><span class="sxs-lookup"><span data-stu-id="c91b6-104">The .winmd file can then be consumed by JavaScript and C++ programs, in addition to managed language programs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c91b6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c91b6-105">Syntax</span></span>  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a><span data-ttu-id="c91b6-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c91b6-106">Remarks</span></span>  
 <span data-ttu-id="c91b6-107">**Winmdobj** nastavení signály pro kompilátor, že modul zprostředkující je vyžadována.</span><span class="sxs-lookup"><span data-stu-id="c91b6-107">The **winmdobj** setting signals to the compiler that an intermediate module is required.</span></span> <span data-ttu-id="c91b6-108">Visual Studio v odpovědi, zkompiluje jako soubor .winmdobj knihovny tříd jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="c91b6-108">In response, Visual Studio compiles the C# class library as a .winmdobj file.</span></span> <span data-ttu-id="c91b6-109">Soubor .winmdobj můžete pak dodáni prostřednictvím <xref:Microsoft.Build.Tasks.WinMDExp> exportovat nástroj k vytvoření souboru metadat (.winmd) systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c91b6-109">The .winmdobj file can then be fed through the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (.winmd) file.</span></span> <span data-ttu-id="c91b6-110">Soubor .winmd obsahuje kód z původní knihovna a WinMD metadata, která se používá JavaScript nebo C++ a prostředí Windows Runtime.</span><span class="sxs-lookup"><span data-stu-id="c91b6-110">The .winmd file contains both the code from the original library and the WinMD metadata that is used by JavaScript or C++ and by the Windows Runtime.</span></span>  
  
 <span data-ttu-id="c91b6-111">Výstup tohoto souboru, který se zkompiluje pomocí **-target: winmdobj** – možnost kompilátoru je určen k použití pouze jako vstup pro nástroj pro export WimMDExp; samotný soubor .winmdobj neodkazuje přímo.</span><span class="sxs-lookup"><span data-stu-id="c91b6-111">The output of a file that’s compiled by using the **-target:winmdobj** compiler option is designed to be used only as input for the WimMDExp export tool; the .winmdobj file itself isn’t referenced directly.</span></span>  
  
 <span data-ttu-id="c91b6-112">Pokud nechcete použít [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) možnost, název výstupního souboru využívá název prvního vstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="c91b6-112">Unless you use the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the first input file.</span></span> <span data-ttu-id="c91b6-113">A [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metoda není povinné.</span><span class="sxs-lookup"><span data-stu-id="c91b6-113">A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method isn’t required.</span></span>  
  
 <span data-ttu-id="c91b6-114">Pokud zadáte-target: winmdobj možnost příkazového řádku, všechny soubory, dokud Další **-out** nebo [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) možnost slouží k vytvoření programu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c91b6-114">If you specify the -target:winmdobj option at a command prompt, all files until the next **-out** or [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) option are used to create the Windows program.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a><span data-ttu-id="c91b6-115">Nastavení této možnosti kompilátoru v integrovaném vývojovém prostředí sady Visual Studio pro aplikaci pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="c91b6-115">To set this compiler option in the Visual Studio IDE for a Windows Store app</span></span>  
  
1.  <span data-ttu-id="c91b6-116">V **Průzkumníku řešení**, otevřete místní nabídku pro svůj projekt a potom zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c91b6-116">In **Solution Explorer**, open the shortcut menu for your project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="c91b6-117">Vyberte **aplikace** kartě.</span><span class="sxs-lookup"><span data-stu-id="c91b6-117">Choose the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="c91b6-118">V **výstupní typ** vyberte **souboru WinMD**.</span><span class="sxs-lookup"><span data-stu-id="c91b6-118">In the **Output type** list, choose **WinMD File**.</span></span>  
  
     <span data-ttu-id="c91b6-119">**Souboru WinMD** možnost je dostupná pouze pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] šablony aplikace.</span><span class="sxs-lookup"><span data-stu-id="c91b6-119">The **WinMD File** option is available only for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] app templates.</span></span>  
  
 <span data-ttu-id="c91b6-120">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="c91b6-120">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c91b6-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c91b6-121">Example</span></span>  
 <span data-ttu-id="c91b6-122">Následující příkaz zkompiluje `filename.cs` do souboru zprostředkující .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="c91b6-122">The following command compiles `filename.cs` into an intermediate .winmdobj file.</span></span>  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c91b6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c91b6-123">See Also</span></span>  
 [<span data-ttu-id="c91b6-124">-target (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c91b6-124">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [<span data-ttu-id="c91b6-125">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c91b6-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
