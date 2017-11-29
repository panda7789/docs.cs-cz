---
title: "Může & č. 39; t vytvořit nezbytný dočasný soubor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbb1c65318f954249da097b026583b09ad340e20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="can39t-create-necessary-temporary-file"></a><span data-ttu-id="ca22a-102">Může & č. 39; t vytvořit nezbytný dočasný soubor</span><span class="sxs-lookup"><span data-stu-id="ca22a-102">Can&#39;t create necessary temporary file</span></span>
<span data-ttu-id="ca22a-103">Buď jednotka je plná obsahující adresáře, určené proměnnou prostředí TEMP, nebo proměnnou prostředí TEMP určuje jednotku neplatný nebo jen pro čtení nebo adresář.</span><span class="sxs-lookup"><span data-stu-id="ca22a-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca22a-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ca22a-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="ca22a-105">Odstraňte soubory z jednotky, pokud je úplná.</span><span class="sxs-lookup"><span data-stu-id="ca22a-105">Delete files from the drive, if full.</span></span>  
  
2.  <span data-ttu-id="ca22a-106">Zadejte jinou jednotku v proměnné prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="ca22a-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3.  <span data-ttu-id="ca22a-107">Zadejte platnou jednotku pro proměnnou prostředí TEMP.</span><span class="sxs-lookup"><span data-stu-id="ca22a-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4.  <span data-ttu-id="ca22a-108">Odeberte omezení jen pro čtení z aktuálně vybranou jednotku nebo adresář.</span><span class="sxs-lookup"><span data-stu-id="ca22a-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca22a-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca22a-109">See Also</span></span>  
 [<span data-ttu-id="ca22a-110">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="ca22a-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
