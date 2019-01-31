---
title: Výchozí vlastnost '<propertyname1>' je v konfliktu s výchozí vlastností '<propertyname2>' ve třídě '<classname>' a je ji třeba deklarovat jako 'Shadows'.
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: bc75b01532ffb112622d7f9bc837490c627883b3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270381"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>Výchozí vlastnost '\<propertyname1 >' je v konfliktu s výchozí vlastností '\<Název_vlastnosti2 >' v '\<classname > "a je třeba ji deklarovat 'Shadows'
Vlastnost je deklarována se stejným názvem jako vlastnost definována v základní třídě. V takovém případě by měl stínové vlastnosti v této třídě vlastnost základní třídy.  
  
 Tato zpráva je upozornění. `Shadows` předpokládá se ve výchozím nastavení. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40007  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `Shadows` – klíčové slovo na deklarace, nebo změňte název vlastnosti deklarované.  
  
## <a name="see-also"></a>Viz také:
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
