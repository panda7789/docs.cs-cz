---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: df05ff6caeae2fb2db6a8d7c8fec1b81774a9fa4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005387"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="79baf-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79baf-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="79baf-103">Instruuje kompilátor, aby nevložil žádný manifest aplikace do spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="79baf-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79baf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79baf-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="79baf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79baf-105">Remarks</span></span>  
 <span data-ttu-id="79baf-106">Pokud použijete tuto možnost, bude se aplikace vztahovat k virtualizaci v systému Windows Vista, pokud neposkytnete manifest aplikace v souboru prostředků Win32 nebo během pozdějšího kroku sestavení.</span><span class="sxs-lookup"><span data-stu-id="79baf-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="79baf-107">Další informace o virtualizaci najdete v tématu [nasazení ClickOnce v systému Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span><span class="sxs-lookup"><span data-stu-id="79baf-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="79baf-108">Další informace o vytváření manifestu naleznete v tématu [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span><span class="sxs-lookup"><span data-stu-id="79baf-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79baf-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79baf-109">See also</span></span>

- [<span data-ttu-id="79baf-110">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="79baf-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="79baf-111">Stránka Aplikace, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="79baf-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
