---
description: -win32icon (možnosti kompilátoru C#)
title: -win32icon (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 76a54f9011371492bdc15f15c3e40d51082deed3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138407"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="5146b-103">-win32icon (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="5146b-103">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="5146b-104">Možnost **-win32icon** vloží soubor. ico do výstupního souboru, který poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="5146b-104">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5146b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5146b-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="5146b-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5146b-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="5146b-107">Soubor. ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="5146b-107">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5146b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5146b-108">Remarks</span></span>  
 <span data-ttu-id="5146b-109">Soubor. ico se dá vytvořit s [kompilátorem prostředků](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="5146b-109">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="5146b-110">Kompilátor prostředků je vyvolán při kompilování Visual C++ programu; soubor. ico je vytvořen ze souboru. rc.</span><span class="sxs-lookup"><span data-stu-id="5146b-110">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="5146b-111">Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="5146b-111">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="5146b-112">Viz [-win32res](./win32res-compiler-option.md) pro import souboru. res.</span><span class="sxs-lookup"><span data-stu-id="5146b-112">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5146b-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5146b-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5146b-114">Otevřete stránky **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="5146b-114">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="5146b-115">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="5146b-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="5146b-116">Upravte vlastnost **ikona aplikace** .</span><span class="sxs-lookup"><span data-stu-id="5146b-116">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="5146b-117">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A> .</span><span class="sxs-lookup"><span data-stu-id="5146b-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5146b-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5146b-118">Example</span></span>  
 <span data-ttu-id="5146b-119">Zkompilujte `in.cs` a připojte soubor. ico `rf.ico` k výrobě `in.exe` :</span><span class="sxs-lookup"><span data-stu-id="5146b-119">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="5146b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5146b-120">See also</span></span>

- [<span data-ttu-id="5146b-121">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="5146b-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5146b-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="5146b-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
