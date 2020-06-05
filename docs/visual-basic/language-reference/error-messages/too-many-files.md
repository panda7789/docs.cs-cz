---
title: Příliš mnoho souborů
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 38d39ad20f350137d714ae5d09db5d2204b83621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362797"
---
# <a name="too-many-files"></a><span data-ttu-id="12bc5-102">Příliš mnoho souborů</span><span class="sxs-lookup"><span data-stu-id="12bc5-102">Too many files</span></span>
<span data-ttu-id="12bc5-103">V kořenovém adresáři, než povoluje operační systém, bylo vytvořeno více souborů, nebo bylo otevřeno více souborů než číslo zadané v souboru CONFIG **=** nastavení v konfiguraci. Soubor SYS.</span><span class="sxs-lookup"><span data-stu-id="12bc5-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12bc5-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="12bc5-104">To correct this error</span></span>  
  
1. <span data-ttu-id="12bc5-105">Pokud program otevírá, zavírá nebo ukládá soubory do kořenového adresáře, změňte program tak, aby používal podadresář.</span><span class="sxs-lookup"><span data-stu-id="12bc5-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="12bc5-106">Zvyšte počet souborů zadaných ve složce **Files =** nastavení v konfiguraci. Soubor SYS a restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="12bc5-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bc5-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="12bc5-107">See also</span></span>

- [<span data-ttu-id="12bc5-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="12bc5-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
