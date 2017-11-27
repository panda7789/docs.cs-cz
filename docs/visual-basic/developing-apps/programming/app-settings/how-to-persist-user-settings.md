---
title: "Postupy: Zachování uživatelského nastavení v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1cf424a4e587818a8e2766a5e27c084010c084c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Postupy: Zachování uživatelského nastavení v jazyce Visual Basic
Můžete použít `My.Settings.Save` metoda k zachování změn nastavení uživatele.  
  
 Obvykle se aplikace jsou navržené a zachová tak změny nastavení pro uživatele po vypnutí aplikace. To je proto ukládání nastavení může trvat, v závislosti na několika faktorech, několik sekund.  
  
 Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  I když můžete změnit a uložit hodnoty uživatelského nastavení v době běhu, nastavení aplikace jsou jen pro čtení a nedá se změnit prostřednictvím kódu programu. Můžete změnit nastavení aplikace při vytváření aplikace, pomocí **Návrhář projektu**, nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  
 Tento příklad změní hodnotu `LastChanged` nastavení uživatele a uloží změny voláním `My.Settings.Save` metoda.  
  
 [!code-vb[VbVbalrMyResources#5](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-persist-user-settings_1.vb)]  
  
 Pro tento příklad fungoval, musí mít vaše aplikace `LastChanged` nastavení uživatele, typu `Date`. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také  
 [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Postupy: čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
