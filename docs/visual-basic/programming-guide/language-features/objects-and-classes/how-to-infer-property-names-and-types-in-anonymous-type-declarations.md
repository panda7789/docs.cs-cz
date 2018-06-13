---
title: 'Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 80127c05d56162397cfa421122ddd9698750b376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653309"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a>Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu (Visual Basic)
Anonymní typy poskytují žádný mechanismus pro zadání přímo datové typy vlastností. Typy všech vlastností jsou odvodit. V následujícím příkladu, typy `Name` a `Price` jsou odvodit přímo z hodnoty, které se používají k inicializaci je.  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 Anonymní typy můžete také odvození názvů a typů z jiných zdrojů vlastností. Části obsahují seznam okolností, kde je možné odvození a příklady situací, kdy není.  
  
## <a name="successful-inference"></a>Úspěšné odvození  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a>Anonymní typy můžete odvození názvů vlastností a typů z následujících zdrojů:  
  
-   Z názvy proměnných. Anonymní typ `anonProduct` budou mít dvě vlastnosti `productName` a `productPrice`. Jejich typy dat, budou původní proměnných `String` a `Double`, v uvedeném pořadí.  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   Z vlastnost nebo pole názvy jiné objekty. Představte si třeba `car` objekt `CarClass` typ, který zahrnuje `Name` a `ID` vlastnosti. Chcete-li vytvořit novou instanci anonymního typu `car1`, s `Name` a `ID` vlastnosti, které jsou inicializovat pomocí hodnoty z `car` objekt, můžete napsat následující:  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     Předchozí deklaraci je ekvivalentní delší řádek kódu, který definuje anonymní typ `car2`.  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   Z XML názvy členů.  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     Výsledný typ pro `anon` by měla mít jednu vlastnost `Book`, typu <xref:System.Collections.IEnumerable>(XElement z).  
  
-   Z funkci, která nemá žádné parametry, jako například `SomeFunction` v následujícím příkladu.  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     Proměnná `anon2` v následujícím kódu je anonymní typ, který má jednu vlastnost s názvem znak `First`. Tento kód zobrazí písmenem "E", písmeno, kterou vrátí funkce <xref:System.Linq.Enumerable.First%2A>.  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a>Odvození selhání  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a>Název odvození selže v mnoha případech, včetně následujících:  
  
-   Odvozených odvozena z volání metody, konstruktor nebo Parametrizovaná vlastnost, která vyžaduje argumenty. Předchozí deklaraci `anon1` selže, pokud `someFunction` má jeden nebo více argumentů.  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     Přiřazení na nový název vlastnosti řeší problém.  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   Odvození je odvozena z složitý výraz.  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     Chyba lze vyřešit přiřazením výsledkem výrazu název vlastnosti.  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   Odvození pro více vlastností vytvoří dvě nebo více vlastností, které mají stejný název. Deklarace v předchozích příkladech s odvoláním zpět, je nelze zobrazit i `product.Name` a `car1.Name` jako vlastnosti anonymní stejného typu. Důvodem je, že by pro každou z nich odvozené identifikátor `Name`.  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     Tento problém lze vyřešit přiřazení hodnoty k vlastnosti jedinečné názvy.  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     Všimněte si, že se změní v případě, že (změny mezi malá a velká písmena) neprovádějte dva názvy distinct.  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   Počáteční typu a hodnoty jednu vlastnost závisí na jiné vlastnosti, která zatím nebyl určen. Například `.IDName = .LastName` není platný v deklaraci anonymního typu Pokud `.LastName` již byla inicializována.  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     V tomto příkladu lze problém vyřešit v obrácení směru, ve které jsou deklarované vlastnosti.  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   Název vlastnosti anonymního typu je stejný jako název členem <xref:System.Object>. Například následující prohlášení nezdaří, protože `Equals` je metoda <xref:System.Object>.  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     Tento problém mohli vyřešit změnou název vlastnosti:  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)
