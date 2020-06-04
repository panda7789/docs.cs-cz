---
title: Inicializátory kolekcí
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: 1d2d5adc7266faaa1636e568d6433429761eeaab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414541"
---
# <a name="collection-initializers-visual-basic"></a>Inicializátory kolekcí (Visual Basic)

*Inicializátory kolekce* poskytují zkrácenou syntaxi, která umožňuje vytvořit kolekci a naplnit ji počáteční sadou hodnot. Inicializátory kolekce jsou užitečné při vytváření kolekce ze sady známých hodnot, například seznamu možností nabídky nebo kategorií, počáteční sady číselných hodnot, statického seznamu řetězců, jako jsou například názvy dnů nebo měsíců nebo zeměpisná umístění, jako je například seznam stavů, které se používají k ověření.

Další informace o kolekcích najdete v tématu [kolekce](../../concepts/collections.md).

Inicializátor kolekce identifikujete pomocí `From` klíčového slova, po kterém následují složené závorky ( `{}` ). Toto je podobné syntaxi literálu pole, která je popsána v [poli](../arrays/index.md). Následující příklady znázorňují různé způsoby použití inicializátorů kolekcí k vytváření kolekcí.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> Jazyk C# také poskytuje inicializátory kolekce. Inicializátory kolekce jazyka C# poskytují stejné funkce jako Visual Basic Inicializátory kolekcí. Další informace o inicializátorech kolekce jazyka C# naleznete v tématu [Inicializátory objektů a kolekcí](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Syntaxe

Inicializátor kolekce se skládá ze seznamu hodnot oddělených čárkami, které jsou uzavřeny v závorkách ( `{}` ), předchází `From` klíčové slovo, jak je znázorněno v následujícím kódu.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Při vytváření kolekce, jako je například <xref:System.Collections.Generic.List%601> nebo <xref:System.Collections.Generic.Dictionary%602> , je nutné před inicializátorem kolekce zadat typ kolekce, jak je znázorněno v následujícím kódu.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Nelze kombinovat inicializátor kolekce a inicializátor objektu pro inicializaci stejného objektu kolekce. Můžete použít inicializátory objektů k inicializaci objektů v inicializátoru kolekce.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Vytvoření kolekce pomocí inicializátoru kolekce

Když vytváříte kolekci pomocí inicializátoru kolekce, každá hodnota, která je zadána v inicializátoru kolekce, je předána příslušné `Add` metodě kolekce. Například pokud vytvoříte pomocí <xref:System.Collections.Generic.List%601> inicializátoru kolekce, každá řetězcová hodnota v inicializátoru kolekce je předána <xref:System.Collections.Generic.List%601.Add%2A> metodě. Pokud chcete vytvořit kolekci pomocí inicializátoru kolekce, zadaný typ musí být platný typ kolekce. Příklady platných typů kolekcí zahrnují třídy, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo dědí <xref:System.Collections.CollectionBase> třídu. Zadaný typ musí také vystavit `Add` metodu, která splňuje následující kritéria.

- `Add`Metoda musí být k dispozici z oboru, ve kterém je volán inicializátor kolekce. `Add`Metoda nemusí být veřejná, pokud používáte inicializátor kolekce v situaci, kdy je možné k neveřejným metodám kolekce přistupovat.

- `Add`Metoda musí být členem instance nebo `Shared` členem třídy kolekce nebo metodou rozšíření.

- `Add`Metoda musí existovat, která může odpovídat na základě pravidel rozlišení přetížení na typy, které jsou zadány v inicializátoru kolekce.

 Například následující příklad kódu ukazuje, jak vytvořit `List(Of Customer)` kolekci pomocí inicializátoru kolekce. Při spuštění kódu `Customer` se každý objekt předává `Add(Customer)` metodě obecného seznamu.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Následující příklad kódu ukazuje ekvivalentní kód, který nepoužívá inicializátor kolekce.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Pokud má kolekce `Add` metodu, která má parametry odpovídající konstruktoru pro `Customer` objekt, můžete vnořovat hodnoty parametrů pro `Add` metodu v rámci inicializátorů kolekce, jak je popsáno v následující části. Pokud kolekce neobsahuje takovou `Add` metodu, můžete ji vytvořit jako metodu rozšíření. Příklad vytvoření `Add` metody jako metody rozšíření pro kolekci naleznete v tématu [How to: Create a Add rozšiřující metodu, kterou používá inicializátor kolekce](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Příklad vytvoření vlastní kolekce, která může být použita s inicializátorem kolekce, naleznete v tématu [How to: Create a Collection použit inicializátorem kolekce](how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Vnořování inicializátorů kolekce

Můžete vnořovat hodnoty v rámci inicializátoru kolekce pro identifikaci konkrétního přetížení `Add` metody pro kolekci, která se vytváří. Hodnoty předané `Add` metodě musí být odděleny čárkami a uzavřeny v závorkách ( `{}` ), podobně jako v literálu pole nebo inicializátoru kolekce.

Při vytváření kolekce pomocí vnořených hodnot je každý prvek seznamu vnořených hodnot předán jako argument `Add` metodě, která odpovídá typům prvků. Například následující příklad kódu vytvoří, <xref:System.Collections.Generic.Dictionary%602> v němž jsou klíče typu `Integer` a hodnoty jsou typu `String` . Každý z vnořených seznamů hodnot se shoduje s <xref:System.Collections.Generic.Dictionary%602.Add%2A> metodou pro `Dictionary` .

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Předchozí příklad kódu je ekvivalentní následujícímu kódu.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Metodě pro typ kolekce jsou odesílány pouze seznamy s vnořenými hodnotami z první úrovně vnoření `Add` . Hlubší úrovně vnoření jsou považovány za pole literálů a vnořené seznamy hodnot se neshodují s `Add` metodou žádné kolekce.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|---|---|
|[Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Ukazuje, jak vytvořit rozšiřující metodu nazvanou `Add` , která může být použita k naplnění kolekce hodnotami z inicializátoru kolekce.|
|[Postupy: Vytvoření kolekce používané inicializátorem kolekce](how-to-create-a-collection-used-by-a-collection-initializer.md)|Ukazuje, jak povolit použití inicializátoru kolekce zahrnutím `Add` metody do třídy kolekce, která implementuje `IEnumerable` .|

## <a name="see-also"></a>Viz také

- [Kolekce](../../concepts/collections.md)
- [Pole](../arrays/index.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [New – operátor](../../../language-reference/operators/new-operator.md)
- [Automaticky implementované vlastnosti](../procedures/auto-implemented-properties.md)
- [Postupy: Inicializace proměnné pole v jazyce Visual Basic](../arrays/how-to-initialize-an-array-variable.md)
- [Odvození místního typu](../variables/local-type-inference.md)
- [Anonymní typy](../objects-and-classes/anonymous-types.md)
- [Představení technologie LINQ v jazyce Visual Basic](../linq/introduction-to-linq.md)
- [Postupy: Vytvoření seznamu položek](../../concepts/linq/how-to-create-a-list-of-items.md)
