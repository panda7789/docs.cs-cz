---
title: Automaticky implementované vlastnosti
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: b322bd2215c95298be0a33ace1f3590a63878e24
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350387"
---
# <a name="auto-implemented-properties-visual-basic"></a>Automaticky implementované vlastnosti (Visual Basic)
*Automaticky implementované vlastnosti* umožňují rychle zadat vlastnost třídy, aniž byste museli psát kód pro `Get` a `Set` vlastnost. Při psaní kódu pro automaticky implementovanou vlastnost automaticky vytvoří kompilátor Visual Basic privátní pole pro uložení proměnné vlastnosti kromě vytvoření přidružených `Get` a `Set` postupů.  
  
 S automaticky implementovanými vlastnostmi lze vlastnost, včetně výchozí hodnoty, deklarovat na jednom řádku. Následující příklad ukazuje tři deklarace vlastností.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Automaticky implementovaná vlastnost je ekvivalentní vlastnosti, pro kterou je hodnota vlastnosti uložena v soukromém poli. Následující příklad kódu ukazuje automaticky implementovanou vlastnost.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 Následující příklad kódu ukazuje ekvivalentní kód pro předchozí automaticky implementovaný příklad vlastnosti.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 Následující kód ukazuje implementaci vlastností ReadOnly:  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 K vlastnosti můžete přiřadit výrazy inicializace, jak je znázorněno v příkladu, nebo můžete přiřadit vlastnosti v konstruktoru nadřazeného typu.  Můžete kdykoli přiřadit k zálohovaným polím vlastností ReadOnly.  
  
## <a name="backing-field"></a>Pole pro zálohování  
 Pokud deklarujete automaticky implementovanou vlastnost, Visual Basic automaticky vytvoří skryté soukromé pole s názvem *pole zálohování* , které obsahuje hodnotu vlastnosti. Název záložního pole je název automaticky implementované vlastnosti předchází podtržítkem (_). Například pokud deklarujete automaticky implementovanou vlastnost s názvem `ID`, je pole pro zálohování pojmenované `_ID`. Pokud zahrnete člena vaší třídy, který je také pojmenován `_ID`, vytváříte konflikt názvů a Visual Basic ohlásí chybu kompilátoru.  
  
 Pole pro zálohování má také následující vlastnosti:  
  
- Modifikátor přístupu pro pole pro zálohování je vždycky `Private`, i když má vlastní vlastnost jinou úroveň přístupu, třeba `Public`.  
  
- Je-li vlastnost označena jako `Shared`, je sdíleno také pole zálohování.  
  
- Atributy zadané pro vlastnost se nevztahují na pole pro zálohování.  
  
- K poli pro zálohování se dá dostat z kódu v rámci třídy a z ladicích nástrojů, jako je okno Kukátko. Pole zálohování se ale nezobrazí v seznamu dokončování slov IntelliSense.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializuje se automaticky implementovaná vlastnost.  
 Libovolný výraz, který lze použít k inicializaci pole, je platný pro inicializaci automaticky implementované vlastnosti. Při inicializaci automaticky implementované vlastnosti se výraz vyhodnotí a předává `Set` proceduře pro vlastnost. Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které obsahují počáteční hodnoty.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Nelze inicializovat automaticky implementovanou vlastnost, která je členem `Interface`, nebo jinou, která je označena `MustOverride`.  
  
 Pokud deklarujete automaticky implementovanou vlastnost jako člena `Structure`, lze pouze inicializovat vlastnost automaticky implementované, pokud je označena jako `Shared`.  
  
 Pokud deklarujete automaticky implementovanou vlastnost jako pole, nemůžete zadat explicitní meze pole. Můžete však dodat hodnotu pomocí inicializátoru pole, jak je znázorněno v následujících příkladech.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definice vlastností, které vyžadují standardní syntaxi  
 Automaticky implementované vlastnosti jsou pohodlné a podporují řadu programovacích scénářů. Existují však situace, kdy nemůžete použít automaticky implementovanou vlastnost a místo toho je třeba použít standardní nebo *rozbalenou*syntaxi vlastností.  
  
 Pokud chcete provést některou z následujících akcí, je nutné použít rozšířenou syntaxi definice vlastností:  
  
- Přidejte kód do `Get` nebo `Set` postupu vlastnosti, jako je například kód pro ověření příchozích hodnot v `Set` proceduře. Například může být vhodné ověřit, že řetězec představující telefonní číslo obsahuje požadovaný počet číslic před nastavením hodnoty vlastnosti.  
  
- Zadejte pro `Get` a `Set` postup jinou přístupnost. Například můžete chtít provést `Set` proceduru `Private` a `Get` procedury `Public`.  
  
- Vytvořte vlastnosti, které jsou `WriteOnly`.  
  
- Použijte parametrizované vlastnosti (včetně `Default` vlastností). Chcete-li určit parametr pro vlastnost nebo zadat další parametry pro `Set` proceduru, je nutné deklarovat rozšířenou vlastnost.  
  
- Umístěte atribut do pole zálohování nebo změňte úroveň přístupu v poli pro zálohování.  
  
- Zadejte komentáře XML pro pole zálohování.  
  
## <a name="expanding-an-auto-implemented-property"></a>Rozšíření automaticky implementované vlastnosti  
 Pokud je nutné převést automaticky implementovanou vlastnost na rozšířenou vlastnost obsahující `Get` nebo `Set` postup, Editor kódu Visual Basic může automaticky generovat `Get` a `Set` postupy a příkaz `End Property` pro vlastnost. Kód je vygenerován při vložení kurzoru do prázdného řádku za příkazem `Property`, zadejte `G` (pro `Get`) nebo `S` (pro `Set`) a stiskněte klávesu ENTER. Editor kódu Visual Basic automaticky generuje `Get` nebo `Set` procedury pro vlastnosti jen pro čtení a jen pro zápis, když stisknete klávesu ENTER na konci `Property`ho příkazu.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: deklarace a volání výchozí vlastnosti v Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
