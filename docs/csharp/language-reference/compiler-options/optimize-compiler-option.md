---
title: "-optimize (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a><span data-ttu-id="3784c-102">/optimize (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="3784c-102">/optimize (C# Compiler Options)</span></span>
<span data-ttu-id="3784c-103">**/ Optimize** možnost povolí nebo zakáže optimalizace provádí kompilátoru k vytvoření výstupního souboru menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="3784c-103">The **/optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3784c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3784c-104">Syntax</span></span>  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="3784c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3784c-105">Remarks</span></span>  
 <span data-ttu-id="3784c-106">**/ optimize** informuje o modul common language runtime optimalizovat kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="3784c-106">**/optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="3784c-107">Ve výchozím nastavení jsou zakázány optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3784c-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="3784c-108">Zadejte **/ optimize +** povolit optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3784c-108">Specify **/optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="3784c-109">Při sestavování modulu, který bude používán sestavení, použijte stejný **/ optimize** nastavení jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="3784c-109">When building a module to be used by an assembly, use the same **/optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="3784c-110">**/o** je zkratka pro **/ optimize**.</span><span class="sxs-lookup"><span data-stu-id="3784c-110">**/o** is the short form of **/optimize**.</span></span>  
  
 <span data-ttu-id="3784c-111">Je možné kombinovat **/ optimize** a [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) možnosti.</span><span class="sxs-lookup"><span data-stu-id="3784c-111">It is possible to combine the **/optimize** and [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3784c-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3784c-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="3784c-113">Otevření projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="3784c-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="3784c-114">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="3784c-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="3784c-115">Změnit **optimalizovat kód** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3784c-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="3784c-116">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="3784c-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3784c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="3784c-117">Example</span></span>  
 <span data-ttu-id="3784c-118">Kompilace `t2.cs` a povolení optimalizace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="3784c-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="3784c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3784c-119">See Also</span></span>  
 [<span data-ttu-id="3784c-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="3784c-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="3784c-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="3784c-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
