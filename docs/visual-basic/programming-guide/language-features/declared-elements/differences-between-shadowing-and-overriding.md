---
title: "Rozdíly mezi stínováním a přepsáním (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d67486d9c6af96d314abad7142ba86779d74f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Rozdíly mezi stínováním a přepsáním (Visual Basic)
Když definujete třídu, která dědí vlastnosti ze základní třídy, někdy chtějí znovu definovat jeden nebo více elementů základní třídu v odvozené třídě. Stínováním a přepsáním jsou k dispozici pro tento účel.  
  
## <a name="comparison"></a>Srovnání  
 Stínováním a přepsáním používá při odvozené třídy dědí vlastnosti ze základní třídy a obě znovu definovat jeden deklarovaný element s jinou. Ale existují významné rozdíly mezi nimi.  
  
 Následující tabulka porovnává stínový provoz s přepsání.  
  
||||  
|---|---|---|  
|Porovnání|Stínový provoz|Přepsání|  
|Účel|Chrání před následné Změna základní třídy, která představuje člen, které jste definovali již v odvozené třídě|Polymorfismus dosahuje definování jinou implementaci procedury nebo vlastnost s stejné volací sekvence<sup>1</sup>|  
|Předefinovaná – element|Žádné deklarovaný typ elementu|Pouze procedury (`Function`, `Sub`, nebo `Operator`) nebo vlastnost|  
|Opětovná definice elementu|Žádné deklarovaný typ elementu|Pouze postup nebo vlastnost s identické volací sekvence<sup>1</sup>|  
|Úroveň přístupu tohoto elementu opětovná definice|Všechny úrovně přístupu|Nelze změnit úroveň přístupu tohoto přepsaný prvek|  
|Přehlednosti a writability z opětovná definice elementu|Libovolnou kombinaci|Nelze změnit čitelnost nebo writability přepsané vlastnosti|  
|Možnost ovládat opětovná definice|Základní třída prvku nelze vynutit nebo zakázat stínováním|Můžete zadat základní třída prvku `MustOverride`, `NotOverridable`, nebo`Overridable`|  
|Použití – klíčové slovo|`Shadows`doporučení v odvozené třídě; `Shadows` předpokládá, že pokud ani `Shadows` ani `Overrides` zadaný<sup>2</sup>|`Overridable`nebo `MustOverride` požadované v základní třídě; `Overrides` požadované odvozené třídy|  
|Dědičnost opětovná definice elementu třídy odvozování z odvozené třídy|Stínový provoz element zdědí další odvozené třídy; stíněné element i nadále skryté<sup>3</sup>|Přepsání element zdědí další odvozené třídy; přepsaný prvek stále přepsat.|  
  
 <sup>1</sup> *volání pořadí* se skládá z typu elementu (`Function`, `Sub`, `Operator`, nebo `Property`), název, seznam parametrů a návratovým typem. Nejde přepsat procedury vlastnosti nebo naopak. Nejde přepsat jeden druh procedury (`Function`, `Sub`, nebo `Operator`) s jiného typu.  
  
 <sup>2</sup> Pokud nezadáte buď `Shadows` nebo `Overrides`, vydá upozornění můžete Ujistěte se, jaký druh předefinování, kterou chcete použít. Pokud budete ignorovat upozornění, použije se stínového provozu mechanismus.  
  
 <sup>3</sup> Pokud element stínového provozu je nedostupná další odvozené třídy, není zděděna stínový provoz. Například, pokud je deklarovat stínového provozu element jako `Private`, třídu odvozování z odvozené třídy dědí původní element místo prvku stínového provozu.  
  
## <a name="guidelines"></a>Pokyny  
 Standardně používáte přepsání v následujících případech:  
  
-   Definování polymorfní odvozené třídy.  
  
-   Chcete bezpečnost s kompilátoru vynutit typ elementu identické a volací sekvence.  
  
 Standardně používáte stínový provoz v následujících případech:  
  
-   Předpokládáte, že vaše základní třída by se mohly změnit a definovat elementu s použitím stejný název jako vaše.  
  
-   Chcete volnost Změna typu elementu nebo sekvence volání.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Postupy: skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Stínů](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Přepsání](../../../../visual-basic/language-reference/modifiers/overrides.md)
