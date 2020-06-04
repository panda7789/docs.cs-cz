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
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396204"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Určuje, že třídu lze použít pouze jako základní třídu a že přímo z ní nelze vytvořit objekt.  
  
## <a name="remarks"></a>Poznámky  
 Účelem *základní třídy* (označované také jako *abstraktní třída*) je definování funkcionality, která je společná pro všechny třídy odvozené od ní. Tím se uloží odvozené třídy, abyste museli předefinovat společné prvky. V některých případech není tato společná funkce dostatečně dokončena, aby provedla použitelný objekt a každá odvozená třída definuje chybějící funkce. V takovém případě chcete, aby kód vytvářel objekty pouze z odvozených tříd. Použijete `MustInherit` na základní třídě k vykonání této zásady.  
  
 Dalším použitím `MustInherit` třídy je omezit proměnnou na sadu souvisejících tříd. Můžete definovat základní třídu a odvodit z ní všechny tyto související třídy. Základní třída nemusí poskytovat žádné funkce společné pro všechny odvozené třídy, ale může sloužit jako filtr pro přiřazení hodnot proměnným. Pokud váš nenáročný kód deklaruje proměnnou jako základní třídu, Visual Basic umožňuje přiřadit pouze objekt z jedné z odvozených tříd do této proměnné.  
  
 .NET Framework definuje několik `MustInherit` tříd, mezi nimi, <xref:System.Array> <xref:System.Enum> a <xref:System.ValueType> . <xref:System.ValueType>je příklad základní třídy, která omezuje proměnnou. Všechny typy hodnot jsou odvozeny z <xref:System.ValueType> . Pokud deklarujete proměnnou jako <xref:System.ValueType> , můžete k této proměnné přiřadit pouze typy hodnot.  
  
## <a name="rules"></a>Pravidla  
  
- **Kontext deklarace** Můžete použít `MustInherit` pouze v `Class` příkazu.  
  
- **Kombinované modifikátory.** Nelze zadat `MustInherit` společně s `NotInheritable` ve stejné deklaraci.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje vynucenou dědičnost a vynucené přepsání. Základní třída `shape` definuje proměnnou `acrossLine` . Třídy `circle` a `square` odvozují z `shape` . Dědí definici `acrossLine` , ale musí definovat funkci, `area` protože tento výpočet se liší pro každý druh obrazce.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Můžete deklarovat `shape1` a `shape2` být typu `shape` . Nemůžete však vytvořit objekt z, `shape` protože nemá funkci `area` a je označen `MustInherit` .  
  
 Vzhledem k tomu, že jsou deklarovány jako `shape` , proměnné `shape1` a `shape2` jsou omezeny na objekty z odvozených tříd `circle` a `square` . Visual Basic neumožňuje přiřadit žádné další objekty k těmto proměnným, což poskytuje vysokou úroveň bezpečnosti typů.  
  
## <a name="usage"></a>Využití  
 `MustInherit`V tomto kontextu lze použít modifikátor:  
  
 [Class – příkaz](../statements/class-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Inherits – příkaz](../statements/inherits-statement.md)
- [NotInheritable](notinheritable.md)
- [Klíčová slova](../keywords/index.md)
- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
