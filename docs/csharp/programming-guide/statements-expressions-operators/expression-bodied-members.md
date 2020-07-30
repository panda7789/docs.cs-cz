---
title: Expression-těle Members – Průvodce programováním v C#
description: Přečtěte si o členech Expression-těle. Podívejte se na příklady kódu, které používají definici textu výrazu pro vlastnosti, konstruktory, finalizační metody a další.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381655"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Expression-těle členové (Průvodce programováním v C#)

Definice textu výrazu umožňují poskytovat implementaci člena ve velmi stručné a čitelné podobě. Definici těla výrazu můžete použít vždy, když logika pro libovolný podporovaný člen, jako je například metoda nebo vlastnost, se skládá z jednoho výrazu. Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

*výraz* WHERE je platný výraz.

Pro metody a vlastnosti jen pro čtení v C# 6 byly zavedeny podpory pro definice těla výrazu a rozšířily se v C# 7,0. Definice textu výrazu lze použít s členy typu uvedenými v následující tabulce:

|Člen  |Podporováno pro... |
|---------|---------|
|[Metoda](#methods)  |C# 6 |
|[Vlastnost jen pro čtení](#read-only-properties)   |C# 6  |
|[Vlastnost](#properties)  |C# 7.0 |
|[Konstruktor](#constructors)   |C# 7.0 |
|[Finalizační metodu](#finalizers)     |C# 7.0 |
|[Indexer](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda těle výrazu se skládá z jednoho výrazu, který vrací hodnotu, jejíž typ odpovídá návratového typu metody, nebo pro metody, které vracejí `void` , které provádí určitou operaci. Například typy, které přepisují <xref:System.Object.ToString%2A> metodu obvykle zahrnují jeden výraz, který vrací řetězcovou reprezentaci aktuálního objektu.

Následující příklad definuje `Person` třídu, která přepisuje <xref:System.Object.ToString%2A> metodu pomocí definice těla výrazu. Definuje také `DisplayName` metodu, která zobrazí název konzole. Všimněte si, že `return` klíčové slovo se v `ToString` definici těla výrazu nepoužívá.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Další informace naleznete v tématu [metody (Průvodce programováním v C#)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Vlastnosti jen pro čtení

Počínaje jazykem C# 6 můžete použít definici textu výrazu k implementaci vlastnosti jen pro čtení. K tomu použijte následující syntaxi:

```csharp
PropertyType PropertyName => expression;
```

Následující příklad definuje `Location` třídu, jejíž vlastnost jen pro čtení `Name` je implementována jako definice těla výrazu, která vrací hodnotu soukromého `locationName` pole:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Další informace o vlastnostech naleznete v tématu [Properties (Průvodce programováním v C#)](../classes-and-structs/properties.md).

## <a name="properties"></a>Vlastnosti

Počínaje jazykem C# 7,0 můžete použít definice těla výrazu k implementaci vlastností `get` a `set` přístupových objektů. Následující příklad ukazuje, jak to provést:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Další informace o vlastnostech naleznete v tématu [Properties (Průvodce programováním v C#)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktory

Definice těla výrazu pro konstruktor se obvykle skládá z jednoho výrazu přiřazení nebo volání metody, které zpracovává argumenty konstruktoru nebo inicializuje stav instance.

Následující příklad definuje třídu, `Location` jejíž konstruktor má jeden řetězcový parametr s názvem *Name*. Definice těla výrazu přiřadí argument `Name` Vlastnosti.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Další informace naleznete v tématu [konstruktory (Průvodce programováním v C#)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizační metody

Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, například příkazy, které uvolní nespravované prostředky.

Následující příklad definuje finalizační metodu, která používá definici těla výrazu k označení toho, že finalizační metoda byla volána.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Další informace naleznete v tématu [finalizační metody (Průvodce programováním v C#)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indexery

Podobně jako u vlastností jsou indexery `get` a `set` přistupující objekty tvořeny definicemi těla výrazu `get` , pokud se přistupující objekt skládá z jediného výrazu, který vrací hodnotu nebo `set` přistupující objekt provádí jednoduché přiřazení.

Následující příklad definuje třídu s názvem `Sports` , která obsahuje interní <xref:System.String> pole, které obsahuje názvy pro řadu sportovních. Indexer `get` i `set` přistupující objekty jsou implementovány jako definice textu výrazu.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Další informace najdete v tématu [indexery (Průvodce programováním v C#)](../indexers/index.md).
