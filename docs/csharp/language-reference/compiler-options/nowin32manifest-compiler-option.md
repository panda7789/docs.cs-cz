---
title: -nowin32manifest (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602711"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="56b3d-102">-nowin32manifest (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="56b3d-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="56b3d-103">Pomocí možnosti **-nowin32manifest** můžete kompilátoru dát pokyn, aby do spustitelného souboru nevkládal žádný manifest aplikace.</span><span class="sxs-lookup"><span data-stu-id="56b3d-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56b3d-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="56b3d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56b3d-105">Remarks</span></span>  
 <span data-ttu-id="56b3d-106">Pokud je tato možnost použita, bude aplikace předmětem virtualizace v systému Windows Vista, pokud nezadáte manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="56b3d-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="56b3d-107">V sadě Visual Studio nastavte tuto možnost na stránce **Vlastnosti aplikace** výběrem **možnosti Vytvořit aplikaci bez manifestu** v rozevíracím seznamu **Manifest.**</span><span class="sxs-lookup"><span data-stu-id="56b3d-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="56b3d-108">Další informace naleznete v [tématu Stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="56b3d-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="56b3d-109">Další informace o vytvoření manifestu naleznete v tématu [-win32manifest (C# Compiler Options).](./win32manifest-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="56b3d-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b3d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="56b3d-110">See also</span></span>

- [<span data-ttu-id="56b3d-111">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="56b3d-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="56b3d-112">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="56b3d-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
