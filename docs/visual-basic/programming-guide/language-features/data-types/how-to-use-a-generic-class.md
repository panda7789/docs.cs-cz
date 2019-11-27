---
title: 'Postupy: Použití obecné třídy'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 87ca0da5095484615666cda505b4f7678d8160de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350063"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Postupy: Použití obecné třídy (Visual Basic)
Třída, která přijímá *parametry typu* , se nazývá *Obecná třída*. Pokud používáte obecnou třídu, můžete z ní vytvořit *vytvořenou třídu* zadáním *argumentu typu* pro každý z těchto parametrů. Pak můžete deklarovat proměnnou typu konstruované třídy a vytvořit instanci konstruované třídy a přiřadit ji k této proměnné.  
  
 Kromě tříd můžete také definovat a používat obecné struktury, rozhraní, procedury a delegáty.  
  
 Následující postup převezme obecnou třídu definovanou v .NET Framework a vytvoří z ní instanci.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Použití třídy, která přebírá parametr typu  
  
1. Na začátku zdrojového souboru zahrňte [příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pro import oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>. To vám umožňuje odkazovat na třídu <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, aniž by bylo nutné plně kvalifikovat jejich rozlišení od jiných tříd front, jako je například <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2. Vytvořte objekt normálním způsobem, ale přidejte `(Of type)` hned za název třídy.  
  
     Následující příklad používá stejnou třídu (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) k vytvoření dvou objektů fronty, které obsahují položky různých datových typů. Přidá položky na konec každé fronty a pak odebere a zobrazí položky z přední části každé fronty.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Obecné typy v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)
- [Tohoto](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Iterátory](../../../../visual-basic/programming-guide/concepts/iterators.md)
