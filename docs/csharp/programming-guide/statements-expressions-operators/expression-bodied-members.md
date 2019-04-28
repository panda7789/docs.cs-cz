---
title: Členové tvoření - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709988"
---
# <a name="expression-bodied-members-c-programming-guide"></a>Členové tvoření (C# programovací příručka)

Definice těla výrazu umožňují poskytovat implementace člena ve velmi stručným čitelné formy. Definice těla výrazu můžete použít pokaždé, když se logika pro všechny podporované členu, například metody nebo vlastnosti, se skládá z jednoho výrazu. Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

kde *výraz* je platný výraz.

Podpora pro definice těla výrazu byla zavedená pro metody a vlastnosti jen pro čtení v C# 6 a se rozbalil v C# 7.0. Definice těla výrazu jde použít s členy typu uvedené v následující tabulce:

|Člen  |Podporované od systému... |
|---------|---------|
|[– Metoda](#methods)  |C# 6 |
|[Vlastnost jen pro čtení](#read-only-properties)   |C# 6  |
|[Vlastnost](#properties)  |C# 7.0 |
|[Konstruktor](#constructors)   |C# 7.0 |
|[Finalizační metody](#finalizers)     |C# 7.0 |
|[Indexer](#indexers)       |C# 7.0 |

## <a name="methods"></a>Metody

S výrazem v těle metody obsahuje jediný výraz, který vrací hodnotu, jehož typ odpovídá návratový typ metody nebo pro metody, které vracejí `void`, který provede některé operace. Například typy toto přepsání <xref:System.Object.ToString%2A> metoda obvykle zahrnují jeden výraz, který vrátí řetězcovou reprezentaci aktuálního objektu.

Následující příklad definuje `Person` třídu, která přepíše <xref:System.Object.ToString%2A> metodu s definici tělo výrazu. Definuje také `DisplayName` metodu, která zobrazuje název do konzoly. Všimněte si, že `return` – klíčové slovo se nepoužívá `ToString` definice těla výrazu.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Další informace najdete v tématu [Methods (C# Programming Guide)](../classes-and-structs/methods.md).

## <a name="read-only-properties"></a>Vlastnosti jen pro čtení

Počínaje C# 6, definice těla výrazu můžete použít k implementaci vlastnost jen pro čtení. K tomuto účelu použijte následující syntaxi:

```csharp
PropertyType PropertyName => expression;
```

Následující příklad definuje `Location` třídy, jejichž jen pro čtení `Name` vlastnost je implementovaný jako definici tělo výrazu, který vrací hodnotu privátní `locationName` pole:

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Další informace o vlastnostech najdete v tématu [vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).

## <a name="properties"></a>Vlastnosti

Počínaje C# 7.0, definice těla výrazu můžete použít k implementaci vlastnost `get` a `set` přistupující objekty. Následující příklad ukazuje, jak to udělat:

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

Další informace o vlastnostech najdete v tématu [vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).

## <a name="constructors"></a>Konstruktory

Definice těla výrazu pro konstruktor se obvykle skládá z výrazu přiřazení jednoho nebo volání metody, která zpracuje argumenty konstruktoru nebo inicializuje stav instance.

Následující příklad definuje `Location` třídy, jejíž konstruktor má jeden řetězcový parametr s názvem *název*. Definice textu výrazu přiřadí argument `Name` vlastnost.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Další informace najdete v tématu [konstruktory (C# Programming Guide)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizační metody

Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, jako je například příkazy, které uvolnění nespravovaných prostředků.

Následující příklad definuje finalizační metodu, která používá definici tělo výrazu k označení, že byla zavolána finalizační metodu.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Další informace najdete v tématu [finalizační metody (C# Programming Guide)](../classes-and-structs/destructors.md).

## <a name="indexers"></a>Indexery

Jako jsou vlastnosti indexeru pro operace get a přístupové objekty set se skládají z definice těla výrazu Pokud přistupující objekt get se skládá z jednoho příkazu, který vrací hodnotu, nebo přístupový objekt set provádí jednoduché přiřazení.

Následující příklad definuje třídu s názvem `Sports` , který obsahuje interní <xref:System.String> pole, které obsahuje názvy počet sportu. Get indexeru a přístupové objekty set jsou implementovány jako definice těla výrazu.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

Další informace najdete v tématu [indexery (C# Programming Guide)](../indexers/index.md).
