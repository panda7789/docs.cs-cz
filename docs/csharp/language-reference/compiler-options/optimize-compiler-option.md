---
description: -Optimize (možnosti kompilátoru C#)
title: -Optimize (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 6fd268414c4e54e7b4865733480f8917389015d0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125030"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="617b5-103">-Optimize (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="617b5-103">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="617b5-104">Možnost **-optimiz** povolí nebo zakáže optimalizace prováděné kompilátorem, aby byl výstupní soubor menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="617b5-104">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="617b5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="617b5-105">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="617b5-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="617b5-106">Remarks</span></span>  
 <span data-ttu-id="617b5-107">**– optimalizuje** také instruuje modul CLR (Common Language Runtime), aby optimalizoval kód za běhu.</span><span class="sxs-lookup"><span data-stu-id="617b5-107">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="617b5-108">Ve výchozím nastavení jsou optimalizace zakázané.</span><span class="sxs-lookup"><span data-stu-id="617b5-108">By default, optimizations are disabled.</span></span> <span data-ttu-id="617b5-109">Pokud chcete povolit optimalizace, zadejte **a optimalizujte +** .</span><span class="sxs-lookup"><span data-stu-id="617b5-109">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="617b5-110">Při sestavování modulu, který má být použit sestavením, použijte stejné nastavení **– optimalizovat** jako u sestavení.</span><span class="sxs-lookup"><span data-stu-id="617b5-110">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="617b5-111">**-o** je krátká forma typu **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="617b5-111">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="617b5-112">Je možné kombinovat možnosti **-optimalizovat** a [-ladit](./debug-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="617b5-112">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="617b5-113">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="617b5-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="617b5-114">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="617b5-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="617b5-115">Klikněte na stránku vlastností **Build (sestavit** ).</span><span class="sxs-lookup"><span data-stu-id="617b5-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="617b5-116">Upravte vlastnost **kód optimalizace** .</span><span class="sxs-lookup"><span data-stu-id="617b5-116">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="617b5-117">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A> .</span><span class="sxs-lookup"><span data-stu-id="617b5-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="617b5-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="617b5-118">Example</span></span>  
 <span data-ttu-id="617b5-119">Kompilovat `t2.cs` a povolit optimalizace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="617b5-119">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="617b5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="617b5-120">See also</span></span>

- [<span data-ttu-id="617b5-121">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="617b5-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="617b5-122">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="617b5-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
