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
ms.openlocfilehash: 0bda03d3c01356317fbcc56d44199ff4f9484b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053935"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Určuje, že třídu lze použít pouze jako základní třídu a objekt nelze vytvořit přímo z ní.  
  
## <a name="remarks"></a>Poznámky  
 Účel *základní třída* (označované také jako *abstraktní třídu*) je definování funkcí, které jsou společné pro všechny třídy odvozené z něj. To museli znovu definovat společné prvky uloží odvozené třídy. V některých případech tato běžné funkce není dostatečně kompletní, chcete-li použít objekt a Každá odvozená třída definuje chybějící funkce. V takovém případě má časově náročný kód k vytvoření objektů pouze z odvozených tříd. Použijete `MustInherit` na základní třídu, pokud to chcete vynutit.  
  
 Další používání `MustInherit` třída je omezit proměnnou na sadu souvisejících tříd. Můžete definovat základní třídy a z něj odvodit všechny související třídy. Není potřeba poskytují všechny funkce, které jsou společné pro všechny odvozené třídy základní třídy, ale může sloužit jako filtr pro přiřazení hodnoty proměnné. Pokud váš náročný kód deklaruje proměnnou jako základní třída, Visual Basic umožňuje přiřadit pouze objekt z jedné z odvozených tříd na tuto proměnnou.  
  
 Rozhraní .NET Framework definuje několik `MustInherit` tříd, mezi nimi <xref:System.Array>, <xref:System.Enum>, a <xref:System.ValueType>. <xref:System.ValueType> je příklad základní třídu, která omezuje proměnné. Všechny typy hodnot jsou odvozeny z <xref:System.ValueType>. Pokud deklarujete proměnnou jako <xref:System.ValueType>, k této proměnné můžete přiřadit jenom typy hodnot.  
  
## <a name="rules"></a>pravidla  
  
- **Místní deklarace.** Můžete použít `MustInherit` pouze v `Class` příkazu.  
  
- **Kombinované modifikátory.** Nelze zadat `MustInherit` spolu s `NotInheritable` ve stejné deklaraci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje vynucené dědičnosti a Vynucené přepsání. Základní třída `shape` definuje proměnnou `acrossLine`. Třídy `circle` a `square` odvozovat `shape`. Dědí definici `acrossLine`, ale jejich musí definovat funkci `area` protože výpočtu se liší pro každý druh tvaru.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Je možné deklarovat `shape1` a `shape2` typu `shape`. Však nelze vytvořit objekt `shape` protože postrádá funkčnost funkce `area` a je označen `MustInherit`.  
  
 Protože jsou deklarovány jako `shape`, proměnné `shape1` a `shape2` je omezena na objekty z odvozených tříd `circle` a `square`. Visual Basic neumožňuje jakýkoli jiný objekt přiřadit tyto proměnné, která poskytuje vysoký stupeň bezpečnost typů.  
  
## <a name="usage"></a>Použití  
 `MustInherit` Modifikátor lze použít v tomto kontextu:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
