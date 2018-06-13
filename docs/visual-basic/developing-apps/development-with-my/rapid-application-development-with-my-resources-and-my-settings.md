---
title: Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: 808e02510d4f0a237ad4354b2edac8fa024b5f83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582269"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)
`My.Resources` Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načíst prostředky pro vaši aplikaci.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  
 Počet prostředků, jako je například zvukové soubory, ikony, Image a řetězce mohou být načteny prostřednictvím `My.Resources` objektu. Například můžete přístup k souborům prostředků specifické pro jazykovou verzi aplikace. Následující příklad nastaví ikona formuláře na ikonu s názvem `Form1Icon` uložené v souboru prostředků aplikace.  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` Objekt se poskytuje pouze globální prostředky. Neposkytuje přístup k prostředku soubory spojené s formuláři. Ve formuláři musí přístup k prostředkům formuláře.  
  
 Podobně `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládání a načítání nastavení vlastností a další informace pro vaši aplikaci. Další informace najdete v tématu [My.Resources – objekt](../../../visual-basic/language-reference/objects/my-resources-object.md) a [My.Settings – objekt](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Viz také  
 [Objekt My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)  
 [Objekt My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)  
 [Přístup k nastavení aplikace](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
