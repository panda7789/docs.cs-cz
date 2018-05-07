---
title: 'Postupy: Změna uživatelského nastavení v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 2f67c3713a77c37ce43647980a9d3b17e47ba1bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Postupy: čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [Postupy: zachovaly uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
