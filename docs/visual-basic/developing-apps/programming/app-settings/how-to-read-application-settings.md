---
title: 'Postupy: Čtení nastavení aplikace'
ms.date: 07/20/2015
helpviewer_keywords:
- reading application settings
- My.Settings object [Visual Basic], reading application settings
- application settings [Visual Basic], reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
ms.openlocfilehash: 9b326341c54d652479776e3ab93a2b140f4531e0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410137"
---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Postupy: Čtení nastavení aplikace v jazyce Visual Basic

Můžete číst nastavení uživatele přístupem k vlastnosti nastavení `My.Settings` objektu.  
  
 `My.Settings`Objekt zpřístupňuje každé nastavení jako vlastnost. Název vlastnosti je stejný jako název nastavení a typ vlastnosti je stejný jako typ nastavení. **Obor** nastavení určuje, zda je vlastnost určena pouze pro čtení; vlastnost pro nastavení rozsahu **aplikace** je jen pro čtení, zatímco vlastnost pro nastavení oboru **uživatele** je určena pro čtení i zápis. Další informace najdete v tématu [objekt My. Settings](../../../language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Příklad  

 V tomto příkladu se zobrazí hodnota `Nickname` nastavení.  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 Aby tento příklad fungoval, musí mít vaše aplikace `Nickname` Nastavení typu `String` . Další informace najdete v tématu [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Viz také

- [My.Settings – objekt](../../../language-reference/objects/my-settings-object.md)
- [Postupy: Změna uživatelského nastavení v jazyce Visual Basic](how-to-change-user-settings.md)
- [Postupy: Zachování uživatelského nastavení v jazyce Visual Basic](how-to-persist-user-settings.md)
- [Postupy: Vytváření mřížek vlastností pro nastavení uživatele v jazyce Visual Basic](how-to-create-property-grids-for-user-settings.md)
- [Správa nastavení aplikace (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
