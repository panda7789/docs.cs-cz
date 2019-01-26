---
title: 'Postupy: Použití obecné třídy (Visual Basic)'
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
ms.openlocfilehash: 4f60c0c07c0270b94dbb018b9423e210f16269d6
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065801"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Postupy: Použití obecné třídy (Visual Basic)
Třída, která přebírá *parametry typu* se volá *obecnou třídu*. Pokud používáte obecnou třídu, můžete vygenerovat *vytvořená třída* z něj zadáním *argument typu* pro každou z těchto parametrů. Pak může deklarovat proměnnou typu vytvořeného třídy, a můžete vytvořit instanci třídy konstruovaný a přiřaďte ho k proměnné.  
  
 Kromě tříd můžete také definovat a použijte obecné struktury, rozhraní, postupy a delegáti.  
  
 Následující postup používá obecné třídy definované v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a vytvoří instanci z něj.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Použít třídu, která přebírá parametr typu  
  
1.  Na začátku zdrojového souboru, patří [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) import <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. To umožňuje odkazovat <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy bez nutnosti k plnému určení ho, aby ho odlišil od jiných tříd fronty jako <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Vytvořte objekt běžným způsobem, ale přidat `(Of type)` bezprostředně za název třídy.  
  
     Následující příklad používá stejnou třídu (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) vytvořte dva objekty fronty, které obsahují položky z různých datových typů. Přidá položky do konce každou frontu a následně odebere a zobrazí položky z přední části každou frontu.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)
- [z](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Iterátory](../../../../visual-basic/programming-guide/concepts/iterators.md)
