---
title: Explicitní implementace rozhraní – C# Průvodce programováním
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628147"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implementace explicitního rozhraní (Průvodce programováním v C#)

Pokud [Třída](../../language-reference/keywords/class.md) implementuje dvě rozhraní, která obsahují člena se stejnou signaturou, pak implementace tohoto člena na třídu způsobí, že obě rozhraní budou používat tento člen jako svou implementaci. V následujícím příkladu všechna volání `Paint` vyvolat stejnou metodu. Tato první ukázka definuje typy:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

Následující příklad volá metody:

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Pokud dva členy rozhraní neprovádějí stejnou funkci, vede k nesprávné implementaci jednoho nebo obou rozhraní. Je možné implementovat člena rozhraní explicitně – vytvořením členu třídy, který je volán pouze prostřednictvím rozhraní a je specifický pro toto rozhraní. Pojmenujte člena třídy názvem rozhraní a tečkou. Příklad:

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Člen třídy `IControl.Paint` je k dispozici pouze prostřednictvím rozhraní `IControl` a `ISurface.Paint` je k dispozici pouze prostřednictvím `ISurface`. Implementace obou metod jsou oddělené a žádné nejsou k dispozici přímo na třídě. Příklad:

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

Explicitní implementace je také použita k vyřešení případů, kde dvě rozhraní každý deklaruje různé členy stejného názvu, jako je například vlastnost a metoda. Pro implementaci obou rozhraní musí třída použít explicitní implementaci buď pro vlastnost `P`, nebo metodu `P`nebo obojí, aby nedošlo k chybě kompilátoru. Příklad:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Pokud třída dědí implementaci metody z rozhraní, je tato metoda přístupná pouze prostřednictvím odkazu typu rozhraní. Zděděný člen se nezobrazuje jako součást veřejného rozhraní. Následující příklad definuje výchozí implementaci pro metodu rozhraní:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

Následující ukázka vyvolá výchozí implementaci:

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Libovolná třída, která implementuje rozhraní `IControl`, může přepsat výchozí `Paint` metodu buď jako veřejnou metodu, nebo jako explicitní implementaci rozhraní.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](../classes-and-structs/index.md)
- [Rozhraní](./index.md)
- [Dědičnost](../classes-and-structs/inheritance.md)
