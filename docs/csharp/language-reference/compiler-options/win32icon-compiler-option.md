---
title: -win32icon (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606277"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="07e68-102">-win32icon (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="07e68-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="07e68-103">Volba **-win32icon** vloží do výstupního souboru soubor .ico, který dává výstupnímu souboru požadovaný vzhled v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="07e68-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07e68-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="07e68-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="07e68-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="07e68-106">Soubor ICO, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="07e68-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e68-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="07e68-107">Remarks</span></span>  
 <span data-ttu-id="07e68-108">Soubor .ico lze vytvořit pomocí [kompilátoru prostředků](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="07e68-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="07e68-109">Kompilátor prostředků je vyvolán při kompilaci programu Visual C++; Soubor .ico je vytvořen ze souboru RC.</span><span class="sxs-lookup"><span data-stu-id="07e68-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="07e68-110">Viz [-linkresource](./linkresource-compiler-option.md) (odkaz) nebo [-resource](./resource-compiler-option.md) (připojit) soubor prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07e68-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="07e68-111">Viz [-win32res](./win32res-compiler-option.md) pro import souboru .res.</span><span class="sxs-lookup"><span data-stu-id="07e68-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="07e68-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="07e68-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="07e68-113">Otevřete stránky **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="07e68-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="07e68-114">Klikněte na stránku vlastností **Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="07e68-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="07e68-115">Upravte vlastnost **ikony Aplikace.**</span><span class="sxs-lookup"><span data-stu-id="07e68-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="07e68-116">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="07e68-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07e68-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="07e68-117">Example</span></span>  
 <span data-ttu-id="07e68-118">Kompilace `in.cs` a připojení souboru `rf.ico` `in.exe`.ico k vytvoření :</span><span class="sxs-lookup"><span data-stu-id="07e68-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="07e68-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="07e68-119">See also</span></span>

- [<span data-ttu-id="07e68-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07e68-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="07e68-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="07e68-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
