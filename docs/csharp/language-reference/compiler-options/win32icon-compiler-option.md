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
ms.openlocfilehash: ba5c7fcc8fe9e3eaab0a955f4cd1a1e07169049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216197"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="3306d-102">-win32icon (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3306d-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="3306d-103">**-Win32icon** možnost vloží soubor .ico, který do výstupního souboru, který poskytuje výstupní soubor požadovaný vzhled v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="3306d-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3306d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3306d-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="3306d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3306d-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3306d-106">Soubor .ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="3306d-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3306d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3306d-107">Remarks</span></span>  
 <span data-ttu-id="3306d-108">Soubor .ico, který může být vytvořen pomocí [kompilátor prostředků](https://msdn.microsoft.com/library/aa381042.aspx).</span><span class="sxs-lookup"><span data-stu-id="3306d-108">An .ico file can be created with the [Resource Compiler](https://msdn.microsoft.com/library/aa381042.aspx).</span></span> <span data-ttu-id="3306d-109">Kompilátor prostředků je vyvolán při kompilaci Visual C++ program; soubor .ico, který je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="3306d-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="3306d-110">V tématu [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (pro referenční dokumentace) nebo [– prostředek](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) souboru prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3306d-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="3306d-111">V tématu [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) .res soubor naimportovat.</span><span class="sxs-lookup"><span data-stu-id="3306d-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3306d-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3306d-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3306d-113">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="3306d-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="3306d-114">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="3306d-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="3306d-115">Změnit **ikona aplikace** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3306d-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="3306d-116">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="3306d-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3306d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3306d-117">Example</span></span>  
 <span data-ttu-id="3306d-118">Kompilace `in.cs` a připojte soubor .ico `rf.ico` k vytvoření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="3306d-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="3306d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3306d-119">See Also</span></span>  
 [<span data-ttu-id="3306d-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3306d-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="3306d-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3306d-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
