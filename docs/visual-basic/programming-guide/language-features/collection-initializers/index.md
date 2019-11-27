---
title: Inicializátory kolekce
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: fbdd116298c530ae54677631eff7dac2f22c0fe2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346786"
---
# <a name="collection-initializers-visual-basic"></a>Inicializátory kolekcí (Visual Basic)

*Inicializátory kolekce* poskytují zkrácenou syntaxi, která umožňuje vytvořit kolekci a naplnit ji počáteční sadou hodnot. Inicializátory kolekce jsou užitečné při vytváření kolekce ze sady známých hodnot, například seznamu možností nabídky nebo kategorií, počáteční sady číselných hodnot, statického seznamu řetězců, jako jsou například názvy dnů nebo měsíců nebo zeměpisná umístění, jako je například seznam stavů, které se použijí k ověření.

Další informace o kolekcích najdete v tématu [kolekce](../../../../visual-basic/programming-guide/concepts/collections.md).

Inicializátor kolekce identifikujete pomocí klíčového slova `From`, po kterém následují složené závorky (`{}`). Toto je podobné syntaxi literálu pole, která je popsána v [poli](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Následující příklady znázorňují různé způsoby použití inicializátorů kolekcí k vytváření kolekcí.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> C#také poskytuje inicializátory kolekce. C#inicializátory kolekce poskytují stejné funkce jako Visual Basic Inicializátory kolekcí. Další informace o C# inicializátorech kolekce naleznete v tématu [Inicializátory objektů a kolekcí](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Syntaxe

Inicializátor kolekce se skládá ze seznamu hodnot oddělených čárkami, které jsou uzavřeny v závorkách (`{}`) před klíčovým slovem `From`, jak je znázorněno v následujícím kódu.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Při vytváření kolekce, jako je například <xref:System.Collections.Generic.List%601> nebo <xref:System.Collections.Generic.Dictionary%602>, je nutné před inicializátorem kolekce zadat typ kolekce, jak je znázorněno v následujícím kódu.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Nelze kombinovat inicializátor kolekce a inicializátor objektu pro inicializaci stejného objektu kolekce. Můžete použít inicializátory objektů k inicializaci objektů v inicializátoru kolekce.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Vytvoření kolekce pomocí inicializátoru kolekce

Když vytváříte kolekci pomocí inicializátoru kolekce, každá hodnota, která je zadána v inicializátoru kolekce, je předána příslušné `Add` metodě kolekce. Například pokud vytvoříte <xref:System.Collections.Generic.List%601> pomocí inicializátoru kolekce, každá řetězcová hodnota v inicializátoru kolekce je předána metodě <xref:System.Collections.Generic.List%601.Add%2A>. Pokud chcete vytvořit kolekci pomocí inicializátoru kolekce, zadaný typ musí být platný typ kolekce. Příklady platných typů kolekcí zahrnují třídy, které implementují rozhraní <xref:System.Collections.Generic.IEnumerable%601> nebo dědí <xref:System.Collections.CollectionBase> třídy. Zadaný typ musí také vystavit `Add` metodu, která splňuje následující kritéria.

- Metoda `Add` musí být k dispozici z oboru, ve kterém je volán inicializátor kolekce. Metoda `Add` nemusí být veřejná, pokud používáte inicializátor kolekce v situaci, kdy je k dispozici neveřejné metody kolekce.

- Metoda `Add` musí být členem instance nebo `Shared` členem třídy kolekce nebo metodou rozšíření.

- Musí existovat `Add` metoda, která může odpovídat na základě pravidel Rozlišení přetěžování na typy, které jsou zadány v inicializátoru kolekce.

 Například následující příklad kódu ukazuje, jak vytvořit kolekci `List(Of Customer)` pomocí inicializátoru kolekce. Při spuštění kódu je každý objekt `Customer` předán metodě `Add(Customer)` obecného seznamu.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

Následující příklad kódu ukazuje ekvivalentní kód, který nepoužívá inicializátor kolekce.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Pokud má kolekce `Add` metodu, která má parametry odpovídající konstruktoru pro objekt `Customer`, mohli byste vnořit hodnoty parametrů pro metodu `Add` v rámci inicializátorů kolekce, jak je popsáno v následující části. Pokud kolekce neobsahuje takovou `Add` metodu, můžete ji vytvořit jako metodu rozšíření. Příklad, jak vytvořit metodu `Add` jako metodu rozšíření pro kolekci, naleznete v tématu [How to: Create a Add rozšiřující metodu, kterou používá inicializátor kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Příklad vytvoření vlastní kolekce, která může být použita s inicializátorem kolekce, naleznete v tématu [How to: Create a Collection použit inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Vnořování inicializátorů kolekce

Můžete vnořit hodnoty do inicializátoru kolekce a identifikovat konkrétní přetížení metody `Add` pro kolekci, která se vytváří. Hodnoty předané metodě `Add` musí být odděleny čárkami a uzavřeny ve složených závorkách (`{}`), jako by to bylo provedeno v literálu pole nebo inicializátoru kolekce.

Při vytváření kolekce pomocí vnořených hodnot je každý prvek seznamu vnořených hodnot předán jako argument metodě `Add`, která odpovídá typům prvků. Například následující příklad kódu vytvoří <xref:System.Collections.Generic.Dictionary%602>, ve kterém jsou klíče typu `Integer` a hodnoty jsou typu `String`. Každý z vnořených seznamů hodnot se shoduje s metodou <xref:System.Collections.Generic.Dictionary%602.Add%2A> pro `Dictionary`.

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

Předchozí příklad kódu je ekvivalentní následujícímu kódu.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Do metody `Add` pro typ kolekce jsou odesílány pouze seznamy s vnořenými hodnotami z první úrovně vnoření. Hlubší úrovně vnoření jsou považovány za pole literálů a vnořené seznamy hodnot se neshodují s metodou `Add` žádné kolekce.

## <a name="related-topics"></a>Související témata

|Titul|Popis|
|---|---|
|[Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Ukazuje, jak vytvořit metodu rozšíření nazvanou `Add`, kterou lze použít k naplnění kolekce hodnotami z inicializátoru kolekce.|
|[Postupy: Vytvoření kolekce používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Ukazuje, jak povolit použití inicializátoru kolekce zahrnutím metody `Add` do třídy kolekce, která implementuje `IEnumerable`.|

## <a name="see-also"></a>Viz také:

- [Kolekce](../../../../visual-basic/programming-guide/concepts/collections.md)
- [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Operátor New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Automaticky implementované vlastnosti](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Postupy: Inicializace proměnné pole v Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
- [Odvození místního typu](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Anonymní typy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Úvod do jazyka LINQ v Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Postupy: Vytvoření seznamu položek](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
