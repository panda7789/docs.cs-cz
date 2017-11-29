---
title: "-nowin32manifest (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e0d4697e0e14c84c4bc642521cf4f9cdf6a4ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nowin32manifest-c-compiler-options"></a><span data-ttu-id="ef490-102">/nowin32manifest (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="ef490-102">/nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="ef490-103">Použití **/nowin32manifest** – možnost kompilátoru není pro vložení jakýkoli manifest aplikace do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="ef490-103">Use the **/nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef490-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef490-104">Syntax</span></span>  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="ef490-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef490-105">Remarks</span></span>  
 <span data-ttu-id="ef490-106">Pokud tato možnost se používá, aplikace budou platit virtualizace v systému Windows Vista Pokud není poskytnut manifest aplikace v souboru Win32 prostředků nebo v pozdějším kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef490-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="ef490-107">V sadě Visual Studio, nastavte tuto možnost **vlastnosti aplikace** stránky tak, že vyberete **vytvořit aplikaci bez manifestu** možnost **Manifest** rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef490-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="ef490-108">Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ef490-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="ef490-109">Další informace o vytváření manifestu najdete v tématu [/win32manifest (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="ef490-109">For more information about manifest creation, see [/win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef490-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef490-110">See Also</span></span>  
 [<span data-ttu-id="ef490-111">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="ef490-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ef490-112">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="ef490-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
