---
title: "Odvozené třídy nemohou vyvolat události třídy Base."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords: BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70dde8b96980adfd618e38b9ce142cdec56a6b13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Odvozené třídy nemohou vyvolat události třídy Base.
Událost může být vyvolána pouze z deklarace místa, ve kterém je deklarovaná. Proto třídy nemohou vyvolat události z jiné třídě, i jeden, ze kterého je odvozený.  
  
 **ID chyby:** BC30029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout `Event` příkaz nebo `RaiseEvent` příkaz tak, aby byly ve stejné třídě.  
  
## <a name="see-also"></a>Viz také  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
 [RaiseEvent – příkaz](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
