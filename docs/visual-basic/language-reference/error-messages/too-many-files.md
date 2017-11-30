---
title: "Příliš mnoho souborů"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 506f0735956267d51b575cd26b628605e9db38cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-files"></a><span data-ttu-id="f3407-102">Příliš mnoho souborů</span><span class="sxs-lookup"><span data-stu-id="f3407-102">Too many files</span></span>
<span data-ttu-id="f3407-103">Buď další soubory byly vytvořeny v kořenovém adresáři než operačního systému povolí, nebo více souborů byly otevřeny než číslo zadané v **soubory =** nastavení v souboru CONFIG. Soubor SYS.</span><span class="sxs-lookup"><span data-stu-id="f3407-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f3407-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f3407-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="f3407-105">Pokud váš program otevírání, zavírání nebo ukládání souborů v kořenovém adresáři, změňte tak, aby používala podadresáři vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="f3407-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2.  <span data-ttu-id="f3407-106">Zvýšit číslo zadané v soubory vaší **soubory =** nastavení v souboru CONFIG. SYS souboru a restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="f3407-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3407-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3407-107">See Also</span></span>  
 [<span data-ttu-id="f3407-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="f3407-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
