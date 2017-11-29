---
title: "Postupy: Změna uživatelského nastavení v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db35a5d63938fcc508c23af5588957d8dc518676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Postupy: Změna uživatelského nastavení v jazyce Visual Basic
Uživatelské nastavení můžete změnit přiřazením nové hodnoty pro vlastnosti nastavení na `My.Settings` objektu.  
  
 `My.Settings` Objekt zpřístupňuje každé nastavení vlastnosti. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. Toto nastavení **oboru** Určuje, zda je vlastnost jen pro čtení: vlastnost pro **aplikace**-oboru nastavení je jen pro čtení, při vlastnost pro **uživatele**-oboru nastavení je pro čtení a zápis. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  I když můžete změnit a uložit hodnoty uživatelského nastavení v době běhu, nastavení aplikace jsou jen pro čtení a nedá se změnit prostřednictvím kódu programu. Nastavení aplikace můžete změnit, když vytvoříte aplikaci pomocí **Návrhář projektu** nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  
 Tento příklad změní hodnotu `Nickname` nastavení uživatele.  
  
 [!code-vb[VbVbalrMyResources#7](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-change-user-settings_1.vb)]  
  
 Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` nastavení uživatele, typu `String`.  
  
 Při vypnutí aplikace, aplikace uloží uživatelská nastavení. Chcete-li uložit nastavení okamžitě, zavolejte `My.Settings.Save` metoda. Další informace najdete v tématu [postupy: zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také  
 [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Postupy: čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
