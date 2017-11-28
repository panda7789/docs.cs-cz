---
title: "Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1657febf935560ff4c8dd2f54b10fdcb2254891f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)
`My.Resources` Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načíst prostředky pro vaši aplikaci.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  
 Počet prostředků, jako je například zvukové soubory, ikony, Image a řetězce mohou být načteny prostřednictvím `My.Resources` objektu. Například můžete přístup k souborům prostředků specifické pro jazykovou verzi aplikace. Následující příklad nastaví ikona formuláře na ikonu s názvem `Form1Icon` uložené v souboru prostředků aplikace.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` Objekt se poskytuje pouze globální prostředky. Neposkytuje přístup k prostředku soubory spojené s formuláři. Ve formuláři musí přístup k prostředkům formuláře. Další informace najdete v tématu [návod: lokalizace Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5).  
  
 Podobně `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládání a načítání nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [My.Resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) a [My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Viz také  
 [My.Resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Přístup k nastavení aplikace](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
