---
title: -win32icon (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606277"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="21366-102">-win32icon (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="21366-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="21366-103">Možnost **-win32icon** vloží soubor. ico do výstupního souboru, který poskytne výstupnímu souboru požadovaný vzhled v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="21366-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21366-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21366-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="21366-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="21366-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="21366-106">Soubor. ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="21366-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21366-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21366-107">Remarks</span></span>  
 <span data-ttu-id="21366-108">Soubor. ico se dá vytvořit s kompilátorem [prostředků](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="21366-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="21366-109">Kompilátor prostředků je vyvolán při kompilování vizuálního C++ programu; soubor. ico je vytvořen ze souboru. rc.</span><span class="sxs-lookup"><span data-stu-id="21366-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="21366-110">Viz [– linkresource –](./linkresource-compiler-option.md) (odkazování) nebo [-Resource](./resource-compiler-option.md) (pro připojení) .NET Frameworkho souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="21366-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="21366-111">Viz [-win32res](./win32res-compiler-option.md) pro import souboru. res.</span><span class="sxs-lookup"><span data-stu-id="21366-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="21366-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="21366-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="21366-113">Otevřete stránky **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="21366-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="21366-114">Klikněte na stránku vlastností **aplikace** .</span><span class="sxs-lookup"><span data-stu-id="21366-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="21366-115">Upravte vlastnost **ikona aplikace** .</span><span class="sxs-lookup"><span data-stu-id="21366-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="21366-116">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="21366-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21366-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="21366-117">Example</span></span>  
 <span data-ttu-id="21366-118">Zkompilujte `in.cs` a připojte soubor `rf.ico` . ico k výrobě `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="21366-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="21366-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21366-119">See also</span></span>

- [<span data-ttu-id="21366-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="21366-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="21366-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="21366-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
