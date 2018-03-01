---
title: "Příliš mnoho klientů aplikace knihovny DLL"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="2a060-102">Příliš mnoho klientů aplikace knihovny DLL</span><span class="sxs-lookup"><span data-stu-id="2a060-102">Too many DLL application clients</span></span>
<span data-ttu-id="2a060-103">Dynamická knihovna (DLL) pro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pouze zvládne přístup podle omezený počet hostitele aplikací.</span><span class="sxs-lookup"><span data-stu-id="2a060-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="2a060-104">Vaše aplikace a dalších aplikací, které jsou [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hostitelů (některé z nich může být přístupné aplikace) se pokoušíte získat přístup [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] knihovny DLL ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="2a060-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2a060-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2a060-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2a060-106">Snižte počet spuštěné aplikace přístup k [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2a060-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a060-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a060-107">See Also</span></span>  
 [<span data-ttu-id="2a060-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="2a060-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
