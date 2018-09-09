---
title: -win32icon (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5014b1da714f8e29f869d4641da93796a607aa4d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225344"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="237ff-102">-win32icon (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="237ff-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="237ff-103">**-Win32icon** možnost vloží soubor .ico do výstupního souboru, který dává výstupnímu souboru požadovaný vzhled v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="237ff-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="237ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="237ff-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="237ff-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="237ff-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="237ff-106">Soubor .ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="237ff-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="237ff-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="237ff-107">Remarks</span></span>  
 <span data-ttu-id="237ff-108">Soubor .ico, který lze vytvořit pomocí [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="237ff-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="237ff-109">Nástroj Resource Compiler je vyvolán při kompilaci programu v jazyce Visual C++; soubor .ico je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="237ff-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="237ff-110">Zobrazit [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (na odkaz) nebo [– prostředků](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) soubor prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="237ff-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="237ff-111">Zobrazit [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) importovat soubor .res.</span><span class="sxs-lookup"><span data-stu-id="237ff-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="237ff-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="237ff-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="237ff-113">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="237ff-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="237ff-114">Klikněte na tlačítko **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="237ff-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="237ff-115">Upravit **ikona aplikace** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="237ff-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="237ff-116">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="237ff-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="237ff-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="237ff-117">Example</span></span>  
 <span data-ttu-id="237ff-118">Kompilace `in.cs` a připojte soubor .ico `rf.ico` k vytvoření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="237ff-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="237ff-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="237ff-119">See Also</span></span>  

- [<span data-ttu-id="237ff-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="237ff-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="237ff-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="237ff-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
