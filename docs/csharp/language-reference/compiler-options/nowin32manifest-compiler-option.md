---
title: -nowin32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 3ab52d541c169850f6ae7ba7e7cfded290f890e7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420616"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="88591-102">-nowin32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="88591-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="88591-103">Použití **-nowin32manifest** možnost dát pokyn kompilátoru, aby jakýkoli manifest aplikace pro vložení do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="88591-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88591-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88591-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="88591-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88591-105">Remarks</span></span>  
 <span data-ttu-id="88591-106">Při použití této možnosti aplikace se budou řídit virtualizace v systému Windows Vista, pokud nezadáte manifest aplikace do souboru prostředků Win32 nebo v pozdějším kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="88591-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="88591-107">V sadě Visual Studio, nastavte tuto možnost **vlastnost aplikace** stránky tak, že vyberete **vytvořit aplikaci bez manifestu** možnost **Manifest** rozevírací seznam.</span><span class="sxs-lookup"><span data-stu-id="88591-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="88591-108">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="88591-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="88591-109">Další informace o vytváření manifestu naleznete v tématu [-win32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="88591-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88591-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="88591-110">See Also</span></span>  

- [<span data-ttu-id="88591-111">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88591-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="88591-112">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="88591-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
