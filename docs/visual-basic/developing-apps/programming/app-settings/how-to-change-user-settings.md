---
title: 'Postupy: Změna uživatelského nastavení'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: c9b89459f9b443c3a447edce90fee3437bbf1b6a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410176"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Postupy: Změna uživatelského nastavení v jazyce Visual Basic

Nastavení uživatele můžete změnit přiřazením nové hodnoty k vlastnosti nastavení `My.Settings` objektu.  
  
 `My.Settings`Objekt zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení: vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení oboru **uživatele**je určena pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově. Můžete změnit nastavení rozsahu aplikace při vytváření aplikace pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  

 Tento příklad změní hodnotu `Nickname` nastavení uživatele.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` uživatelské nastavení typu `String` .  
  
 Aplikace uloží nastavení uživatele, když se aplikace vypíná. Chcete-li nastavení uložit hned, zavolejte `My.Settings.Save` metodu. Další informace najdete v tématu [Postup: zachování uživatelských nastavení v Visual Basic](how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také

- [My.Settings – objekt](../../../language-reference/objects/my-settings-object.md)
- [Postupy: Čtení nastavení aplikace v jazyce Visual Basic](how-to-read-application-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
