---
title: 'Postupy: Změna uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: d24b6d239c894788ce67b0723b4bf034050bf307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329619"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Postupy: Změna uživatelského nastavení v jazyce Visual Basic

Nastavení uživatele můžete změnit přiřazením nové hodnoty vlastnosti nastavení `My.Settings` objektu.  
  
 Objekt `My.Settings` zveřejňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Obor** nastavení určuje, zda je vlastnost jen pro čtení: Vlastnost pro nastavení **Application**-scope je jen pro čtení, zatímco vlastnost pro nastavení **User**-scope je čtení a zápis. Další informace naleznete v tématu [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Přestože můžete změnit a uložit hodnoty nastavení uživatelského oboru za běhu, nastavení oboru aplikace jsou jen pro čtení a nelze je programově změnit. Nastavení oboru aplikace můžete změnit při vytváření aplikace pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace. Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  

 Tento příklad změní hodnotu nastavení `Nickname` uživatele.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Aby tento příklad fungoval, musí `Nickname` mít aplikace uživatelské `String`nastavení typu .  
  
 Aplikace uloží uživatelská nastavení při vypnutí aplikace. Chcete-li nastavení uložit `My.Settings.Save` okamžitě, zavolejte metodu. Další informace naleznete v [tématu How to: Persist User Settings in Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
