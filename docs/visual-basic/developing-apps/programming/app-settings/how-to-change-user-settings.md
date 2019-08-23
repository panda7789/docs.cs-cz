---
title: 'Postupy: Změna uživatelského nastavení v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- user settings [Visual Basic], changing in Visual Basic
- user settings
- My.Settings object [Visual Basic], changing user settings
- examples [Visual Basic], changing user settings
ms.assetid: 41250181-c594-4854-9988-8183b9eb03cf
ms.openlocfilehash: 553ebc5b0d6381f56783df8be83344f96a21dd8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968407"
---
# <a name="how-to-change-user-settings-in-visual-basic"></a>Postupy: Změna uživatelského nastavení v Visual Basic
Nastavení uživatele můžete změnit přiřazením nové hodnoty k vlastnosti `My.Settings` nastavení objektu.  
  
 `My.Settings` Objekt zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Rozsah** nastavení určuje, zda je vlastnost určena pouze pro čtení: Vlastnost pro nastavení rozsahu **aplikace**je jen pro čtení a vlastnost pro nastavení rozsahu **uživatele**je pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
> I když můžete změnit a uložit hodnoty nastavení rozsahu uživatele v době běhu, nastavení rozsahu aplikace jsou jen pro čtení a nelze je změnit programově. Můžete změnit nastavení rozsahu aplikace při vytváření aplikace pomocí **Návrháře projektu** nebo úpravou konfiguračního souboru aplikace. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="example"></a>Příklad  
 Tento příklad změní hodnotu `Nickname` nastavení uživatele.  
  
 [!code-vb[VbVbalrMyResources#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#7)]  
  
 Aby tento příklad fungoval, musí mít `Nickname` vaše aplikace uživatelské nastavení typu. `String`  
  
 Aplikace uloží nastavení uživatele, když se aplikace vypíná. Chcete-li nastavení uložit hned, zavolejte `My.Settings.Save` metodu. Další informace najdete v tématu [jak: Zachovat uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Číst nastavení aplikace v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Postupy: Zachovat uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
