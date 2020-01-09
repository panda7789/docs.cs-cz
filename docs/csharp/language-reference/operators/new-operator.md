---
title: Nový operátor – C# referenční informace
ms.date: 06/25/2019
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: beb55f0765e7f9090f0587f1d2a06cf03ea90ab8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712660"
---
# <a name="new-operator-c-reference"></a>New – operátorC# (Referenční dokumentace)

Operátor `new` vytvoří novou instanci typu.

Můžete také použít klíčové slovo `new` jako [Modifikátor deklarace člena](../keywords/new-modifier.md) nebo [omezení obecného typu](../keywords/new-constraint.md).

## <a name="constructor-invocation"></a>Vyvolání konstruktoru

Chcete-li vytvořit novou instanci typu, obvykle vyvoláte jeden z [konstruktorů](../../programming-guide/classes-and-structs/constructors.md) tohoto typu pomocí operátoru `new`:

[!code-csharp-interactive[invoke constructor](~/samples/csharp/language-reference/operators/NewOperator.cs#Constructor)]

Můžete použít [inicializátor objektu nebo kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) s operátorem `new` pro vytvoření instance a inicializaci objektu v jednom příkazu, jak ukazuje následující příklad:

[!code-csharp-interactive[constructor with initializer](~/samples/csharp/language-reference/operators/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a>Vytvoření pole

Také operátor `new` slouží k vytvoření instance pole, jak ukazuje následující příklad:

[!code-csharp-interactive[create array](~/samples/csharp/language-reference/operators/NewOperator.cs#Array)]

Pomocí syntaxe inicializace pole vytvořte instanci pole a naplňte ji prvky v jednom příkazu. Následující příklad ukazuje různé způsoby, jak to lze provést:

[!code-csharp-interactive[initialize array](~/samples/csharp/language-reference/operators/NewOperator.cs#ArrayInitialization)]

Další informace o polích naleznete v tématu [Arrays](../../programming-guide/arrays/index.md).

## <a name="instantiation-of-anonymous-types"></a>Vytváření instancí anonymních typů

Chcete-li vytvořit instanci [anonymního typu](../../programming-guide/classes-and-structs/anonymous-types.md), použijte operátor `new` a syntaxi inicializátoru objektu:

[!code-csharp-interactive[anonymous type](~/samples/csharp/language-reference/operators/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a>Zničení instancí typů

Nemusíte zničit dřívější vytvořené instance typu. Instance obou typů odkaz i hodnota jsou zničeny automaticky. Instance typů hodnot jsou zničeny ihned po zničení kontextu, který je obsahuje. Instance typů odkazů jsou zničeny systémem [uvolňování paměti](../../../standard/garbage-collection/index.md) v nespecifikovaném čase po odebrání posledního odkazu na ně.

U instancí typu, které obsahují nespravované prostředky, například popisovač souboru, se doporučuje použít deterministické vyčištění, aby bylo zajištěno, že prostředky, které obsahují, budou zveřejněny co nejdříve. Další informace najdete v tématu Reference k rozhraní API <xref:System.IDisposable?displayProperty=nameWithType> a v článku o [příkazu Using](../keywords/using-statement.md) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže přetížit operátor `new`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v části [Nový operátor](~/_csharplang/spec/expressions.md#the-new-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Inicializátory objektu a kolekce](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
