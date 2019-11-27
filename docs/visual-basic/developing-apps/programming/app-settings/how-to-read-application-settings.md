---
title: 'Postupy: čtení nastavení aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 04726381f8d285ae61045d1624b3b41b7f47e491
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329573"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Postupy: Čtení nastavení aplikace v jazyce Visual Basic

Můžete číst nastavení uživatele přístupem k vlastnosti nastavení objektu `My.Settings`.  
  
 Objekt `My.Settings` zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Obor** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace** je jen pro čtení, zatímco vlastnost pro nastavení oboru **uživatele** je určena pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Příklad  

 V tomto příkladu se zobrazí hodnota nastavení `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby tento příklad fungoval, musí mít aplikace `Nickname` nastavení typu `String`. Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Postupy: Změna uživatelského nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Postupy: zachování uživatelských nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Postupy: vytváření mřížek vlastností pro uživatelská nastavení v Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
