---
title: "-win32icon (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 356502b8528e22a5b5ff9a28a3f82d5f9c0a72f9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2017
---
# <a name="win32icon-c-compiler-options"></a><span data-ttu-id="74681-102">/win32icon (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="74681-102">/win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="74681-103">**/Win32icon** možnost vloží soubor .ico, který do výstupního souboru, který poskytuje výstupní soubor požadovaný vzhled v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="74681-103">The **/win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74681-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74681-104">Syntax</span></span>  
  
```console  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="74681-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="74681-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="74681-106">Soubor .ico, který chcete přidat do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="74681-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74681-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74681-107">Remarks</span></span>  
 <span data-ttu-id="74681-108">Soubor .ico, který může být vytvořen pomocí [kompilátor prostředků](https://msdn.microsoft.com/library/aa381042.aspx).</span><span class="sxs-lookup"><span data-stu-id="74681-108">An .ico file can be created with the [Resource Compiler](https://msdn.microsoft.com/library/aa381042.aspx).</span></span> <span data-ttu-id="74681-109">Kompilátor prostředků je vyvolán při kompilaci Visual C++ program; soubor .ico, který je vytvořen ze souboru .rc.</span><span class="sxs-lookup"><span data-stu-id="74681-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="74681-110">V tématu [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (pro referenční dokumentace) nebo [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (pro připojení) souboru prostředků rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74681-110">See [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="74681-111">V tématu [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) .res soubor naimportovat.</span><span class="sxs-lookup"><span data-stu-id="74681-111">See [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="74681-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="74681-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="74681-113">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="74681-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="74681-114">Klikněte **aplikace** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="74681-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="74681-115">Změnit **ikona aplikace** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="74681-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="74681-116">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="74681-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74681-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="74681-117">Example</span></span>  
 <span data-ttu-id="74681-118">Kompilace `in.cs` a připojte soubor .ico `rf.ico` k vytvoření `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="74681-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc /win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="74681-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="74681-119">See Also</span></span>  
 [<span data-ttu-id="74681-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="74681-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="74681-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="74681-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
