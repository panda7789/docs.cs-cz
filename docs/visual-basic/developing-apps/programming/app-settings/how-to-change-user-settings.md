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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329619"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Postupy: Změna uživatelského nastavení v jazyce Visual Basic

Nastavení uživatele můžete změnit přiřazením nové hodnoty vlastnosti nastavení objektu `My.Settings`.  
  
 Objekt `My.Settings` zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení: vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení oboru **uživatele**je určena pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově. Můžete změnit nastavení rozsahu aplikace při vytváření aplikace pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  

 Tento příklad změní hodnotu nastavení `Nickname` uživatele.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Aby tento příklad fungoval, musí mít aplikace `Nickname` uživatelské nastavení typu `String`.  
  
 Aplikace uloží nastavení uživatele, když se aplikace vypíná. Chcete-li nastavení uložit hned, zavolejte metodu `My.Settings.Save`. Další informace najdete v tématu [Postup: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: čtení nastavení aplikace v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
