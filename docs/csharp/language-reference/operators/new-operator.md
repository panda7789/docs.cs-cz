---
title: operátor new - C# odkaz
ms.custom: seodec18
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3d64c4805abe38c80301748ffa6b35fc87563b60
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402511"
---
# <a name="new-operator-c-reference"></a>New – operátor (C# odkaz)

`new` Operátor vytvoří novou instanci typu.

Můžete také použít `new` – klíčové slovo jako [modifikátoru deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Vyvolání konstruktoru

Pokud chcete vytvořit novou instanci typu, je obvykle vyvolat jeden z [konstruktory](../../programming-guide/classes-and-structs/constructors.md) tento typ použití `new` operátor:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Můžete použít [inicializátor objektu nebo kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) s `new` operátor konkretizovat a inicializovat objekt v jednom příkazu, jako v následujícím příkladu:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Vytvoření pole

Můžete také použít `new` operátoru pro vytvoření instance pole, jako v následujícím příkladu:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Syntaxe inicializace pole použijte k vytvoření instance pole a přidejte do ní prvky v jednom příkazu. Následující příklad ukazuje různé způsoby, jak můžete to udělat:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Další informace o polích naleznete v tématu [pole](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Vytvoření instance anonymní typy

K vytvoření instance [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte `new` operátor a objekt syntaxe inicializátoru:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Odstranění instance typu

Není nutné ke zničení dříve vytvořený typ instance. Instance typů odkazu a hodnota jsou zničeny automaticky. Poté, co je zničen kontext, který je obsahuje, jsou zničeny instancí typů hodnot. Instance typů odkazů, jsou zničeny podle [systému uvolňování paměti](../../../standard/garbage-collection/index.md) neurčené době po odebrání poslední odkazy na ně.

Pro typy, které obsahují nespravované prostředky například popisovač souboru, se doporučuje využívat deterministické čištění zajistit, že se prostředky, které obsahují vydávají co nejdříve. Další informace najdete v tématu <xref:System.IDisposable?displayProperty=nameWithType> reference k rozhraní API a [příkaz using](../keywords/using-statement.md) článku.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit `new` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátor new](~/_csharplang/spec/expressions.md#the-new-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Inicializátory objektu a kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
