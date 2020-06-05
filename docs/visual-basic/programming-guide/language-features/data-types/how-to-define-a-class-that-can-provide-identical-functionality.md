---
title: 'Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 3b1f47250453c32735d633b98da0bd0ddb1ed5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393854"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy (Visual Basic).
Můžete definovat třídu, ze které můžete vytvářet objekty, které poskytují stejné funkce pro různé datové typy. Chcete-li to provést, zadejte v definici jeden nebo více *parametrů typu* . Třída pak může sloužit jako šablona pro objekty, které používají různé datové typy. Třída definovaná tímto způsobem se nazývá *Obecná třída*.  
  
 Výhodou definování obecné třídy je, že ji definujete pouze jednou a váš kód jej může použít k vytvoření mnoha objektů, které používají širokou škálu datových typů. Výsledkem je lepší výkon než definování třídy s `Object` typem.  
  
 Kromě tříd můžete také definovat a používat obecné struktury, rozhraní, procedury a delegáty.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Definování třídy s parametrem typu  
  
1. Definujte třídu normálním způsobem.  
  
2. Přidejte `(Of` *typeparameter* `)` hned za název třídy pro určení parametru typu.  
  
3. Pokud máte více než jeden parametr typu, vytvořte v závorkách seznam oddělený čárkami. Klíčové slovo neopakuje `Of` .  
  
4. Pokud váš kód provádí operace s parametrem typu, který je jiný než jednoduché přiřazení, použijte tento parametr typu s `As` klauzulí k přidání jednoho nebo více *omezení*. Omezení zaručuje, že typ zadaný pro tento parametr typu splňuje požadavky, jako například následující:  
  
    - Podporuje operaci, například `>` , kterou váš kód provádí  
  
    - Podporuje člena, jako je například metoda, ke které váš kód přistupuje.  
  
    - Zpřístupňuje konstruktor bez parametrů.  
  
     Pokud nezadáte žádná omezení, mohou být použity pouze operace a členy, které váš kód podporuje, pomocí [datového typu objektu](../../../language-reference/data-types/object-data-type.md). Další informace najdete v tématu [seznam typů](../../../language-reference/statements/type-list.md).  
  
5. Identifikujte všechny členy třídy, které mají být deklarovány se zadaným typem a deklarujete je `As` `typeparameter` . To platí pro interní úložiště, parametry procedury a návratové hodnoty.  
  
6. Ujistěte se, že váš kód používá pouze operace a metody, které jsou podporovány jakýmkoli datovým typem, který může zadat `itemType` .  
  
     Následující příklad definuje třídu, která spravuje velmi jednoduchý seznam. Obsahuje seznam interního pole `items` a kód using může deklarovat datový typ prvků seznamu. Parametrizovaný konstruktor umožňuje použití kódu pro nastavení horní meze `items` a konstruktor bez parametrů nastaví tuto hodnotu na 9 (celkem 10 položek).  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     Můžete deklarovat třídu z `simpleList` , aby obsahovala seznam `Integer` hodnot, jinou třídu pro uložení seznamu `String` hodnot a další pro uložení `Date` hodnot. S výjimkou datového typu seznamů členů se objekty vytvořené ze všech těchto tříd chovají stejně.  
  
     Argument typu, který používá kód `itemType` , může být vnitřní typ, například `Boolean` nebo `Double` , struktura, výčet nebo jakýkoli typ třídy, včetně toho, který definuje vaše aplikace.  
  
     Třídu lze otestovat `simpleList` pomocí následujícího kódu.  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Obecné typy v Visual Basic](generic-types.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)
- [Tohoto](../../../language-reference/statements/of-clause.md)
- [Seznam typů](../../../language-reference/statements/type-list.md)
- [Postupy: Použití obecné třídy](how-to-use-a-generic-class.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
