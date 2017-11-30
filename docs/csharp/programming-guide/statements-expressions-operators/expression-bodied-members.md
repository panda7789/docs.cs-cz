---
title: "Výraz vozidlo členové (C# programování průvodce)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ead1e474fe87bd9fbd0f972bc0f2fc4fefc12ecf
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="expression-bodied-members-c-programming-guide"></a>Výraz vozidlo členové (C# programovací průvodce)
Výraz definice textu umožňují poskytovat implementace člena ve formuláři velmi stručným a čitelné. Definici výraz text můžete použít vždy, když logiku pro všechny podporované člena, jako je například metody nebo vlastnosti, se skládá z jednoho výrazu. Definici výraz text má následující obecné syntaxi:

```csharp
member => expression;
```

kde *výraz* je platný výraz. 

Podpora pro výraz text definice byla zavedená pro metody a vlastnosti získat přístupové objekty v C# 6 a byla rozšířena v C# 7. Výraz definice textu lze použít s členy typu uvedené v následující tabulce: 

|Člen  |Podporované od systému... |
|---------|---------|
|[– Metoda](#methods)  |C# 6 |
|[Konstruktor](#constructors)   |C# 7 |
|[Finalizační metodu](#finalizers)     |C# 7 |
|[Vlastnost Get](#property-get-statements)  |C# 6 |
|[Sada vlastností](#property-set-statements)  |C# 7 |
|[Indexer](#indexers)       |C# 7 |

## <a name="methods"></a>Metody

Výraz vozidlo metoda se skládá z jediného výrazu, která vrátí hodnotu, jejíž typ odpovídá návratový typ metody, nebo pro metody, které vracejí `void`, který provede nějaké operace. Například, že přepsání typy <xref:System.Object.ToString%2A> metoda obvykle obsahují jeden výraz, který vrátí řetězcovou reprezentaci aktuálního objektu. 

V následujícím příkladu definuje `Person` třídu, která přepisuje <xref:System.Object.ToString%2A> metoda k definici textu výraz. Také definuje `Show` metoda, která zobrazí název ke konzole. Všimněte si, že `return` – klíčové slovo není používáno ve `ToString` definice textu výrazu.

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Další informace najdete v tématu [metody (C# programování průvodce)](../classes-and-structs/methods.md).
 
## <a name="constructors"></a>Konstruktory

Definici výraz text pro konstruktor se obvykle skládá z jedné přiřazení výraz nebo volání metody, která zpracuje argumenty v konstruktoru nebo inicializuje stav instance. 

V následujícím příkladu definuje `Location` třídu, jejíž konstruktor má jednoho řetězce parametr s názvem *název*. Definice textu výraz přiřadí argument `Name` vlastnost.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Další informace najdete v tématu [konstruktory (C# programování průvodce)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finalizační metody

Definici výraz text finalizační metody obvykle obsahuje čištění příkazy, jako je například příkazy, které uvolnění nespravovaných prostředků.

V následujícím příkladu definuje finalizační metodu, který používá definici textu výraz k označení, že byla volána finalizační metodu.

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Další informace najdete v tématu [finalizační metody (C# Průvodce programováním)](../classes-and-structs/destructors.md).

## <a name="property-get-statements"></a>Property get – příkazy

Pokud chcete implementovat vlastnost načtení přístupového objektu sami, můžete použít definici textu výraz pro jeden výrazy, které jednoduše vrátit hodnotu vlastnosti. Všimněte si, že `return` příkaz nepoužívá.

V následujícím příkladu definuje `Location.Name` vlastnost, jejichž vlastnost načtení přístupového objektu vrací hodnotu privátní `locationName` pole, která zálohuje vlastnost. 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Vlastnosti jen pro čtení, které použijte definici textu výraz lze provést bez explicitního `set` příkaz. Syntaxe je následující:

```csharp
PropertyName => returnValue;
```

V následujícím příkladu definuje `Location` třídy jehož jen pro čtení `Name` vlastnost je implementovaný jako definice textu výraz, který vrací hodnotu privátní `locationName` pole.

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Další informace najdete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Vlastnost set – příkazy

Pokud zvolíte možnost implementovat vlastnosti sami, můžete použít definici textu výraz pro výraz jeden řádek, který přiřazuje hodnotu pole, která zálohuje vlastnost.

V následujícím příkladu definuje `Location.Name` vlastnost, jehož vlastnost nastavena příkaz přiřadí privátní jeho vstupní argument `locationName` pole, která zálohuje vlastnost.

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Další informace najdete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Indexery

Jako vlastnosti indexer get a přístupových objektů sady obsahovat definice textu výraz Pokud přistupující objekt get se skládá z jednoho příkazu, který vrátí hodnotu, nebo přistupující objekt set provede jednoduché přiřazení.

Následující příklad definuje třídu s názvem `Sports` , který obsahuje interní <xref:System.String> pole, které obsahuje názvy počtu sportu. Get indexeru a přístupových objektů sady jsou implementované jako výraz text definice.

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Další informace najdete v tématu [indexery (C# Průvodce programováním)](../indexers/index.md).

