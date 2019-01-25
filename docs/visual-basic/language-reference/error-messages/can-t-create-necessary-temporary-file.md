---
title: Můžete&#39;nezbytný dočasný soubor vytvořit t
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: c10444129f2a57bfef7f523a291e0f6d30e68d85
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610367"
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="39714-102">Můžete&#39;nezbytný dočasný soubor vytvořit t</span><span class="sxs-lookup"><span data-stu-id="39714-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="39714-103">Buď jednotka je plná, který obsahuje adresáře určené proměnnou prostředí TEMP nebo proměnná prostředí TEMP určuje neplatné nebo jen pro čtení disku nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="39714-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="39714-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="39714-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="39714-105">Odstraňte soubory z disku, pokud je úplná.</span><span class="sxs-lookup"><span data-stu-id="39714-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="39714-106">Zadejte jinou jednotku v proměnné prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="39714-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="39714-107">Zadejte platnou jednotku pro proměnnou prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="39714-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="39714-108">Odebrání tohoto omezení jen pro čtení z aktuálně vybranou jednotku nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="39714-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39714-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39714-109">See also</span></span>
- [<span data-ttu-id="39714-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="39714-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
