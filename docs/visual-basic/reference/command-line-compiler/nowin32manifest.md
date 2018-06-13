---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba4abc4a94a4938d54b3c34fbea2a5041a99454f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648759"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="5e55d-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e55d-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="5e55d-103">Dá pokyn kompilátoru není pro vložení jakýkoli manifest aplikace do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="5e55d-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e55d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e55d-104">Syntax</span></span>  
  
```  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="5e55d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5e55d-105">Remarks</span></span>  
 <span data-ttu-id="5e55d-106">Pokud tato možnost se používá, aplikace budou platit virtualizace v systému Windows Vista Pokud není poskytnut manifest aplikace v souboru Win32 prostředků nebo v pozdějším kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="5e55d-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="5e55d-107">Další informace o virtualizaci najdete v tématu [ClickOnce – nasazení v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="5e55d-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="5e55d-108">Další informace o vytváření manifestu najdete v tématu [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="5e55d-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e55d-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e55d-109">See Also</span></span>  
 [<span data-ttu-id="5e55d-110">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5e55d-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5e55d-111">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e55d-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
