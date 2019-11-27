---
title: MustInherit
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
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351500"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Určuje, že třídu lze použít pouze jako základní třídu a že přímo z ní nelze vytvořit objekt.  
  
## <a name="remarks"></a>Poznámky  
 Účelem *základní třídy* (označované také jako *abstraktní třída*) je definování funkcionality, která je společná pro všechny třídy odvozené od ní. Tím se uloží odvozené třídy, abyste museli předefinovat společné prvky. V některých případech není tato společná funkce dostatečně dokončena, aby provedla použitelný objekt a každá odvozená třída definuje chybějící funkce. V takovém případě chcete, aby kód vytvářel objekty pouze z odvozených tříd. K vykonání je použit `MustInherit` na základní třídě.  
  
 Dalším použitím `MustInherit` třídy je omezit proměnnou na sadu souvisejících tříd. Můžete definovat základní třídu a odvodit z ní všechny tyto související třídy. Základní třída nemusí poskytovat žádné funkce společné pro všechny odvozené třídy, ale může sloužit jako filtr pro přiřazení hodnot proměnným. Pokud váš nenáročný kód deklaruje proměnnou jako základní třídu, Visual Basic umožňuje přiřadit pouze objekt z jedné z odvozených tříd do této proměnné.  
  
 .NET Framework definuje několik tříd `MustInherit`, mezi nimi <xref:System.Array>, <xref:System.Enum>a <xref:System.ValueType>. <xref:System.ValueType> je příklad základní třídy, která omezuje proměnnou. Všechny typy hodnot jsou odvozeny od <xref:System.ValueType>. Pokud deklarujete proměnnou jako <xref:System.ValueType>, můžete této proměnné přiřadit pouze typy hodnot.  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** `MustInherit` lze použít pouze v příkazu `Class`.  
  
- **Kombinované modifikátory.** Nemůžete zadat `MustInherit` společně s `NotInheritable` ve stejné deklaraci.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje vynucenou dědičnost a vynucené přepsání. Základní třída `shape` definuje proměnnou `acrossLine`. Třídy `circle` a `square` jsou odvozeny z `shape`. Dědí definici `acrossLine`, ale musí definovat funkci `area`, protože tento výpočet se liší pro každý druh obrazce.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Můžete deklarovat `shape1` a `shape2` být typu `shape`. Nemůžete však vytvořit objekt z `shape`, protože nemá funkci `area` funkce a je označena `MustInherit`.  
  
 Vzhledem k tomu, že jsou deklarovány jako `shape`, proměnné `shape1` a `shape2` jsou omezeny na objekty z odvozených tříd `circle` a `square`. Visual Basic neumožňuje přiřadit žádné další objekty k těmto proměnným, což poskytuje vysokou úroveň bezpečnosti typů.  
  
## <a name="usage"></a>Využití  
 V tomto kontextu lze použít modifikátor `MustInherit`:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
