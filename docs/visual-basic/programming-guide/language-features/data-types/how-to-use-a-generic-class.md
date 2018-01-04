---
title: "Postupy: Použití obecné třídy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 168e5c7f7d144d5c20513d62f4e3458bc6f87235
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-a-generic-class-visual-basic"></a>Postupy: Použití obecné třídy (Visual Basic)
Třída, která přebírá *parametry typu* nazývá *– obecná třída*. Pokud používáte obecné třídy, můžete vygenerovat *sestavený třída* z něj zadáním *argument typu* pro každou z těchto parametrů. Potom můžete deklarovat proměnnou typu sestavené třídy a můžete vytvořit instance třídy vytvořený a přiřadit ji k této proměnné.  
  
 Kromě třídy můžete také definovat a použít obecné struktury, rozhraní, postupy a delegáti.  
  
 Následující postup trvá obecné třídy definované v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a vytvoří instanci z něj.  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>Použití třídy, která přebírá parametr typu  
  
1.  Na začátku zdrojový soubor, patří [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) k importu <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů. To umožňuje odkazovat <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třída bez nutnosti k plnému určení ho k odlišení certifikátu od jiné třídy fronty, jako <xref:System.Collections.Queue?displayProperty=nameWithType>.  
  
2.  Vytvořit objekt běžným způsobem, ale přidat `(Of` `type``)` ihned po název třídy.  
  
     Následující příklad používá stejnou třídu (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) k vytvoření dvou objektů fronty, které mají různé datové typy položky. Přidá na konec každé fronty položky a poté odstraní a zobrazí položky z před každou frontu.  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md)  
 [Z](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Postupy: Definice třídy, která poskytne identické funkce pro různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [Iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
