---
title: Seznam typů
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 7e22ad6e32ec13f081391e1d47a80df8b1e65063
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412985"
---
# <a name="type-list-visual-basic"></a>Seznam typů (Visual Basic)

Určuje *parametry typu* pro *obecný* programovací prvek. Více parametrů je odděleno čárkami. Následuje syntaxe pro jeden parametr typu.

## <a name="syntax"></a>Syntaxe

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a>Součásti

|Pojem|Definice|
|---|---|
|`genericmodifier`|Nepovinný parametr. Dá se použít jenom v obecných rozhraních a delegátech. Kovariantu typu lze deklarovat pomocí klíčového slova [out](../modifiers/out-generic-modifier.md) nebo kontravariantní pomocí klíčového slova [in](../modifiers/in-generic-modifier.md) . Viz [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).|
|`typename`|Povinná hodnota. Název parametru typu Toto je zástupný symbol, který bude nahrazen definovaným typem poskytnutým odpovídajícím argumentem typu.|
|`constraintlist`|Nepovinný parametr. Seznam požadavků, které omezí datový typ, který je možné zadat pro `typename` . Pokud máte více omezení, vložte je do složených závorek ( `{ }` ) a oddělte je čárkami. Seznam omezení je nutné zavést pomocí klíčového slova [as](as-clause.md) . Použijete ji `As` jenom jednou na začátku seznamu.|

## <a name="remarks"></a>Poznámky

Každý obecný programovací prvek musí mít alespoň jeden parametr typu. Parametr typu je zástupný symbol pro konkrétní typ ( *konstruovaný element*), který určuje kód klienta při vytváření instance obecného typu. Můžete definovat obecnou třídu, strukturu, rozhraní, proceduru nebo delegáta.

Další informace o tom, kdy definovat obecný typ, naleznete [v tématu Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md). Další informace o názvech parametrů typů naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="rules"></a>Pravidla

- **Závorky.** Pokud zadáte seznam parametrů typu, je nutné jej uzavřít do závorek a je třeba uvést seznam [s klíčovým](of-clause.md) slovem. Použijete ji `Of` jenom jednou na začátku seznamu.

- **Jednotlivým.** Seznam *omezení* pro parametr typu může zahrnovat následující položky v libovolné kombinaci:

  - Libovolný počet rozhraní. Zadaný typ musí implementovat každé rozhraní v tomto seznamu.

  - Nejvýše jedna třída. Poskytnutý typ musí dědit z této třídy.

  - `New`Klíčové slovo. Zadaný typ musí vystavit konstruktor bez parametrů, ke kterému má přístup váš obecný typ. To je užitečné, pokud omezíte parametr typu jedním nebo více rozhraními. Typ, který implementuje rozhraní, nutně nezveřejňuje konstruktor a v závislosti na úrovni přístupu konstruktoru, kód v obecném typu nemusí mít přístup k němu.

  - Buď `Class` klíčové slovo, nebo `Structure` klíčové slovo. `Class`Klíčové slovo omezuje parametr obecného typu tak, aby vyžadovalo, aby jakýkoliv argument typu, který je předaný, byl odkazovým typem, například řetězcem, polem nebo delegátem, nebo objektem vytvořeným z třídy. `Structure`Klíčové slovo omezuje parametr obecného typu tak, aby vyžadovalo, aby jakýkoli argument typu, který je předaný, byl typ hodnoty, například struktura, výčet nebo základní datový typ. Nemůžete zahrnout `Class` i `Structure` do stejného `constraintlist` .

  Zadaný typ musí splňovat všechny požadavky, které zahrnete do `constraintlist` .

  Omezení pro jednotlivé parametry typu jsou nezávislá na omezeních u jiných parametrů typu.

## <a name="behavior"></a>Chování

- **Nahrazování v době kompilace.** Když vytvoříte konstruovaný typ z obecného programovacího prvku, zadáte definovaný typ pro každý parametr typu. Kompilátor Visual Basic nahradí daný typ pro všechny výskyty `typename` v rámci obecného prvku.

- **Neexistence omezení** Pokud nezadáte žádná omezení parametru typu, je váš kód omezen na operace a členy podporované [datovým typem objektu](../data-types/object-data-type.md) pro tento parametr typu.

## <a name="example"></a>Příklad

Následující příklad znázorňuje kostru definice třídy obecného slovníku, včetně funkce kostry pro přidání nové položky do slovníku.

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a>Příklad

Vzhledem k tomu `dictionary` , že je obecný, kód, který ho používá, může z něj vytvořit nejrůznější objekty, každá má stejné funkce, ale funguje na jiném datovém typu. Následující příklad ukazuje řádek kódu, který vytvoří `dictionary` objekt s `String` položkami a `Integer` klíči.

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a>Příklad

Následující příklad ukazuje ekvivalentní kostru definice vygenerovanou předchozím příkladem.

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a>Viz také

- [Tohoto](of-clause.md)
- [New – operátor](../operators/new-operator.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Datový typ objektu](../data-types/object-data-type.md)
- [Function – příkaz](function-statement.md)
- [Structure – příkaz](structure-statement.md)
- [Sub – příkaz](sub-statement.md)
- [Postupy: Použití obecné třídy](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [V](../modifiers/in-generic-modifier.md)
- [Mimo](../modifiers/out-generic-modifier.md)
