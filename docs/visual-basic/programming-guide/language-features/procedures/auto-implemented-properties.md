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
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656311"
---
# <a name="auto-implemented-properties-visual-basic"></a>Automaticky implementované vlastnosti (Visual Basic)
*Automaticky implementované vlastnosti* vám umožní rychle určit vlastnost třídy bez nutnosti psaní kódu pro `Get` a `Set` vlastnost. Při psaní kódu automaticky implementované vlastnosti, Visual Basic – kompilátor automaticky vytvoří privátní pole pro uložení proměnné vlastnost kromě vytváření přidruženého `Get` a `Set` postupy.  
  
 S automaticky implementované vlastnosti vlastnosti, včetně výchozí hodnotu, lze deklarovat na jednom řádku. Následující příklad ukazuje tři vlastnosti deklarací.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 Ve automaticky implementované vlastnosti je stejná jako vlastnost, pro kterou je hodnota vlastnosti uložené v soukromé pole. Následující příklad kódu ukazuje ve automaticky implementované vlastnosti.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 Následující příklad kódu ukazuje kód ekvivalentní pro předchozí příklad automaticky implementované vlastnosti.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 Následující kód zobrazit implementace vlastnosti jen pro čtení:  
  
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
  
 Můžete přiřadit k vlastnosti s inicializace výrazy, jak je znázorněno v příkladu, nebo můžete přiřadit k vlastnosti v konstruktoru obsahující typu.  Kdykoli můžete přiřadit na pole základní vlastnosti jen pro čtení.  
  
## <a name="backing-field"></a>Základní pole  
 Když je deklarovat ve automaticky implementované vlastnosti, Visual Basic automaticky vytvoří privátní skrytá pole s názvem *základní pole* tak, aby obsahovala hodnotu vlastnosti. Název pole nástroje zálohování je název automaticky implementované vlastnosti sebou podtržítko (_). Například, pokud je deklarovat ve automaticky implementované vlastnosti s názvem `ID`, má název pole Základní `_ID`. Pokud zahrnete člena třídy, který je také název `_ID`, můžete vytvořit ke konfliktu názvů a hlásí chyby kompilátoru jazyka Visual Basic.  
  
 Pole Základní také má následující vlastnosti:  
  
-   Modifikátor přístupu pro pole zálohování je vždy `Private`, i když samotné vlastnosti má úroveň různý přístup, jako například `Public`.  
  
-   Pokud je vlastnost označena jako `Shared`, také sdílet pole zálohování.  
  
-   Zadané atributy pro vlastnost se nevztahují na základní pole.  
  
-   Základní pole jsou přístupné z kódu v rámci třídy a ladění nástrojů, jako je okno kukátka. Pole Základní se však nezobrazuje v seznamu dokončení IntelliSense aplikace word.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicializace ve automaticky implementované vlastnosti  
 Jakýkoli výraz, který slouží k inicializaci pole je platný pro inicializaci ve automaticky implementované vlastnosti. Při inicializaci ve automaticky implementované vlastnosti je výraz vyhodnocen a předán `Set` postup pro vlastnost. Následující příklady kódu ukazují některé automaticky implementované vlastnosti, které zahrnují počáteční hodnoty.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 Nelze inicializovat ve automaticky implementované vlastnosti, který je členem skupiny `Interface`, nebo takové, která je označena `MustOverride`.  
  
 Když je deklarovat ve automaticky implementované vlastnosti jako člen skupiny `Structure`, automaticky implementované vlastnosti můžete inicializovat pouze pokud je označen jako `Shared`.  
  
 Po deklarování ve automaticky implementované vlastnosti jako pole, nemůžete zadat explicitní pole hranice. Můžete však zadat hodnotu pomocí inicializátoru pole, podle následujících příkladů.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definice vlastností, které vyžadují standardní syntaxe  
 Automaticky implementované vlastnosti jsou pohodlný a podporují mnoho scénáře programování. Existují však situace, ve kterých nelze použít ve automaticky implementované vlastnosti a místo toho musíte použít standard, nebo *rozšířit*, vlastnost syntaxe.  
  
 Budete muset použít rozšířené definici vlastnosti syntaxe, pokud budete chtít provést jednu z těchto možností:  
  
-   Přidejte kód, který `Get` nebo `Set` postup vlastnosti, jako je například kódu k ověření příchozích hodnot v `Set` postupu. Například můžete chtít ověřte, že řetězec, který představuje telefonní číslo obsahuje požadovaný počet číslic před nastavením hodnoty vlastnosti.  
  
-   Zadejte jiný usnadnění pro `Get` a `Set` postupu. Například můžete chtít provést `Set` postup `Private` a `Get` postup `Public`.  
  
-   Vytvoření vlastnosti, které jsou `WriteOnly`.  
  
-   Použití parametrizovaného vlastností (včetně `Default` vlastnosti). Je potřeba deklarovat rozšířené vlastnosti za účelem zadejte parametr pro vlastnost, nebo k zadání dalších parametrů pro `Set` postupu.  
  
-   Umístit na pole Základní atribut, nebo změnit úroveň přístupu tohoto pole zálohování.  
  
-   Zadejte XML – komentáře pro pole zálohování.  
  
## <a name="expanding-an-auto-implemented-property"></a>Rozšíření ve automaticky implementované vlastnosti  
 Pokud máte ve automaticky implementované vlastnosti převést na rozšířené vlastnosti, která obsahuje `Get` nebo `Set` postupu editoru kódu jazyka Visual Basic může automaticky generovat `Get` a `Set` procedury a `End Property`příkaz Vlastnosti. Pokud umístěte kurzor na prázdný řádek následující vygenerování kódu `Property` příkazu, zadejte `G` (pro `Get`) nebo `S` (pro `Set`) a stiskněte klávesu ENTER. Automaticky generuje editoru kódu jazyka Visual Basic `Get` nebo `Set` postup pro vlastnosti jen pro čtení a jen pro zápis po stisknutí klávesy ENTER na konci `Property` příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
