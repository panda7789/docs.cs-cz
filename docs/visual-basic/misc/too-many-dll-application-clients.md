---
title: "Příliš mnoho klientů aplikace knihovny DLL"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a>Příliš mnoho klientů aplikace knihovny DLL
Dynamická knihovna (DLL) pro [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pouze zvládne přístup podle omezený počet hostitele aplikací. Vaše aplikace a dalších aplikací, které jsou [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hostitelů (některé z nich může být přístupné aplikace) se pokoušíte získat přístup [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] knihovny DLL ve stejnou dobu.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Snižte počet spuštěné aplikace přístup k [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Typy chyb](../../visual-basic/programming-guide/language-features/error-types.md)
