---
title: 'Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 5bd4e0a760bcedf8f5e96c2cebe3a71b9050a420
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582283"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu (Visual Basic)

Anonymní typy neposkytují žádný mechanismus pro přímé určení datových typů vlastností. Typy všech vlastností jsou odvozeny. V následujícím příkladu jsou typy `Name` a `Price` odvozeny přímo z hodnot, které jsou použity k jejich inicializaci.

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

Anonymní typy mohou také odvodit názvy vlastností a typy z jiných zdrojů. Níže uvedené části obsahují seznam případů, ve kterých je odvozeno odvozování, a příklady situací, kdy není možné.

## <a name="successful-inference"></a>Úspěšné odvození

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonymní typy mohou odvodit názvy vlastností a typy z následujících zdrojů:

- Z názvů proměnných. @No__t_0 anonymního typu budou mít dvě vlastnosti, `productName` a `productPrice`. Jejich datové typy budou ty z původních proměnných, `String` a `Double`, v uvedeném pořadí.

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- Z vlastností nebo názvů polí jiných objektů. Zvažte například `car` objekt `CarClass` typu, který obsahuje vlastnosti `Name` a `ID`. Chcete-li vytvořit novou instanci anonymního typu `car1`, s `Name` a `ID` vlastnosti, které jsou inicializovány s hodnotami z objektu `car`, můžete zapsat následující:

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  Předchozí deklarace je ekvivalentní s delším řádkem kódu, který definuje anonymní typ `car2`.

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- Z názvů členů XML.

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  Výsledný typ pro `anon` by měl mít jednu vlastnost `Book` typu <xref:System.Collections.IEnumerable> (Of XElement).

- Z funkce, která nemá žádné parametry, například `SomeFunction` v následujícím příkladu.

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  Proměnná `anon2` v následujícím kódu je anonymní typ, který má jednu vlastnost, znak nazvaný `First`. Tento kód zobrazí písmeno "E", které je vráceno funkcí <xref:System.Linq.Enumerable.First%2A>.

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a>Selhání odvození

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Odvození názvu selže v mnoha případech, včetně následujících:

- Odvození je odvozeno od vyvolání metody, konstruktoru nebo parametrizované vlastnosti, která vyžaduje argumenty. Předchozí deklarace `anon1` se nezdařila, pokud `someFunction` jeden nebo více argumentů.

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  Přiřazení k novému názvu vlastnosti tento problém vyřeší.

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- Odvození je odvozeno od složitého výrazu.

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  Chybu lze vyřešit přiřazením výsledku výrazu k názvu vlastnosti.

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- Odvození pro více vlastností vytváří dvě nebo více vlastností, které mají stejný název. Odkazy zpět na deklarace v předchozích příkladech nemůžete uvést `product.Name` a `car1.Name` jako vlastnosti stejného anonymního typu. Důvodem je, že odvozený identifikátor každého z nich by byl `Name`.

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  Problém lze vyřešit přiřazením hodnot k jedinečným názvům vlastností.

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  Všimněte si, že změny v případě (změny mezi velkými a malými písmeny) nedělají dva názvy odlišně.

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- Počáteční typ a hodnota jedné vlastnosti závisí na jiné vlastnosti, která ještě není navázána. Například `.IDName = .LastName` není platný v deklaraci anonymního typu, pokud není `.LastName` již inicializována.

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  V tomto příkladu lze problém vyřešit zrušením pořadí, ve kterém jsou vlastnosti deklarovány.

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- Název vlastnosti anonymního typu je stejný jako název členu <xref:System.Object>. Například následující deklarace se nezdařila, protože `Equals` je metoda <xref:System.Object>.

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  Problém můžete vyřešit tak, že změníte název vlastnosti:

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a>Viz také:

- [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
