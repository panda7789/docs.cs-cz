---
title: Expression – těle členové – C# Průvodce programováním
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711984"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Výrazy – těle členové (C# Průvodce programováním)

Definice textu výrazu umožňují poskytovat implementaci člena ve velmi stručné a čitelné podobě. Definici těla výrazu můžete použít vždy, když logika pro libovolný podporovaný člen, jako je například metoda nebo vlastnost, se skládá z jednoho výrazu. Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

*výraz* WHERE je platný výraz.

Pro metody a vlastnosti jen pro čtení v C# 6 byly zavedeny podpory definic těla výrazů a v C# 7,0 byly rozbaleny. Definice textu výrazu lze použít s členy typu uvedenými v následující tabulce:

|Člen  |Podporováno pro... |
|---------|---------|
|[– Metoda](#methods)  |C# 6 |
|[Vlastnost jen pro čtení](#read-only-properties)   |C# 6  |
|[Vlastnost](#properties)  |C# 7.0 |
|[BeginRequestEventArgs](#constructors)   |C# 7.0 |
|[Finalizační metodu](#finalizers)     |C# 7.0 |
|[Indexer](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda těle výrazu se skládá z jednoho výrazu, který vrací hodnotu, jejíž typ odpovídá návratový typ metody, nebo, pro metody, které vracejí `void`, které provádí určitou operaci. Například typy, které přepisují metodu <xref:System.Object.ToString%2A> obvykle zahrnují jeden výraz, který vrací řetězcovou reprezentaci aktuálního objektu.

Následující příklad definuje třídu `Person`, která přepisuje metodu <xref:System.Object.ToString%2A> pomocí definice těla výrazu. Definuje také metodu `DisplayName`, která zobrazuje název konzoly. Všimněte si, že klíčové slovo `return` se v definici těla výrazu `ToString` nepoužívá.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Další informace naleznete v tématu [metody (C# Průvodce programováním)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Vlastnosti jen pro čtení

Počínaje C# 6 můžete použít definici textu výrazu k implementaci vlastnosti jen pro čtení. K tomu použijte následující syntaxi:

```csharp
PropertyType PropertyName => expression;
```

Následující příklad definuje třídu `Location`, jejíž vlastnost `Name` jen pro čtení je implementována jako definice těla výrazu, která vrací hodnotu soukromého `locationName` pole:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Další informace o vlastnostech naleznete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).

## <a name="properties"></a>Vlastnosti

Počínaje verzí C# 7,0 můžete použít definice těla výrazu k implementaci `get` vlastností a přístupových objektů `set`. Následující příklad ukazuje, jak to provést:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Další informace o vlastnostech naleznete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktory

Definice těla výrazu pro konstruktor se obvykle skládá z jednoho výrazu přiřazení nebo volání metody, které zpracovává argumenty konstruktoru nebo inicializuje stav instance.

Následující příklad definuje třídu `Location`, jejíž konstruktor má jeden řetězcový parametr s názvem *Name*. Definice těla výrazu přiřadí argument vlastnosti `Name`.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Další informace naleznete v tématu [konstruktory (C# Průvodce programováním)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizační metody

Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, například příkazy, které uvolní nespravované prostředky.

Následující příklad definuje finalizační metodu, která používá definici těla výrazu k označení toho, že finalizační metoda byla volána.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Další informace naleznete v tématu [finalizační metody (C# Průvodce programováním)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indexery

Podobně jako u vlastností, indexerů `get` a přistupujících objektů `set` se skládají z definic textu výrazu, pokud se `get` přistupující objekt skládá z jediného výrazu, který vrací hodnotu nebo objekt pro přístup k `set` provádí jednoduché přiřazení.

Následující příklad definuje třídu s názvem `Sports`, která obsahuje interní <xref:System.String> pole, které obsahuje názvy pro řadu sportovních. Indexer `get` i přistupující objekty `set` jsou implementovány jako definice textu výrazu.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Další informace najdete v tématu [indexery (C# Průvodce programováním)](../indexers/index.md).
