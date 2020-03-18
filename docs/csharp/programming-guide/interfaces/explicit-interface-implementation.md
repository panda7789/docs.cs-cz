---
title: Explicitní implementace rozhraní – programovací příručka jazyka C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167670"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementace explicitního rozhraní (Průvodce programováním v C#)

Pokud [třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, které obsahují člen se stejným podpisem, pak implementace tohoto člena ve třídě způsobí, že obě rozhraní použít tento člen jako jejich implementace. V následujícím příkladu všechna `Paint` volání vyvolat stejnou metodu. Tato první ukázka definuje typy:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Následující ukázka volá metody:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Pokud dva členové rozhraní nevykonávají stejnou funkci, vede k nesprávné implementaci jednoho nebo obou rozhraní. Je možné implementovat člen rozhraní explicitně – vytvoření člena třídy, který je volán pouze prostřednictvím rozhraní a je specifické pro toto rozhraní. Pojmenujte člena třídy názvem rozhraní a tečkou. Například:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

`IControl.Paint` Člen třídy je k `IControl` dispozici `ISurface.Paint` pouze prostřednictvím `ISurface`rozhraní a je k dispozici pouze prostřednictvím . Obě implementace metody jsou samostatné a ani nejsou k dispozici přímo ve třídě. Například:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Explicitní implementace se také používá k vyřešení případů, kdy dvě rozhraní každý deklarovat různé členy se stejným názvem, jako je například vlastnost a metoda. Chcete-li implementovat obě rozhraní, třída musí použít `P`explicitní implementaci `P`buď pro vlastnost , nebo metodu nebo obojí, aby se zabránilo chybě kompilátoru. Například:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Počínaje [C# 8.0](../../whats-new/csharp-8.md#default-interface-methods), můžete definovat implementaci pro členy deklarované v rozhraní. Pokud třída dědí implementaci metody z rozhraní, tato metoda je přístupná pouze prostřednictvím odkazu na typ rozhraní. Zděděný člen se nezobrazí jako součást veřejného rozhraní. Následující ukázka definuje výchozí implementaci metody rozhraní:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Následující ukázka vyvolá výchozí implementaci:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Každá třída, která `IControl` implementuje rozhraní `Paint` můžete přepsat výchozí metodu, buď jako veřejnou metodu nebo jako explicitní implementace rozhraní.

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
