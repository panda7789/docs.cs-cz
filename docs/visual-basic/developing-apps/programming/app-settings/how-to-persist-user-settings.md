---
title: 'Postupy: Zachování uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], persisting user settings
- persistence [Visual Basic], persisting user settings [Visual Basic]
- user settings [Visual Basic], persisting
ms.assetid: 0e5e6415-b6e2-4602-9be0-a65fa167d007
ms.openlocfilehash: 817111060259bdfbbb26d9f8eafeae439e1f651f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410150"
---
# <a name="how-to-persist-user-settings-in-visual-basic"></a>Postupy: Zachování uživatelského nastavení v jazyce Visual Basic

Můžete použít `My.Settings.Save` metodu k uchování změn nastavení uživatele.  
  
 Aplikace jsou obvykle navržené tak, aby při ukončení aplikace vytrvaly změny nastavení uživatele. Důvodem je to, že ukládání nastavení může trvat v závislosti na několika faktorech, a to několik sekund.  
  
 Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově. Můžete změnit nastavení rozsahu aplikace při vytváření aplikace, pomocí **Návrháře projektu**nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  

 Tento příklad změní hodnotu `LastChanged` nastavení uživatele a uloží tuto změnu voláním `My.Settings.Save` metody.  
  
 [!code-vb[VbVbalrMyResources#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#5)]  
  
 Aby tento příklad fungoval, musí mít vaše aplikace `LastChanged` uživatelské nastavení typu `Date` . Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také

- [My.Settings – objekt](../../../language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](how-to-read-application-settings.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](how-to-change-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
