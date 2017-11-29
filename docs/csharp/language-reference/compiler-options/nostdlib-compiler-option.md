---
title: "-nostdlib (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad3ca7775512623de43c7fe6b7fe1cf481ccca87
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="nostdlib-c-compiler-options"></a><span data-ttu-id="c89d0-102">/nostdlib (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c89d0-102">/nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="c89d0-103">**/ nostdlib** zabraňuje importu mscorlib.dll, která definuje obor názvů, celý systém.</span><span class="sxs-lookup"><span data-stu-id="c89d0-103">**/nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c89d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c89d0-104">Syntax</span></span>  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c89d0-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c89d0-105">Remarks</span></span>  
 <span data-ttu-id="c89d0-106">Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty.</span><span class="sxs-lookup"><span data-stu-id="c89d0-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="c89d0-107">Pokud nezadáte **/nostdlib**, mscorlib.dll bude importována do programu (totéž jako zadání **/nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="c89d0-107">If you do not specify **/nostdlib**, mscorlib.dll will be imported into your program (same as specifying **/nostdlib-**).</span></span> <span data-ttu-id="c89d0-108">Určení **/nostdlib** je stejné jako zadání **/nostdlib+**.</span><span class="sxs-lookup"><span data-stu-id="c89d0-108">Specifying **/nostdlib** is the same as specifying **/nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="c89d0-109">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c89d0-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="c89d0-110">Otevřete **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="c89d0-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="c89d0-111">Klikněte **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="c89d0-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="c89d0-112">Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c89d0-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="c89d0-113">Změnit **Neodkazovat mscorlib.dll** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c89d0-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="c89d0-114">Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="c89d0-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c89d0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c89d0-115">See Also</span></span>  
 [<span data-ttu-id="c89d0-116">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="c89d0-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
