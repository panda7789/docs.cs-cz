---
description: -nowin32manifest (možnosti kompilátoru C#)
title: -nowin32manifest (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8514ab5b118e320d456d1b7367fab3b463c3607a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125056"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="140f3-103">-nowin32manifest (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="140f3-103">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="140f3-104">Pomocí možnosti **-nowin32manifest** dejte kompilátoru pokyn, aby nevložil žádný manifest aplikace do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="140f3-104">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="140f3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="140f3-105">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="140f3-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="140f3-106">Remarks</span></span>  
 <span data-ttu-id="140f3-107">Pokud použijete tuto možnost, bude se aplikace vztahovat k virtualizaci v systému Windows Vista, pokud neposkytnete manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="140f3-107">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="140f3-108">V sadě Visual Studio nastavte tuto možnost na stránce **vlastností aplikace** výběrem možnosti **vytvořit aplikaci bez manifestu** v rozevíracím seznamu **manifest** .</span><span class="sxs-lookup"><span data-stu-id="140f3-108">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="140f3-109">Další informace naleznete na [stránce aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="140f3-109">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="140f3-110">Další informace o vytváření manifestu naleznete v tématu [-win32manifest (možnosti kompilátoru C#)](./win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="140f3-110">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="140f3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="140f3-111">See also</span></span>

- [<span data-ttu-id="140f3-112">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="140f3-112">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="140f3-113">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="140f3-113">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
