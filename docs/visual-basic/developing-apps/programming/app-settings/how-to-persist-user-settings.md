---
title: 'Postupy: zachování uživatelských nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329631"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Postupy: Zachování uživatelského nastavení v jazyce Visual Basic

Chcete-li zachovat změny nastavení uživatele, můžete použít metodu `My.Settings.Save`.  
  
 Aplikace jsou obvykle navržené tak, aby při ukončení aplikace vytrvaly změny nastavení uživatele. Důvodem je to, že ukládání nastavení může trvat v závislosti na několika faktorech, a to několik sekund.  
  
 Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově. Můžete změnit nastavení rozsahu aplikace při vytváření aplikace, pomocí **Návrháře projektu**nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  

 Tento příklad změní hodnotu nastavení `LastChanged` uživatele a uloží tuto změnu voláním metody `My.Settings.Save`.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Aby tento příklad fungoval, musí mít aplikace `LastChanged` uživatelské nastavení typu `Date`. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: čtení nastavení aplikace v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
