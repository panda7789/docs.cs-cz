---
title: -optimalizovat (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606596"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="93721-102">-optimalizovat (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="93721-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="93721-103">Možnost **-optimize** umožňuje nebo zakáže optimalizace prováděné kompilátorem, aby byl výstupní soubor menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="93721-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93721-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93721-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="93721-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93721-105">Remarks</span></span>  
 <span data-ttu-id="93721-106">**-optimize** také říká, že společný jazyk runtime pro optimalizaci kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="93721-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="93721-107">Ve výchozím nastavení jsou optimalizace zakázány.</span><span class="sxs-lookup"><span data-stu-id="93721-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="93721-108">Zadejte **-optimize+** pro povolení optimalizace.</span><span class="sxs-lookup"><span data-stu-id="93721-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="93721-109">Při vytváření modulu, který má být používán sestavením, použijte stejné nastavení **optimalizace** jako nastavení sestavy.</span><span class="sxs-lookup"><span data-stu-id="93721-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="93721-110">**-o** je krátká forma **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="93721-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="93721-111">Je možné kombinovat možnosti **-optimize** a [-debug.](./debug-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="93721-111">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="93721-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="93721-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="93721-113">Otevřete stránku **Vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="93721-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="93721-114">Klikněte na stránku vlastností **Sestavení.**</span><span class="sxs-lookup"><span data-stu-id="93721-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="93721-115">Upravte vlastnost **Optimalizovat kód.**</span><span class="sxs-lookup"><span data-stu-id="93721-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="93721-116">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="93721-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93721-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="93721-117">Example</span></span>  
 <span data-ttu-id="93721-118">Kompilace `t2.cs` a povolení optimalizace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="93721-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="93721-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="93721-119">See also</span></span>

- [<span data-ttu-id="93721-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="93721-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="93721-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="93721-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
