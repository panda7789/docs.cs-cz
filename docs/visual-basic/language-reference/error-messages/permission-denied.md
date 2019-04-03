---
title: Oprávnění byla odepřena (Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
ms.openlocfilehash: d904ee48ee187d073647b6e09af57264c8c318f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813948"
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="19051-102">Oprávnění byla odepřena (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="19051-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="19051-103">Byl proveden pokus o zápis na disk chráněný proti zápisu nebo pro přístup k souboru uzamčené.</span><span class="sxs-lookup"><span data-stu-id="19051-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19051-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="19051-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="19051-105">Otevřete soubor chráněn proti zápisu, změňte atribut ochranu proti zápisu souboru.</span><span class="sxs-lookup"><span data-stu-id="19051-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="19051-106">Ujistěte se, že nebyla uzamčen jiným procesem souboru a čekání k otevření souboru, dokud ho uvolní jiný proces.</span><span class="sxs-lookup"><span data-stu-id="19051-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="19051-107">Pro přístup k registru, zkontrolujte, že vaše uživatelská oprávnění zahrnují tento typ přístupu k registru.</span><span class="sxs-lookup"><span data-stu-id="19051-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19051-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19051-108">See also</span></span>

- [<span data-ttu-id="19051-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="19051-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
