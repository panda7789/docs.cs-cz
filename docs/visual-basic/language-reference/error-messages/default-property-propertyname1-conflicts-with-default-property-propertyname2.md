---
title: Výchozí vlastnost '<propertyname1>' je v konfliktu s výchozí vlastností '<propertyname2>' ve třídě '<classname>' a je ji třeba deklarovat jako 'Shadows'.
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: ab45278b2e1199282e3066c34828b9bda716e162
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803685"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>Výchozí vlastnost '\<propertyname1 >' je v konfliktu s výchozí vlastností '\<Název_vlastnosti2 >' v '\<classname > "a je třeba ji deklarovat 'Shadows'
Vlastnost je deklarována se stejným názvem jako vlastnost definována v základní třídě. V takovém případě by měl stínové vlastnosti v této třídě vlastnost základní třídy.  
  
 Tato zpráva je upozornění. `Shadows` předpokládá se ve výchozím nastavení. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40007  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidat `Shadows` – klíčové slovo na deklarace, nebo změňte název vlastnosti deklarované.  
  
## <a name="see-also"></a>Viz také:

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
