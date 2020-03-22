---
title: 'Postupy: Zachování uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: b1026e400015ff7807144dca8e9ce6d72fe3d18e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74329631"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Postupy: Zachování uživatelského nastavení v jazyce Visual Basic

Tuto metodu `My.Settings.Save` můžete použít k zachování změn v nastavení uživatele.  
  
 Aplikace jsou obvykle navrženy tak, aby zachovat změny nastavení uživatele při vypnutí aplikace. Je to proto, že uložení nastavení může trvat, v závislosti na několika faktorech, několik sekund.  
  
 Další informace naleznete v tématu [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> Přestože můžete změnit a uložit hodnoty nastavení uživatelského oboru za běhu, nastavení oboru aplikace jsou jen pro čtení a nelze je programově změnit. Nastavení oboru aplikace můžete změnit při vytváření aplikace, prostřednictvím **Návrháře projektu**nebo úpravou konfiguračního souboru aplikace. Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  

 Tento příklad změní hodnotu nastavení `LastChanged` uživatele a uloží `My.Settings.Save` tuto změnu voláním metody.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Aby tento příklad fungoval, musí `LastChanged` mít aplikace uživatelské `Date`nastavení typu . Další informace naleznete v [tématu Správa nastavení aplikací (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
