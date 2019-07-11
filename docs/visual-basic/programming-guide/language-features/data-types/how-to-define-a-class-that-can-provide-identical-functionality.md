---
title: 'Postupy: Definujte třídu, která poskytne identické funkce pro různé datové typy (Visual Basic)'
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
ms.openlocfilehash: 19988e766d0f9ec895a24dddfcd17d0854aaf8ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757393"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Postupy: Definujte třídu, která poskytne identické funkce pro různé datové typy (Visual Basic)
Můžete definovat třídu z které můžete vytvořit objekty, které poskytne identické funkce pro různé datové typy. K tomuto účelu můžete zadat jednu nebo víc *parametry typu* v definici. Třída pak může sloužit jako šablona pro objekty, které používají různé datové typy. Třída definována tímto způsobem se nazývá *obecnou třídu*.  
  
 Výhodou definování obecné třídy je, že definujete pouze jednou a váš kód můžete použít k vytvoření mnoho objektů, které používají širokou škálu datových typů. Výsledkem je lepší výkon než definováním třídy s `Object` typu.  
  
 Kromě tříd můžete také definovat a použijte obecné struktury, rozhraní, postupy a delegáti.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Chcete-li definovat třídu s parametrem typu  
  
1. Definování třídy obvyklým způsobem.  
  
2. Přidat `(Of` *typeparameter* `)` bezprostředně za název třídy pro zadání parametru typu.  
  
3. Pokud máte více než jeden parametr typu, vytvořte seznam oddělený čárkami v závorkách. Neopakovat `Of` – klíčové slovo.  
  
4. Pokud váš kód provádí operace u parametru typu jiného než jednoduché přiřazení, použijte tento parametr typu `As` klauzule, které chcete přidat jeden nebo více *omezení*. Omezení zaručuje, že na typ zadaný pro parametr typu splňuje požadavek, jako je následující:  
  
    - Podporuje operace, jako například `>`, který váš kód provádí  
  
    - Podporuje členu, například metody, které váš kód přistupuje k  
  
    - Zpřístupňuje konstruktor bez parametrů  
  
     Pokud nezadáte žádné omezení, pouze konzole operations Console a váš kód může použít členy jsou jsou podporovány [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). Další informace najdete v tématu [seznam typů](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5. Každý člen třídy, který je deklarován s zadaný typ identifikovat a deklarujte ji `As` `typeparameter`. To platí pro interní úložiště, postup parametrů a návratové hodnoty.  
  
6. Ujistěte se, váš kód používá pouze operace a metody, které jsou podporovány libovolného datového typu, mohou poskytnout `itemType`.  
  
     Následující příklad definuje třídu, která spravuje velmi jednoduchý seznam. Obsahuje seznam v poli interní `items`a pomocí kódu můžete deklarovat typ dat prvků seznamu. Umožňuje do parametrizovaného konstruktoru na pomocí kódu pro nastavení horní mez `items`, a to nastavuje konstruktor bez parametrů 9 (pro celkem 10 položek).  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     Je možné deklarovat třídu z `simpleList` k uložení seznamu `Integer` hodnoty, jiné třídy pro uložení seznamu `String` hodnoty a druhý pro uložení `Date` hodnoty. S výjimkou datový typ seznam členů chovají stejně jako objekty vytvořené z těchto tříd.  
  
     Argument typu, který pomocí kódu poskytuje `itemType` vnitřní typ může být například `Boolean` nebo `Double`, strukturu, výčet nebo libovolný typ třídy, včetně ten, který definuje vaše aplikace.  
  
     Třídu můžete otestovat `simpleList` následujícím kódem.  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)
- [z](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Seznam typů](../../../../visual-basic/language-reference/statements/type-list.md)
- [Postupy: Použití obecné třídy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
