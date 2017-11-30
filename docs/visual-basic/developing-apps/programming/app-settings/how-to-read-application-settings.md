---
title: "Postupy: Čtení nastavení aplikace v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea6cfc529262053daf7c8111271de2c51e9cab4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Postupy: Čtení nastavení aplikace v jazyce Visual Basic
Uživatelské nastavení si můžete přečíst v přístupu k vlastnosti nastavení `My.Settings` objektu.  
  
 `My.Settings` Objekt zpřístupňuje každé nastavení vlastnosti. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. Toto nastavení **oboru** označuje, zda je vlastnost jen pro čtení; vlastnost pro **aplikace** oboru nastavení je jen pro čtení, při vlastnost pro **uživatele** obor nastavení je pro čtení a zápis. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje hodnotu `Nickname` nastavení.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také  
 [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
