---
title: Inicializátory kolekcí (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ec0179df50df453d6058a4b910d17561394140d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="collection-initializers-visual-basic"></a>Inicializátory kolekcí (Visual Basic)
*Inicializátory kolekcí* poskytují zkrácenou syntaxi, která umožňuje vytvořit kolekci a jeho naplnění počáteční sadu hodnot. Inicializátory kolekce jsou užitečné, když vytváříte kolekci ze sady známé hodnoty, například seznam možností v nabídce nebo kategorie, počáteční sadu číselných hodnot, seznam řetězců, jako je například den nebo měsíc názvy nebo zeměpisné umístění, jako statické seznam stavů, který se používá pro ověření.  
  
 Další informace o kolekcích najdete v tématu [kolekce](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b).  
  
 Identifikovat inicializátoru kolekce pomocí `From` – klíčové slovo, za nímž následuje složené závorky (`{}`). Toto je podobná syntaxi literálu pole, která je popsána v [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Následující příklady ukazují různé způsoby použití inicializátory kolekce k vytvoření kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]  
  
> [!NOTE]
>  C# taky poskytuje Inicializátory kolekcí. Inicializátory kolekcí C# poskytovat stejné funkce jako Inicializátory kolekcí jazyka Visual Basic. Další informace o C# Inicializátory kolekcí najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="syntax"></a>Syntaxe  
 Inicializátory kolekce sestává ze seznamu hodnot oddělených čárkami, které jsou uzavřené do složených závorek (`{}`), předcházet `From` – klíčové slovo, jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]  
  
 Když vytvoříte kolekci, například <xref:System.Collections.Generic.List%601> nebo <xref:System.Collections.Generic.Dictionary%602>, je nutné zadat typ kolekce před inicializátoru kolekce, jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]  
  
> [!NOTE]
>  Nelze kombinovat inicializátoru kolekce a inicializátoru objektu inicializovat stejného objektu kolekce. Inicializátory objektů můžete použít třeba inicializovat objekty v inicializátoru kolekce.  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a>Vytvoření kolekce pomocí Intializer kolekce  
 Při vytváření kolekce pomocí inicializátoru kolekce, každá hodnota, která se dodává v inicializátoru kolekce je předán na příslušné `Add` metody kolekce. Například pokud vytvoříte <xref:System.Collections.Generic.List%601> pomocí inicializátoru kolekce každý řetězcová hodnota v kolekci inicializátoru předaný <xref:System.Collections.Generic.List%601.Add%2A> metoda. Pokud chcete vytvořit kolekci pomocí inicializátoru kolekce, zadaný typ musí být typ platný kolekce. Příklady typů platnou kolekci třídy, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní, nebo nastavte dědičnost <xref:System.Collections.CollectionBase> třídy. Zadaný typ musí vystavit také `Add` metoda, která splňuje následující kritéria.  
  
-   `Add` Metoda musí být dostupné z oboru, ve kterém je volána inicializátoru kolekce. `Add` Metoda nemusí být veřejné, pokud používáte pomocí inicializátoru kolekce ve scénáři kde neveřejný kolekce jsou přístupné.  
  
-   `Add` Metoda musí být členem instance nebo `Shared` členem třídy kolekce nebo metody rozšíření.  
  
-   `Add` Metoda musí existovat, je možné porovnávat, na základě pravidel, rozlišení přetížení, typům zadaných v inicializátoru kolekce.  
  
 Například následující příklad kódu ukazuje, jak vytvořit `List(Of Customer)` kolekce pomocí inicializátoru kolekce. Pokud se kód je spuštěn, každý `Customer` je předán objekt `Add(Customer)` metoda obecné seznamu.  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]  
  
 Následující příklad kódu zobrazuje ekvivalentní kód, který nepoužívá inicializátoru kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]  
  
 Pokud má kolekce `Add` metoda, která obsahuje parametry, které odpovídají v konstruktoru pro `Customer` objektu, může vnořit hodnoty parametrů pro `Add` metoda v rámci Inicializátory kolekcí, jak je popsáno v následující části. Pokud například kolekce nemá `Add` metodu, můžete ji vytvořit jako metody rozšíření. Příklad vytvoření `Add` metoda jako metody rozšíření pro kolekci, najdete v části [postupy: vytvoření přidání rozšíření metoda používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Příklad, jak vytvořit vlastní kolekce, která je možné pomocí inicializátoru kolekce, naleznete v části [postupy: vytvoření kolekce používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).  
  
## <a name="nesting-collection-initializers"></a>Inicializátory kolekcí vnoření  
 Lze vnořit hodnot v rámci inicializátoru kolekce k identifikaci na konkrétní přetížení `Add` metodu pro kolekci, která je právě vytvářena. Hodnoty předaný `Add` metoda musí být oddělené čárkami a uzavřené do složených závorek (`{}`), jako by se provádí v inicializátoru pole literál nebo kolekce.  
  
 Když vytvoříte kolekci pomocí vnořené hodnot, každý element seznamu vnořené hodnota je předat jako argument k `Add` metodu, která odpovídá typy elementů. Například následující příklad kódu vytvoří <xref:System.Collections.Generic.Dictionary%602> ve kterém se klíče typu `Integer` a hodnoty jsou typu `String`. Všechny seznamy vnořené hodnota odpovídá <xref:System.Collections.Generic.Dictionary%602.Add%2A> metodu `Dictionary`.  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]  
  
 V předchozím příkladu kódu je ekvivalentní následující kód.  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]  
  
 Z první úroveň vnoření pouze hodnotu vnořené seznamy jsou odesílány `Add` metody pro typ kolekce. Hlubší úrovní vnoření, se považují za literály pole a hodnotu vnořené seznamy nejsou namapovat na `Add` metody žádné kolekce.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|---|---|  
|[Postupy: vytvoření metody přidání rozšíření používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Ukazuje, jak vytvořit volat metody rozšíření `Add` který lze použít k naplnění kolekce hodnotami z inicializátoru kolekce.|  
|[Postupy: vytvoření kolekce používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Ukazuje, jak povolit pomocí inicializátoru kolekce zahrnutím `Add` metodu v třídě kolekce, který implementuje `IEnumerable`.|  
  
## <a name="see-also"></a>Viz také  
 [Kolekce](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Inicializátory objektů: Pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [New – operátor](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Automaticky implementované vlastnosti](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)  
 [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Úvod do LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Postupy: vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
