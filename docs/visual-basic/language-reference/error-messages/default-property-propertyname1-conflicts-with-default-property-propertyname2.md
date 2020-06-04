---
title: Výchozí vlastnost '<propertyname1>' je v konfliktu s výchozí vlastností '<propertyname2>' ve třídě '<classname>' a je ji třeba deklarovat jako 'Shadows'.
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409722"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>Výchozí vlastnost '\<propertyname1>' je v konfliktu s výchozí vlastností '\<propertyname2>' ve třídě '\<classname>' a je ji třeba deklarovat jako 'Shadows'.
Vlastnost je deklarována se stejným názvem jako vlastnost definovaná v základní třídě. V této situaci by vlastnost v této třídě měla vytvořit stínovou vlastnost základní třídy.  
  
 Tato zpráva je upozornění. `Shadows`je ve výchozím nastavení předpokládaná. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40007  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte `Shadows` klíčové slovo do deklarace nebo změňte název vlastnosti, která je deklarována.  
  
## <a name="see-also"></a>Viz také

- [Shadows](../modifiers/shadows.md)
- [Stínění v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
