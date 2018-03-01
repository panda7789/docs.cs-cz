---
title: "Oprávnění byla odepřena (Visual Basic)."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID70
ms.assetid: 71f46756-f522-4814-aab4-492bf9924245
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5d7965ebd42cb3e56d66966d035be9ba3d3957c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="permission-denied-visual-basic"></a><span data-ttu-id="168d5-102">Oprávnění byla odepřena (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="168d5-102">Permission denied (Visual Basic)</span></span>
<span data-ttu-id="168d5-103">Byl proveden pokus o zápis na disk chráněný proti zápisu nebo získat přístup k uzamčení souboru.</span><span class="sxs-lookup"><span data-stu-id="168d5-103">An attempt was made to write to a write-protected disk or to access a locked file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="168d5-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="168d5-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="168d5-105">Otevřete soubor chráněn proti zápisu, změňte atribut ochranu proti zápisu souboru.</span><span class="sxs-lookup"><span data-stu-id="168d5-105">To open a write-protected file, change the write-protection attribute of the file.</span></span>  
  
2.  <span data-ttu-id="168d5-106">Ujistěte se, že jiný proces není uzamčen soubor a počkejte, dokud jiného procesu uvolněním otevřít soubor.</span><span class="sxs-lookup"><span data-stu-id="168d5-106">Make sure that another process has not locked the file, and wait to open the file until the other process releases it.</span></span>  
  
3.  <span data-ttu-id="168d5-107">Chcete-li získat přístup k registru, zkontrolujte, že vaše oprávnění uživatele obsahují tento typ přístupu registru.</span><span class="sxs-lookup"><span data-stu-id="168d5-107">To access the registry, check that your user permissions include this type of registry access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168d5-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="168d5-108">See Also</span></span>  
 [<span data-ttu-id="168d5-109">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="168d5-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
