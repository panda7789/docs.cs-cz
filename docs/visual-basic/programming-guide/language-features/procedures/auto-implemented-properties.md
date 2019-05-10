---
title: Automaticky implementované vlastnosti (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: 4577609c78271ac91e011b20ef6a8b4066072428
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649669"
---
# <a name="auto-implemented-properties-visual-basic"></a>Automaticky implementované vlastnosti (Visual Basic)
*Automaticky implementované vlastnosti* vám umožní rychle určit vlastnost třídy, aniž byste museli napsat kód, který `Get` a `Set` vlastnost. Při psaní kódu pro automaticky implementovanou vlastnost kompilátor jazyka Visual Basic automaticky vytvoří soukromé pole k uložení proměnné vlastnost kromě vytvoření přidružený `Get` a `Set` postupy.  
  
 S automaticky implementovanými vlastnostmi lze deklarovat vlastnosti, včetně výchozí hodnotu, na jednom řádku. Následující příklad ukazuje tři vlastnosti deklarací.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Automaticky implementované vlastnosti je ekvivalentní k vlastnosti, kterou je uložená hodnota vlastnosti v soukromé pole. Následující příklad kódu ukazuje automaticky implementované vlastnosti.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 Následující příklad kódu ukazuje odpovídající kód z předchozího příkladu automaticky implementované vlastnosti.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 Následující kód zobrazí implementace vlastnosti jen pro čtení:  
  
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
  
 Můžete přiřadit k vlastnosti s výrazy inicializace, jak je znázorněno v příkladu, nebo můžete přiřadit k vlastnosti v konstruktoru nadřazeného typu.  Kdykoli můžete přiřadit do pole základní vlastnosti jen pro čtení.  
  
## <a name="backing-field"></a>Zálohovací položka  
 Při deklaraci automaticky implementovaná vlastnost jazyka Visual Basic automaticky vytvoří skrytou privátní pole s názvem *pomocné pole* tak, aby obsahovala hodnotu vlastnosti. Název pomocné pole je název automaticky implementované vlastnosti začínající podtržítkem (_). Například, pokud deklarujete automaticky implementovaná vlastnost s názvem `ID`, se s pomocným polem názvem `_ID`. Pokud zahrnete člena vaší třídy, která se také nazývá `_ID`, vytvářejí konfliktu názvů a Visual Basic hlásí chybu kompilátoru.  
  
 Pomocné pole také má následující vlastnosti:  
  
- Modifikátor přístupu pro pomocné pole je vždy `Private`, i když samotné vlastnosti má úroveň různý přístup, jako například `Public`.  
  
- Pokud je vlastnost označená jako `Shared`, také sdílet pomocným polem.  
  
- Atributy určené pro vlastnost se nevztahují na pomocné pole.  
  
- Pomocné pole jsou přístupné z kódu v rámci třídy a ladicí nástroje, jako jsou okna kukátka. Pomocné pole není uveden v seznamu pro doplňování slov technologie IntelliSense.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializuje se automaticky implementované vlastnosti  
 Libovolný výraz, který slouží k inicializaci pole je platný pro inicializaci automaticky implementované vlastnosti. Při inicializaci automaticky implementované vlastnosti výraz je vyhodnocen a předat `Set` postup pro vlastnost. Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které obsahují počáteční hodnoty.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Nelze inicializovat automaticky implementované vlastnosti, který je členem `Interface`, nebo disk, který je označen `MustOverride`.  
  
 Pokud deklarujete automaticky implementované vlastnosti jako člen `Structure`, automaticky implementované vlastnosti lze inicializovat pouze pokud je označen jako `Shared`.  
  
 Když deklarujete automaticky implementované vlastnosti jako pole, nelze zadat explicitní pole hranice. Můžete však zadat hodnotu pomocí inicializátoru pole, jak je znázorněno v následujícím příkladu.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definice vlastností, které vyžadují standardní syntaxe  
 Automaticky implementované vlastnosti jsou pohodlný a podporují řadu programovacích scénářů. Existují však situace, kdy nejde používat automaticky implementované vlastnosti a musíte místo toho použít standardní, nebo *rozšířit*, syntaxe vlastnosti.  
  
 Budete muset použít syntaxe rozšířené definici vlastnosti, pokud chcete provádět žádnou z následujících akcí:  
  
- Přidejte kód, který `Get` nebo `Set` procedury vlastnosti, jako je například kód pro ověření příchozích hodnot v `Set` postup. Například můžete chtít ověřit, jestli řetězec, který představuje telefonní číslo obsahuje požadovaný počet číslic než nastavení hodnoty vlastnosti.  
  
- Zadejte jiný usnadnění pro `Get` a `Set` postup. Například můžete chtít provést `Set` postup `Private` a `Get` postup `Public`.  
  
- Vytvoření vlastnosti, které jsou `WriteOnly`.  
  
- Použití parametrizovaného vlastností (včetně `Default` vlastnosti). Rozšířené vlastnosti musí deklarovat, pokud chcete zadat parametr pro vlastnost, nebo k zadání dalších parametrů pro `Set` postup.  
  
- Umístit atribut na pomocné pole nebo změnit úroveň přístupu pomocným polem.  
  
- Komentáře XML zadejte pro pole zálohování.  
  
## <a name="expanding-an-auto-implemented-property"></a>Automaticky implementované vlastnosti rozšíření  
 Pokud budete muset převést na rozšířenou vlastnost, která obsahuje automaticky implementované vlastnosti `Get` nebo `Set` postupu, Editor kódu jazyka Visual Basic můžete automaticky vygenerovat `Get` a `Set` postupy a `End Property`příkaz Vlastnosti. Kód je generována, pokud umístěte kurzor na prázdný řádek následující `Property` příkazu, zadejte `G` (pro `Get`) nebo `S` (pro `Set`) a stiskněte klávesu ENTER. Editor kódu jazyka Visual Basic generuje automaticky `Get` nebo `Set` postup pro vlastnosti jen pro čtení a jen pro zápis při stisknutí klávesy ENTER na konci `Property` příkazu.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
