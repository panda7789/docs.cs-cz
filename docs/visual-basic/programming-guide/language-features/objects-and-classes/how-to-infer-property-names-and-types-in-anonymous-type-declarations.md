---
title: 'Postupy: Odvození názvů vlastnosti a typů v deklaracích anonymního typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: aba8c37059cfc58fdffda55bcf1c485b61c3d249
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569489"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Postupy: Odvození názvů vlastnosti a typů v deklaracích anonymního typu (Visual Basic)
Anonymní typy umožňují žádný mechanismus pro datové typy vlastností přímo zadáním. Typy všech vlastností jsou odvozeny. V následujícím příkladu, typy `Name` a `Price` jsou odvozeny z hodnoty, které se používají k inicializaci je přímo.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 Anonymní typy lze odvodit také názvy vlastností a typy z jiných zdrojů. Následující části obsahují seznam okolností, kde je možné odvození a příklady situací, kdy není.  
  
## <a name="successful-inference"></a>Úspěšné odvození  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonymní typy lze odvodit názvy vlastností a typy z následujících zdrojů:  
  
- Z názvů proměnných. Anonymní typ `anonProduct` bude mít dvě vlastnosti `productName` a `productPrice`. Jejich datové typy, budou původní proměnných `String` a `Double`v uvedeném pořadí.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]  
  
- Vlastnost nebo pole názvů jiné objekty. Představte si třeba `car` objekt `CarClass` typ, který zahrnuje `Name` a `ID` vlastnosti. Chcete-li vytvořit novou instanci anonymního typu `car1`, s `Name` a `ID` vlastnosti, které jsou inicializovány s hodnotami z `car` objektu, můžete napsat následující:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]  
  
     Předchozí deklarace je ekvivalentní delší řádek kódu, který definuje anonymního typu `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]  
  
- Z názvů členů XML.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]  
  
     Výsledný typ pro `anon` by mít jednu vlastnost `Book`, typu <xref:System.Collections.IEnumerable>(XElement z).  
  
- Z funkce, která nemá žádné parametry, jako například `SomeFunction` v následujícím příkladu.  

  ```vb
     Dim sc As New SomeClass
     Dim anon1 = New With {Key sc.SomeFunction()}
  ```
  
     Proměnná `anon2` v následujícím kódu je anonymní typ, který má jednu vlastnost s názvem znak `First`. Tento kód zobrazí písmeno "E", písmeno, kterou vrátí funkce <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]  
  
## <a name="inference-failures"></a>Odvození selhání  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Název odvození se nezdaří v mnoha případech platí, včetně následujících:  
  
- Odvození je odvozena z volání metody, konstruktor nebo parametrizovanou vlastnost, která vyžaduje argumenty. Předchozí deklarace této třídy `anon1` selže, pokud `someFunction` má jeden nebo více argumentů.  

    ```vb
    ' Not valid.
    ' Dim anon3 = New With {Key sc.someFunction(someArg)}
    ```
    
     Přiřazení na nový název vlastnosti byl problém vyřešen.  

    ```vb
    ' Valid.
    Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
    ```

- Odvození je odvozena z složitý výraz.  
  
    ```vb  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     Chybu lze vyřešit tak, že přiřadíte výsledek výrazu název vlastnosti.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]  
  
- Odvození pro více vlastností vytvoří dva nebo více vlastností, které mají stejný název. Odkazující zpět na deklarace v předchozích příkladech, vás není možné vypsat obě `product.Name` a `car1.Name` jako vlastnosti anonymního typu. Důvodem je, že by být odvozené identifikátor pro každou z těchto `Name`.  

     ```vb
     ' Not valid.
     ' Dim anon5 = New With {Key product.Name, Key car1.Name}
     ```
     
     Tento problém lze vyřešit přiřazení hodnoty k vlastnosti odlišné názvy.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]  
  
     Všimněte si, že změny v případě, že (změny se mezi velkými a malými písmeny) Nedovolte, aby byly dva názvy distinct.  

     ```vb
     Dim price = 0
     ' Not valid, because Price and price are the same name.
     ' Dim anon7 = New With {Key product.Price, Key price}
     ```
  
- Počáteční typ a hodnotu jednu vlastnost závisí na jiné vlastnosti, která zatím nebyl určen. Například `.IDName = .LastName` není platný v deklaraci anonymního typu není-li `.LastName` již byl inicializován.  

     ```vb
     ' Not valid.
     ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
     ```
     
     V tomto příkladu můžete opravit problém přehozením pořadí, ve kterém jsou deklarovány vlastnosti.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]  
  
- Název vlastnosti anonymního typu je stejný jako název člena <xref:System.Object>. Například následující deklaraci selže, protože `Equals` je metoda <xref:System.Object>.  
  
     ```vb
     ' Not valid.
     ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
     '                       "greater than", Key .Less = "less than"}
     ```
     
     Problém můžete vyřešit tak, že změníte název vlastnosti:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
