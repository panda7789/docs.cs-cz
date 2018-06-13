---
title: 'Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy (Visual Basic).'
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
ms.openlocfilehash: 3570a1c851bb8fead33f4cd208489c4ae087a68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650345"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy (Visual Basic).
Můžete definice třídy, ze kterého můžete vytvořit objekty, které poskytují identické funkce pro různé datové typy. K tomuto účelu můžete zadat jednu nebo několik *parametry typu* v definici. Třída může pak sloužit jako šablona pro objekty, které používají různé datové typy. Třídy definované tímto způsobem se nazývá *– obecná třída*.  
  
 Výhodou definování obecné třídy je, že definujete jen jednou a váš kód můžete použít k vytvoření mnoho objektů, které používají širokou škálu datové typy. To vede k lepší výkon než definice třídy s `Object` typu.  
  
 Kromě třídy můžete také definovat a použít obecné struktury, rozhraní, postupy a delegáti.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Chcete-li definovat třídu s parametrem typu  
  
1.  Definujte třídu běžným způsobem.  
  
2.  Přidat `(Of` *typeparameter* `)` ihned po název třídy pro určení typu parametru.  
  
3.  Pokud máte více než jeden parametr typu, vytvořte seznam oddělený čárkami do závorek. Neopakujte `Of` – klíčové slovo.  
  
4.  Pokud váš kód provádí operace pro parametr typu než jednoduché přiřazení, použijte tento parametr typu s `As` klauzule chcete přidat jeden nebo více *omezení*. Omezení zaručuje, že typ zadaný pro parametr typu splňuje požadavek například následující:  
  
    -   Podporuje operace, jako například `>`, který provádí kódu  
  
    -   Podporuje členem, jako je například metoda, který přistupuje k kódu  
  
    -   Zpřístupní konstruktor bez parametrů  
  
     Pokud nezadáte žádné omezení, jenom operace a členy můžete použít kódu jsou jsou podporovány [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md). Další informace najdete v tématu [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Identifikovat každých třída člena, který je třeba deklarovat s zadaný typ a deklarujte ji `As` `typeparameter`. To platí pro interní úložiště, postup parametry a návratové hodnoty.  
  
6.  Ujistěte se, váš kód používá jenom operace a metody, které jsou podporovány všechny datový typ, můžete zadat do `itemType`.  
  
     Následující příklad definuje třídu, která spravuje seznam velmi jednoduché. V poli interní drží seznamu `items`a pomocí kódu můžou deklarovat datový typ seznamu elementů. Parametrizované konstruktor umožňuje použití kódu nastavit horní mez `items`, a nastaví výchozí konstruktor, to do 9 (pro celkem 10 položek).  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Je možné deklarovat vytvoření třídy z `simpleList` pro uložení seznamu `Integer` hodnoty, jiné třídy pro uložení seznamu `String` hodnoty a druhý pro uložení `Date` hodnoty. S výjimkou datový typ ze seznamu členů chovají stejně jako objekty vytvořené z těchto tříd.  
  
     Argument typu, který pomocí kódu poskytuje `itemType` může být například vnitřního typu `Boolean` nebo `Double`, struktury, výčet nebo libovolného typu třídy, včetně ten, který definuje vaší aplikace.  
  
     Můžete otestovat třída `simpleList` následujícím kódem.  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)  
 [z](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Seznam typů](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Postupy: Použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
