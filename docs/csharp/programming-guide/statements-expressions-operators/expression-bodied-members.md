---
title: Členové s výrazem - Programovací příručka Jazyka C#
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711984"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Členové s výrazem (průvodce programováním jazyka C#)

Definice těla výrazu umožňují poskytnout implementaci člena ve velmi stručné a čitelné podobě. Definici těla výrazu můžete použít vždy, když se logika pro libovolný podporovaný člen, například metoda nebo vlastnost, skládá z jednoho výrazu. Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

kde *výraz* je platný výraz.

Podpora pro definice těla výrazu byla zavedena pro metody a vlastnosti jen pro čtení v C# 6 a byla rozšířena v C# 7.0. Definice těla výrazu lze použít s členy typu uvedenými v následující tabulce:

|Člen  |Podporováno od... |
|---------|---------|
|[Metoda](#methods)  |C# 6 |
|[Vlastnost jen pro čtení](#read-only-properties)   |C# 6  |
|[Vlastnost](#properties)  |C# 7.0 |
|[Konstruktor](#constructors)   |C# 7.0 |
|[Finalizační metoda](#finalizers)     |C# 7.0 |
|[Indexer](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

Metoda s tělovým výrazem se skládá z jednoho výrazu, který vrací hodnotu, jejíž `void`typ odpovídá návratovému typu metody, nebo pro metody, které vracejí , které provádějí některé operace. Například typy, které <xref:System.Object.ToString%2A> přepíší metodu obvykle obsahují jeden výraz, který vrací řetězcovou reprezentaci aktuálního objektu.

Následující příklad definuje `Person` třídu, která <xref:System.Object.ToString%2A> přepíše metodu s definicí těla výrazu. Definuje také metodu, `DisplayName` která zobrazuje název konzoly. Všimněte `return` si, že klíčové `ToString` slovo se nepoužívá v definici těla výrazu.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Další informace naleznete [v tématu Metody (C# Programming Guide)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Vlastnosti jen pro čtení

Počínaje C# 6, můžete použít definici těla výrazu k implementaci vlastnosti jen pro čtení. Chcete-li to provést, použijte následující syntaxi:

```csharp
PropertyType PropertyName => expression;
```

Následující příklad definuje `Location` třídu, jejíž vlastnost jen pro `Name` čtení je implementována `locationName` jako definice těla výrazu, která vrací hodnotu soukromého pole:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Další informace o vlastnostech naleznete v [tématu Vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).

## <a name="properties"></a>Vlastnosti

Počínaje C# 7.0, můžete použít definice těla `get` `set` výrazu k implementaci vlastnosti a přistupující objekty. Následující příklad ukazuje, jak to udělat:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Další informace o vlastnostech naleznete v [tématu Vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktory

Definice těla výrazu pro konstruktor se obvykle skládá z jednoho výrazu přiřazení nebo volání metody, které zpracovává argumenty konstruktoru nebo inicializuje stav instance.

Následující příklad definuje `Location` třídu, jejíž konstruktor má jeden parametr řetězce s názvem *name*. Definice těla výrazu přiřadí `Name` argument vlastnosti.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Další informace naleznete v [tématu Konstruktory (C# Programovací průvodce)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizační metody

Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, jako jsou například příkazy, které vydávají nespravované prostředky.

Následující příklad definuje finalizační metodu, která používá definici těla výrazu k označení, že byla volána finalizační metoda.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Další informace naleznete v tématu [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indexery

Stejně jako s `get` `set` vlastnostmi, indexer a přístupové `get` objekty se skládají z definice těla výrazu, pokud se přistupující objekt skládá z jednoho výrazu, který vrací hodnotu nebo `set` přistupující objekt provádí jednoduché přiřazení.

Následující příklad definuje třídu `Sports` s názvem, která obsahuje vnitřní <xref:System.String> pole, které obsahuje názvy několika sportů. Indexer `get` a `set` přistupující servery jsou implementovány jako definice těla výrazu.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Další informace naleznete v tématu [Indexery (C# Programming Guide)](../indexers/index.md).
