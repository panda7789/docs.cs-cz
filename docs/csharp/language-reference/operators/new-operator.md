---
title: nový operátor - odkaz Jazyka C#
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 84131bc503a106961419a27fc4e3e0f2d82306a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846230"
---
# <a name="new-operator-c-reference"></a>nový operátor (odkaz C# )

Operátor `new` vytvoří novou instanci typu.

Klíčové slovo můžete také použít jako [modifikátor deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md). `new`

## <a name="constructor-invocation"></a>Vyvolání konstruktoru

Chcete-li vytvořit novou instanci typu, obvykle vyvolat jeden z [konstruktorů](../../programming-guide/classes-and-structs/constructors.md) tohoto typu pomocí operátoru: `new`

[!code-csharp-interactive[invoke constructor](snippets/NewOperator.cs#Constructor)]

[Inicializátor objektu nebo](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) `new` kolekce s operátorem můžete použít k vytvoření instance a inicializaci objektu v jednom příkazu, jak ukazuje následující příklad:

[!code-csharp-interactive[constructor with initializer](snippets/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Vytvoření pole

`new` Operátor můžete také použít k vytvoření instance pole, jak ukazuje následující příklad:

[!code-csharp-interactive[create array](snippets/NewOperator.cs#Array)]

Pomocí syntaxe inicializace pole vytvořte instanci pole a naplňte ji prvky v jednom příkazu. Následující příklad ukazuje různé způsoby, jak to udělat:

[!code-csharp-interactive[initialize array](snippets/NewOperator.cs#ArrayInitialization)]

Další informace o polích naleznete v [tématu Arrays](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Vytváření instancí anonymních typů

Chcete-li vytvořit instanci [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte syntaxi inicializačního operátoru `new` a objektu:

[!code-csharp-interactive[anonymous type](snippets/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Zničení instancí typu

Není třeba zničit dříve vytvořené instance typu. Instance referenčních i hodnotových typů jsou automaticky zničeny. Instance typů hodnot jsou zničeny, jakmile je zničen kontext, který je obsahuje. Instance typů odkazů jsou zničeny [systémem uvolňování paměti](../../../standard/garbage-collection/index.md) v neurčeném čase po odebrání posledního odkazu na ně.

Pro instance typu, které obsahují nespravované prostředky, například popisovač souboru, se doporučuje použít deterministické vyčištění, aby bylo zajištěno, že prostředky, které obsahují, budou vydány co nejdříve. Další informace naleznete <xref:System.IDisposable?displayProperty=nameWithType> v odkazu rozhraní API a [using prohlášení](../keywords/using-statement.md) článku.

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ nemůže `new` přetížit operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [v části Nový operátor](~/_csharplang/spec/expressions.md#the-new-operator) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Inicializátory objektů a kolekcí](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
