---
title: 'Postupy: Čtení nastavení aplikace v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: e7d909563ca7e991a51c2f921b5248aa587a83d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014073"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Postupy: Čtení nastavení aplikace v jazyce Visual Basic
Nastavením hlavního názvu uživatele si můžete přečíst na přístupem k nastavení vlastnosti `My.Settings` objektu.  
  
 `My.Settings` Objekt poskytuje každému nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typů nastavení. Toto nastavení **oboru** značí, zda je vlastnost jen pro čtení; vlastnost pro **aplikace** nastavení oboru je jen pro čtení, při vlastnost pro **uživatele** obor nastavení je pro čtení i zápis. Další informace najdete v tématu [My.Settings – objekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje hodnotu `Nickname` nastavení.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Pro tento příklad fungoval, musí mít vaše aplikace `Nickname` typu nastavení `String`. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro uživatelská nastavení v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
