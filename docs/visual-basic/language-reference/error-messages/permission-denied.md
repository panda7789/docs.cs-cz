---
title: Oprávnění byla odepřena (Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: ad75c556748bf5c0f9cef55310c4ffa7b01fd458
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318828"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="31836-102">Oprávnění byla odepřena (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="31836-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="31836-103">Byl proveden pokus o zápis na disk chráněný proti zápisu nebo pro přístup k souboru uzamčené.</span><span class="sxs-lookup"><span data-stu-id="31836-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31836-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="31836-104">To correct this error</span></span>  
  
1. <span data-ttu-id="31836-105">Otevřete soubor chráněn proti zápisu, změňte atribut ochranu proti zápisu souboru.</span><span class="sxs-lookup"><span data-stu-id="31836-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2. <span data-ttu-id="31836-106">Ujistěte se, že nebyla uzamčen jiným procesem souboru a čekání k otevření souboru, dokud ho uvolní jiný proces.</span><span class="sxs-lookup"><span data-stu-id="31836-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3. <span data-ttu-id="31836-107">Pro přístup k registru, zkontrolujte, že vaše uživatelská oprávnění zahrnují tento typ přístupu k registru.</span><span class="sxs-lookup"><span data-stu-id="31836-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31836-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31836-108">See also</span></span>

- [<span data-ttu-id="31836-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="31836-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
