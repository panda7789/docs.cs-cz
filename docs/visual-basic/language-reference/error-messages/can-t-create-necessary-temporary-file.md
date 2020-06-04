---
title: Nezbytný dočasný soubor nelze vytvořit.
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 1a1464e0ac0d87bf9763efe63f2e09927a157a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415424"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="d8413-102">Nezbytný dočasný soubor nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="d8413-102">Can't create necessary temporary file</span></span>
<span data-ttu-id="d8413-103">Jednotka je plná a obsahuje adresář určený proměnnou prostředí TEMP nebo proměnná prostředí TEMP určuje neplatnou jednotku nebo adresář jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d8413-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8413-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d8413-104">To correct this error</span></span>  
  
1. <span data-ttu-id="d8413-105">Pokud je to kompletní, odstraňte soubory z disku.</span><span class="sxs-lookup"><span data-stu-id="d8413-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="d8413-106">V proměnné prostředí TEMP zadejte jinou jednotku.</span><span class="sxs-lookup"><span data-stu-id="d8413-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="d8413-107">Zadejte platnou jednotku pro proměnnou prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="d8413-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="d8413-108">Odebere omezení jen pro čtení z aktuálně zadané jednotky nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="d8413-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8413-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8413-109">See also</span></span>

- [<span data-ttu-id="d8413-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="d8413-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
