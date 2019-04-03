---
title: Příliš mnoho souborů
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: ceacb5d83fcfc9fcbd341cc5d9579c4e2e181353
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829886"
---
# <a name="too-many-files"></a><span data-ttu-id="881eb-102">Příliš mnoho souborů</span><span class="sxs-lookup"><span data-stu-id="881eb-102">Too many files</span></span>
<span data-ttu-id="881eb-103">Další soubory byly vytvořeny v kořenovém adresáři než operačního systému povolí, nebo nebyla otevřena další soubory než číslo zadané v **soubory =** nastavení v souboru CONFIG. SYS souboru.</span><span class="sxs-lookup"><span data-stu-id="881eb-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="881eb-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="881eb-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="881eb-105">Pokud váš program je otevření, zavření nebo ukládání souborů v kořenovém adresáři, změňte tak, aby používala podadresář váš program.</span><span class="sxs-lookup"><span data-stu-id="881eb-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2.  <span data-ttu-id="881eb-106">Zvýšit počet souborů podle vaší **soubory =** nastavení v souboru CONFIG. SYS souboru a restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="881eb-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881eb-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="881eb-107">See also</span></span>

- [<span data-ttu-id="881eb-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="881eb-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
