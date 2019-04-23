---
title: Nezbytný dočasný soubor nelze vytvořit.
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 658c2ab1dc210bf472646bce529ae5ffd7f67bc5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310223"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="399e7-102">Nezbytný dočasný soubor nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="399e7-102">Can't create necessary temporary file</span></span>
<span data-ttu-id="399e7-103">Buď jednotka je plná, který obsahuje adresáře určené proměnnou prostředí TEMP nebo proměnná prostředí TEMP určuje neplatné nebo jen pro čtení disku nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="399e7-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="399e7-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="399e7-104">To correct this error</span></span>  
  
1. <span data-ttu-id="399e7-105">Odstraňte soubory z disku, pokud je úplná.</span><span class="sxs-lookup"><span data-stu-id="399e7-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="399e7-106">Zadejte jinou jednotku v proměnné prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="399e7-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="399e7-107">Zadejte platnou jednotku pro proměnnou prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="399e7-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="399e7-108">Odebrání tohoto omezení jen pro čtení z aktuálně vybranou jednotku nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="399e7-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399e7-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="399e7-109">See also</span></span>

- [<span data-ttu-id="399e7-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="399e7-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
