---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602837"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Určuje, že třídu lze použít pouze jako základní třída a že nelze vytvořit objekt přímo z něj.  
  
## <a name="remarks"></a>Poznámky  
 Účel *základní třída* (také označované jako *abstraktní třída*) je určit funkce, které jsou společné pro všechny třídy z něj odvozenou. To umožňuje ušetřit odvozené třídy z museli znovu definovat běžných elementech. V některých případech tato běžné funkce není dostatečně dokončení, aby objekt použitelné a každý odvozené třídy definuje chybějící funkce. V takovém případě budete chtít kód náročné vytvořit objekty pouze z odvozené třídy. Používáte `MustInherit` na základní třídy, chcete-li vynutit.  
  
 Další používání `MustInherit` třída je omezit proměnné na sadu související třídy. Můžete definovat základní třídy a všechny související třídy odvozena z něj. Není nutné poskytovat žádné funkce, které jsou společné pro všechny odvozené třídy základní třídy, ale může sloužit jako filtr pro přiřazení hodnoty k proměnné. Pokud náročné kód deklaruje proměnnou jako základní třída, Visual Basic umožňuje přiřadit pouze objekt z jednoho z odvozené třídy k této proměnné.  
  
 Rozhraní .NET Framework definuje několik `MustInherit` třídy mezi nimi <xref:System.Array>, <xref:System.Enum>, a <xref:System.ValueType>. <xref:System.ValueType> je příklad základní třídu, která omezuje proměnné. Všechny typy hodnot odvozena od <xref:System.ValueType>. Pokud je deklarovat proměnnou jako <xref:System.ValueType>, tuto proměnnou můžete přiřadit pouze typy hodnot.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `MustInherit` pouze v `Class` příkaz.  
  
-   **Kombinovaná parametrů.** Nelze zadat `MustInherit` společně s `NotInheritable` ve stejné deklaraci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ilustruje vynucené dědičnosti a Vynucené přepsání. Základní třída `shape` definuje proměnnou `acrossLine`. Třídy `circle` a `square` odvozena od `shape`. Dědí definice `acrossLine`, ale jejich musí definovat funkce `area` vzhledem k tomu, že výpočet se liší pro jednotlivé typy tvaru.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Je možné deklarovat `shape1` a `shape2` být typu `shape`. Však nelze vytvořit objekt z `shape` protože postrádá funkci funkce `area` a je označen jako `MustInherit`.  
  
 Protože jsou deklarovány jako `shape`, proměnné `shape1` a `shape2` jsou omezené na objekty z odvozené třídy `circle` a `square`. Visual Basic neumožňuje jakýkoliv jiný objekt přiřadit tyto proměnné, která poskytuje vysokou úroveň zabezpečení typů.  
  
## <a name="usage"></a>Použití  
 `MustInherit` Modifikátor můžete v tomto kontextu použít:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
