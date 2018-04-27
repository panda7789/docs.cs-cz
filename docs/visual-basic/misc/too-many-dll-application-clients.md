---
title: Příliš mnoho klientů aplikace knihovny DLL
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 78b3291531c2097fb4124486f6fbac40e2d13b8e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="92929-102">Příliš mnoho klientů aplikace knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="92929-102">Too many DLL application clients</span></span>
<span data-ttu-id="92929-103">Dynamická knihovna (DLL) jazyka Visual Basic zvládne přístup jenom omezené množství hostitele aplikací.</span><span class="sxs-lookup"><span data-stu-id="92929-103">The dynamic-link library (DLL) for Visual Basic can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="92929-104">Vaše aplikace a dalších aplikací, které jsou hostiteli jazyka Visual Basic (některé z nich může být přístupné aplikace) jsou všechny pokusu o přístup k knihovnu DLL jazyka Visual Basic ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="92929-104">Your application and other applications that are Visual Basic hosts (some of which may be accessed by your application) are all attempting to access the Visual Basic DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="92929-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="92929-105">To correct this error</span></span>  
  
-   <span data-ttu-id="92929-106">Snižte počet otevřených aplikací přístup Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="92929-106">Reduce the number of open applications accessing Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92929-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="92929-107">See Also</span></span>  
 [<span data-ttu-id="92929-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="92929-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
