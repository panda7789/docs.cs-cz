---
title: Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: fd1ec25582e919b84235502f5921edfbc6e1dade
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990206"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)

`My.Resources`Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načítat prostředky pro vaši aplikaci.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  

 Pomocí objektu lze načíst řadu prostředků, jako jsou například zvukové soubory, ikony, obrázky a řetězce `My.Resources` . Můžete například získat přístup k souborům prostředků specifických pro jazykovou verzi aplikace. Následující příklad nastaví ikonu formuláře na ikonu s názvem `Form1Icon` uloženou v souboru prostředků aplikace.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 `My.Resources`Objekt zpřístupňuje pouze globální prostředky. Neposkytuje přístup k souborům prostředků přidruženým k formulářům. Přístup k prostředkům formuláře z formuláře.  
  
 Podobně `My.Settings` objekt poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Další informace naleznete v tématu [objekt My. Resources](../../language-reference/objects/my-resources-object.md) a [My. Settings Object](../../language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Viz také

- [My.Resources – objekt](../../language-reference/objects/my-resources-object.md)
- [My.Settings – objekt](../../language-reference/objects/my-settings-object.md)
- [Přístup k nastavení aplikace](../programming/app-settings/index.md)
