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
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393841"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Postupy: Použití obecné třídy (Visual Basic)
Třída, která přijímá *parametry typu* , se nazývá *Obecná třída*. Pokud používáte obecnou třídu, můžete z ní vytvořit *vytvořenou třídu* zadáním *argumentu typu* pro každý z těchto parametrů. Pak můžete deklarovat proměnnou typu konstruované třídy a vytvořit instanci konstruované třídy a přiřadit ji k této proměnné.  
  
 Kromě tříd můžete také definovat a používat obecné struktury, rozhraní, procedury a delegáty.  
  
 Následující postup převezme obecnou třídu definovanou v .NET Framework a vytvoří z ní instanci.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Použití třídy, která přebírá parametr typu  
  
1. Na začátku zdrojového souboru zahrňte [příkaz Imports (obor názvů a typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) pro import <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. To vám umožní odkazovat na třídu, <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> aniž by bylo nutné plně kvalifikovat jejich rozlišení od jiných tříd fronty, jako je například <xref:System.Collections.Queue?displayProperty=nameWithType> .  
  
2. Vytvořte objekt normálním způsobem, ale přidejte `(Of type)` hned za název třídy.  
  
     Následující příklad používá stejnou třídu ( <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> ) pro vytvoření dvou objektů fronty, které obsahují položky různých datových typů. Přidá položky na konec každé fronty a pak odebere a zobrazí položky z přední části každé fronty.  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také

- [Datové typy](index.md)
- [Obecné typy v Visual Basic](generic-types.md)
- [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)
- [Tohoto](../../../language-reference/statements/of-clause.md)
- [Imports – příkaz (obor názvů a typ rozhraní .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [Iterátory](../../concepts/iterators.md)
