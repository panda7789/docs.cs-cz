---
title: Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349269"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>Rychlý vývoj aplikací s použitím objektů My.Resources a My.Settings (Visual Basic)

Objekt `My.Resources` poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načítat prostředky pro vaši aplikaci.  
  
## <a name="retrieving-resources"></a>Načítání prostředků  

 Množství prostředků, jako jsou zvukové soubory, ikony, obrázky a řetězce, lze načíst prostřednictvím objektu `My.Resources`. Můžete například získat přístup k souborům prostředků specifických pro jazykovou verzi aplikace. Následující příklad nastaví ikonu formuláře na ikonu s názvem `Form1Icon` uloženou v souboru prostředků aplikace.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 Objekt `My.Resources` zpřístupňuje pouze globální prostředky. Neposkytuje přístup k souborům prostředků přidruženým k formulářům. Musíte získat přístup k prostředkům formuláře z formuláře.  
  
 Podobně objekt `My.Settings` poskytuje přístup k nastavení aplikace a umožňuje dynamicky ukládat a načítat nastavení vlastností a další informace pro vaši aplikaci. Další informace naleznete v tématu [objekt My. Resources](../../../visual-basic/language-reference/objects/my-resources-object.md) a [My. Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>Viz také:

- [Objekt My.Resources](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [Objekt My.Settings](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Přístup k nastavení aplikace](../../../visual-basic/developing-apps/programming/app-settings/index.md)
