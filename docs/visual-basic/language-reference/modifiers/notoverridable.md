---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6fc5fb006b36cda1b6ad0e128604bc3bb427fd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Určuje, že vlastnost nebo procedury nelze přepsat v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `NotOverridable` Modifikátor brání vlastnosti nebo metody přepsání v odvozené třídě.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě. Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud `Overridable` nebo `NotOverridable` modifikátor nezadáte, výchozí nastavení závisí na tom, jestli jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody. Pokud jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody, výchozí nastavení je `Overridable`, jinak je `NotOverridable`.  
  
 Element, který nebylo možné přepsat se někdy nazývá *zapečetěné* elementu.  
  
 Můžete použít `NotOverridable` jenom v příkazu deklarace vlastnosti nebo postupu. Můžete zadat `NotOverridable` pouze na vlastnosti nebo postup, který přepíše jinou vlastnost nebo postup, který je pouze v kombinaci s `Overrides`.  
  
## <a name="combined-modifiers"></a>Kombinovaná modifikátory  
 Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.  
  
 Nelze zadat `NotOverridable` společně s `MustOverride`, `Overridable`, nebo `Shared` ve stejné deklaraci.  
  
## <a name="usage"></a>Použití  
 `NotOverridable` Modifikátor lze použít v těchto kontexty:  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Modifikátory](../../../visual-basic/language-reference/modifiers/index.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Přepsání](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
