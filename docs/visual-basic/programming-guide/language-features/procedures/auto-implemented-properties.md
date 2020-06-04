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
ms.openlocfilehash: d991a385e537c43daeb708e96e712acd92110379
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403379"
---
# <a name="auto-implemented-properties-visual-basic"></a>Automaticky implementované vlastnosti (Visual Basic)
*Automaticky implementované vlastnosti* umožňují rychle zadat vlastnost třídy bez nutnosti psát kód do `Get` a `Set` Vlastnosti. Při psaní kódu pro automaticky implementovanou vlastnost automaticky vytvoří kompilátor Visual Basic privátní pole pro uložení proměnné vlastnosti kromě vytvoření přidružených `Get` a `Set` postupů.  
  
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
 Pokud deklarujete automaticky implementovanou vlastnost, Visual Basic automaticky vytvoří skryté soukromé pole s názvem *pole zálohování* , které obsahuje hodnotu vlastnosti. Název záložního pole je název automaticky implementované vlastnosti předchází podtržítkem (_). Například pokud deklarujete automaticky implementovanou vlastnost s názvem `ID` , pole pro zálohování je pojmenované `_ID` . Pokud zahrnete člena vaší třídy, která je také pojmenována `_ID` , dojde k vytvoření konfliktu pojmenování a Visual Basic hlásí chybu kompilátoru.  
  
 Pole pro zálohování má také následující vlastnosti:  
  
- Modifikátor přístupu pro pole pro zálohování je vždy `Private` , i když má sama vlastnost jinou úroveň přístupu, například `Public` .  
  
- Je-li vlastnost označena jako `Shared` , je sdíleno také pole zálohování.  
  
- Atributy zadané pro vlastnost se nevztahují na pole pro zálohování.  
  
- K poli pro zálohování se dá dostat z kódu v rámci třídy a z ladicích nástrojů, jako je okno Kukátko. Pole zálohování se ale nezobrazí v seznamu dokončování slov IntelliSense.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializuje se automaticky implementovaná vlastnost.  
 Libovolný výraz, který lze použít k inicializaci pole, je platný pro inicializaci automaticky implementované vlastnosti. Při inicializaci automaticky implementované vlastnosti je výraz vyhodnocen a předán do `Set` procedury pro vlastnost. Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které obsahují počáteční hodnoty.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Nelze inicializovat automaticky implementovanou vlastnost, která je členem třídy `Interface` nebo která je označena jako `MustOverride` .  
  
 Pokud deklarujete automaticky implementovanou vlastnost jako člen a `Structure` , můžete pouze inicializovat automaticky implementovanou vlastnost, pokud je označena jako `Shared` .  
  
 Pokud deklarujete automaticky implementovanou vlastnost jako pole, nemůžete zadat explicitní meze pole. Můžete však dodat hodnotu pomocí inicializátoru pole, jak je znázorněno v následujících příkladech.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definice vlastností, které vyžadují standardní syntaxi  
 Automaticky implementované vlastnosti jsou pohodlné a podporují řadu programovacích scénářů. Existují však situace, kdy nemůžete použít automaticky implementovanou vlastnost a místo toho je třeba použít standardní nebo *rozbalenou*syntaxi vlastností.  
  
 Pokud chcete provést některou z následujících akcí, je nutné použít rozšířenou syntaxi definice vlastností:  
  
- Přidejte kód do `Get` procedury nebo pro `Set` vlastnost, jako je například kód pro ověření příchozích hodnot v `Set` proceduře. Například může být vhodné ověřit, že řetězec představující telefonní číslo obsahuje požadovaný počet číslic před nastavením hodnoty vlastnosti.  
  
- Zadejte pro `Get` proceduru a jinou přístupnost `Set` . Například může být vhodné provést `Set` postup `Private` a `Get` postup `Public` .  
  
- Vytvořte vlastnosti, které jsou `WriteOnly` .  
  
- Použijte parametrizované vlastnosti (včetně `Default` vlastností). Aby bylo možné zadat parametr pro vlastnost nebo zadat další parametry pro proceduru, je nutné deklarovat rozšířenou vlastnost `Set` .  
  
- Umístěte atribut do pole zálohování nebo změňte úroveň přístupu v poli pro zálohování.  
  
- Zadejte komentáře XML pro pole zálohování.  
  
## <a name="expanding-an-auto-implemented-property"></a>Rozšíření automaticky implementované vlastnosti  
 Pokud je nutné převést automaticky implementovanou vlastnost na rozšířenou vlastnost, která obsahuje `Get` `Set` proceduru or, Editor kódu Visual Basic může automaticky generovat `Get` `Set` procedury a `End Property` příkazy pro vlastnost. Kód je generován při vložení kurzoru do prázdného řádku po `Property` příkazu, zadejte a `G` (pro `Get` ) nebo `S` (pro `Set` ) a stiskněte klávesu ENTER. Editor kódu Visual Basic automaticky generuje `Get` `Set` proceduru nebo pro vlastnosti jen pro čtení a jen pro zápis při stisknutí klávesy ENTER na konci `Property` příkazu.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property – příkaz](../../../language-reference/statements/property-statement.md)
- [ReadOnly](../../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Objekty a třídy](../objects-and-classes/index.md)
