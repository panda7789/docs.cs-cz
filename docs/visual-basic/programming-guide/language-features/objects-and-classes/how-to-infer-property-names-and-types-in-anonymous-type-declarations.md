---
title: 'Postupy: Odvození názvů vlastnosti a typů v deklaracích anonymního typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 67cc9e85d249365a7b4b7636c99766087314622d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596854"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Postupy: Odvození názvů vlastnosti a typů v deklaracích anonymního typu (Visual Basic)
Anonymní typy umožňují žádný mechanismus pro datové typy vlastností přímo zadáním. Typy všech vlastností jsou odvozeny. V následujícím příkladu, typy `Name` a `Price` jsou odvozeny z hodnoty, které se používají k inicializaci je přímo.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 Anonymní typy lze odvodit také názvy vlastností a typy z jiných zdrojů. Následující části obsahují seznam okolností, kde je možné odvození a příklady situací, kdy není.  
  
## <a name="successful-inference"></a>Úspěšné odvození  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonymní typy lze odvodit názvy vlastností a typy z následujících zdrojů:  
  
-   Z názvů proměnných. Anonymní typ `anonProduct` bude mít dvě vlastnosti `productName` a `productPrice`. Jejich datové typy, budou původní proměnných `String` a `Double`v uvedeném pořadí.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   Vlastnost nebo pole názvů jiné objekty. Představte si třeba `car` objekt `CarClass` typ, který zahrnuje `Name` a `ID` vlastnosti. Chcete-li vytvořit novou instanci anonymního typu `car1`, s `Name` a `ID` vlastnosti, které jsou inicializovány s hodnotami z `car` objektu, můžete napsat následující:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     Předchozí deklarace je ekvivalentní delší řádek kódu, který definuje anonymního typu `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   Z názvů členů XML.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     Výsledný typ pro `anon` by mít jednu vlastnost `Book`, typu <xref:System.Collections.IEnumerable>(XElement z).  
  
-   Z funkce, která nemá žádné parametry, jako například `SomeFunction` v následujícím příkladu.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     Proměnná `anon2` v následujícím kódu je anonymní typ, který má jednu vlastnost s názvem znak `First`. Tento kód zobrazí písmeno "E", písmeno, kterou vrátí funkce <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a>Odvození selhání  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Název odvození se nezdaří v mnoha případech platí, včetně následujících:  
  
-   Odvození je odvozena z volání metody, konstruktor nebo parametrizovanou vlastnost, která vyžaduje argumenty. Předchozí deklarace této třídy `anon1` selže, pokud `someFunction` má jeden nebo více argumentů.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Přiřazení na nový název vlastnosti byl problém vyřešen.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   Odvození je odvozena z složitý výraz.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     Chybu lze vyřešit tak, že přiřadíte výsledek výrazu název vlastnosti.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   Odvození pro více vlastností vytvoří dva nebo více vlastností, které mají stejný název. Odkazující zpět na deklarace v předchozích příkladech, vás není možné vypsat obě `product.Name` a `car1.Name` jako vlastnosti anonymního typu. Důvodem je, že by být odvozené identifikátor pro každou z těchto `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     Tento problém lze vyřešit přiřazení hodnoty k vlastnosti odlišné názvy.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     Všimněte si, že změny v případě, že (změny se mezi velkými a malými písmeny) Nedovolte, aby byly dva názvy distinct.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   Počáteční typ a hodnotu jednu vlastnost závisí na jiné vlastnosti, která zatím nebyl určen. Například `.IDName = .LastName` není platný v deklaraci anonymního typu není-li `.LastName` již byl inicializován.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     V tomto příkladu můžete opravit problém přehozením pořadí, ve kterém jsou deklarovány vlastnosti.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   Název vlastnosti anonymního typu je stejný jako název člena <xref:System.Object>. Například následující deklaraci selže, protože `Equals` je metoda <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Problém můžete vyřešit tak, že změníte název vlastnosti:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Key](../../../../visual-basic/language-reference/modifiers/key.md)
