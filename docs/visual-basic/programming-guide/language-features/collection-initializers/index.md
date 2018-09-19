---
title: Inicializátory kolekcí (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: c22599f50ac071245a1381d267f3f7cb66806174
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991620"
---
# <a name="collection-initializers-visual-basic"></a>Inicializátory kolekcí (Visual Basic)
*Inicializátory kolekcí* poskytují zkrácený syntaxi, která vám umožní vytvořit kolekci a přidejte do ní počáteční sadu hodnot. Inicializátory kolekcí jsou užitečné při vytváření kolekce na základě sady známé hodnoty, například seznam možností v nabídce nebo kategorie, počáteční sadu číselných hodnot, statický seznam řetězců, jako je například den nebo měsíc názvy nebo zeměpisné umístění, jako seznam stavů, který se používá k ověření.  
  
 Další informace o kolekcích najdete v tématu [kolekce](../../../../visual-basic/programming-guide/concepts/collections.md).  
  
 Můžete identifikovat pomocí inicializátoru kolekce `From` – klíčové slovo následované složené závorky (`{}`). To se podobá syntaxi literálu pole, podle popisu v [pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Následující příklady ukazují různé způsoby, jak použít inicializátory kolekce k vytvoření kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]  
  
> [!NOTE]
>  C# obsahuje také inicializátory kolekce. Inicializátory kolekce jazyka C# poskytují stejné funkce jako inicializátory kolekce jazyka Visual Basic. Další informace o inicializátory kolekce jazyka C# najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="syntax"></a>Syntaxe  
 Inicializátor kolekce se skládá ze seznamu hodnot oddělených čárkami, které jsou uzavřeny ve složených závorkách (`{}`), předchází `From` – klíčové slovo, jak je znázorněno v následujícím kódu.  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]  
  
 Když vytvoříte kolekci, například <xref:System.Collections.Generic.List%601> nebo <xref:System.Collections.Generic.Dictionary%602>, jak je znázorněno v následujícím kódu je nutné zadat typ kolekce před inicializátor kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]  
  
> [!NOTE]
>  Inicializátor kolekce a inicializátoru objektu inicializovat stejného objektu kolekce nelze kombinovat. Inicializátory objektů můžete použít třeba inicializovat objekty v incializátoru kolekce.  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a>Vytvoření kolekce s použitím Intializer kolekce  
 Při vytvoření kolekce pomocí inicializátoru kolekce, každá hodnota, která je zadána v inicializátoru kolekce je předána na příslušné `Add` metody kolekce. Například, pokud vytvoříte <xref:System.Collections.Generic.List%601> pomocí inicializátoru kolekce je předána hodnota každý řetězec v inicializátoru kolekce <xref:System.Collections.Generic.List%601.Add%2A> metody. Pokud chcete vytvořit kolekci pomocí inicializátoru kolekce, zadaný typ musí být typu platné kolekce. Příklady typů platné kolekce tříd, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo dědí <xref:System.Collections.CollectionBase> třídy. Zadaný typ musí vystavit také `Add` metodu, která splňuje následující kritéria.  
  
-   `Add` Metoda musí být k dispozici z oboru, ve kterém je volána inicializátor kolekce. `Add` Metody nemusí být veřejné, pokud použijete inicializátor kolekce v případě kdy je přístupná neveřejné metody kolekce.  
  
-   `Add` Metoda musí být členem instance nebo `Shared` člena kolekce třídy nebo metody rozšíření.  
  
-   `Add` Metodu musí existovat, který by se shodovala, na základě pravidel rozlišení přetížení, typy, které jsou dodávány v inicializátoru kolekce.  
  
 Například následující příklad kódu ukazuje, jak vytvořit `List(Of Customer)` kolekce pomocí inicializátoru kolekce. Když je kód spuštěn, každý `Customer` objekt je předán `Add(Customer)` metoda obecného seznamu.  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]  
  
 Následující příklad kódu ukazuje odpovídající kód, který nepoužívá inicializátor kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]  
  
 Pokud má kolekce `Add` metodu, která obsahuje parametry, které odpovídají konstruktor pro `Customer` objektu, může vnořené hodnoty parametrů pro `Add` metody v rámci kolekce inicializátory, jak je popsáno v další části. Pokud například kolekce nemá `Add` metodu, můžete si ho vytvořit jako metody rozšíření. Příklad toho, jak vytvořit `Add` metody jako metody rozšíření pro kolekci, najdete v článku [postupy: vytvoření přidat rozšíření metoda používá inicializátor kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Příklad toho, jak vytvořit vlastní kolekce, která je možné pomocí inicializátoru kolekce, naleznete v tématu [postupy: vytvoření kolekce používané Inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).  
  
## <a name="nesting-collection-initializers"></a>Inicializátory kolekcí vnoření  
 Je možné vnořovat hodnotami v inicializátoru kolekce k identifikaci na konkrétní přetížení `Add` metodu pro kolekci, která se vytváří. Hodnot předaných `Add` metoda musí být oddělené čárkami a uzavřeny ve složených závorkách (`{}`), stejně jako by v inicializátoru pole literálu nebo kolekci.  
  
 Při vytvoření kolekce pomocí vnořených hodnot, každý prvek seznamu Vnořená hodnota předána jako argument `Add` metodu, která odpovídá typy prvků. Například následující příklad kódu vytvoří <xref:System.Collections.Generic.Dictionary%602> v které klíče jsou typu `Integer` a hodnoty jsou typu `String`. Každého ze seznamů vnořené hodnoty odpovídají <xref:System.Collections.Generic.Dictionary%602.Add%2A> metodu `Dictionary`.  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]  
  
 V předchozím příkladu kódu je ekvivalentní následujícímu kódu.  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]  
  
 Z první úroveň vnoření pouze vnořené hodnoty seznamy jsou odesílány `Add` metody pro typ kolekce. Hlubší úrovně vnoření jsou považovány za literály pole a seznamy vnořené hodnoty nejsou odpovídají `Add` metoda žádné kolekce.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|---|---|  
|[Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Ukazuje, jak vytvořit rozšiřující metoda volá `Add` , který slouží k naplnění kolekce s hodnotami z inicializátoru kolekce.|  
|[Postupy: Vytvoření kolekce používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Ukazuje, jak povolit používání inicializátoru kolekce zahrnutím `Add` metody ve třídě kolekce, která implementuje `IEnumerable`.|  
  
## <a name="see-also"></a>Viz také:

- [Kolekce](../../../../visual-basic/programming-guide/concepts/collections.md)  
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
- [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)  
- [Automaticky implementované vlastnosti](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
- [Postupy: Inicializace proměnné pole v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)  
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
- [Úvod do LINQ v JAZYKU Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [Postupy: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
