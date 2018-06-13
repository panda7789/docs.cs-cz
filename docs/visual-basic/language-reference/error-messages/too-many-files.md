---
title: Příliš mnoho souborů
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 8a9d89cc96e5b5875d0286becbf5b20d6895ae34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593964"
---
# <a name="too-many-files"></a><span data-ttu-id="91190-102">Příliš mnoho souborů</span><span class="sxs-lookup"><span data-stu-id="91190-102">Too many files</span></span>
<span data-ttu-id="91190-103">Buď další soubory byly vytvořeny v kořenovém adresáři než operačního systému povolí, nebo více souborů byly otevřeny než číslo zadané v **soubory =** nastavení v souboru CONFIG. Soubor SYS.</span><span class="sxs-lookup"><span data-stu-id="91190-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="91190-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="91190-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="91190-105">Pokud váš program otevírání, zavírání nebo ukládání souborů v kořenovém adresáři, změňte tak, aby používala podadresáři vašeho programu.</span><span class="sxs-lookup"><span data-stu-id="91190-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2.  <span data-ttu-id="91190-106">Zvýšit číslo zadané v soubory vaší **soubory =** nastavení v souboru CONFIG. SYS souboru a restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="91190-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91190-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="91190-107">See Also</span></span>  
 [<span data-ttu-id="91190-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="91190-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
