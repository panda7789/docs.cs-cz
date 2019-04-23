---
title: -optimize (možnosti kompilátoru C#)
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
ms.openlocfilehash: 25a9ee1b27836dfb00dcbc72712ed068639fa2fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320029"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="f4c95-102">-optimize (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="f4c95-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="f4c95-103">**– Optimalizace** možnost povolí nebo zakáže optimalizace provedené kompilátorem za účelem zkontrolujte výstupní soubor menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="f4c95-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4c95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4c95-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f4c95-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4c95-105">Remarks</span></span>  
 <span data-ttu-id="f4c95-106">**-optimize** také říká modul common language runtime k optimalizaci kódu za běhu.</span><span class="sxs-lookup"><span data-stu-id="f4c95-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="f4c95-107">Ve výchozím nastavení jsou zakázané optimalizace.</span><span class="sxs-lookup"><span data-stu-id="f4c95-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="f4c95-108">Zadejte **– optimalizace +** povolíte optimalizace.</span><span class="sxs-lookup"><span data-stu-id="f4c95-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="f4c95-109">Při vytváření modulu pro sestavení, použijte stejný **– optimalizace** nastavení jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="f4c95-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="f4c95-110">**-o** je zkratka pro **– optimalizace**.</span><span class="sxs-lookup"><span data-stu-id="f4c95-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="f4c95-111">Je možné kombinovat **– optimalizace** a [– ladění](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) možnosti.</span><span class="sxs-lookup"><span data-stu-id="f4c95-111">It is possible to combine the **-optimize** and [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f4c95-112">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4c95-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f4c95-113">Otevřete v projektu **vlastnosti** stránky.</span><span class="sxs-lookup"><span data-stu-id="f4c95-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="f4c95-114">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="f4c95-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="f4c95-115">Upravit **optimalizovat kód** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f4c95-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="f4c95-116">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f4c95-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4c95-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4c95-117">Example</span></span>  
 <span data-ttu-id="f4c95-118">Kompilace `t2.cs` a povolení optimalizace kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="f4c95-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4c95-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4c95-119">See also</span></span>

- [<span data-ttu-id="f4c95-120">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4c95-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="f4c95-121">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="f4c95-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
