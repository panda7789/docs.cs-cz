---
title: where (omezení obecného typu) (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16be19e342016becd100e2c21434393c3f36f815
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)

`where` Klauzule v definici obecného určuje omezení typy, které se používají jako argumenty pro typ parametry obecného typu, metoda, delegát nebo místní funkce. Omezení můžete určit rozhraní, základní třídy, nebo vyžadovat obecného typu odkaz, hodnota nebo nespravovaný typ. Jejich deklarovat možnosti, které musí mít argument typu.

Můžou například deklarovat obecná třída `MyGenericClass`, tak, že parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Další informace o where klauzule ve výrazu dotazu, najdete v části [kde klauzule](where-clause.md).

`where` Klauzule může také obsahovat omezení základní třídy. Základní třída omezení stavy, že typ má být použit jako typ argumentu pro tento obecný typ má jako základní třída pro zadanou třídu (nebo je, že základní třída) má být použit jako typ argumentu pro obecného typu. Pokud se používá k omezení základní třídy, musí být před jiná omezení u tohoto typu parametru. Některé typy nejsou povoleny jako základní třída omezení: <xref:System.Object>, <xref:System.Array>, a <xref:System.ValueType>. Před C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, a <xref:System.MulticastDelegate> byly také nepovolené jako základní třída omezení. Následující příklad ukazuje typy, které nyní je možné zadat jako základní třída:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` Klauzule můžete určit, zda je typ `class` nebo `struct`. `struct` Omezení eliminuje nutnost zadejte základní třídu omezení `System.ValueType`. `System.ValueType` Typ nemusí použít jako základní třída omezení. Následující příklad ukazuje, jak `class` a `struct` omezení:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Klauzule může také zahrnovat `unmanaged` omezení. `unmanaged` Omezení omezuje parametr typu pro typy, které jsou známé jako **nespravované typy**. **Nespravované typu** je typ, který není typu odkazu a neobsahuje pole typu odkaz na libovolnou úroveň vnoření. `unmanaged` Omezení usnadňuje psaní nízké úrovně spolupráce kódu v jazyce C#. Toto omezení umožňuje opakovaně použitelné rutiny všech nespravované typů. `unmanaged` Omezení nelze kombinovat s `class` nebo `struct` omezení. `unmanaged` Vynucuje omezení, musí být typ `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` Klauzule může také zahrnovat konstruktor omezení, `new()`. Aby omezení umožňuje vytvořit instanci typu parametr pomocí `new` operátor. [New() omezení](new-constraint.md) umožňuje kompilátoru vědět, že musí mít přístupné některý typ argument zadaný bez parametrů--nebo--výchozí konstruktor. Příklad:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Omezení, zobrazí se v poslední `where` klauzule. `new()` Omezení nelze kombinovat s `struct` nebo `unmanaged` omezení. Všechny typy, které splňují tato omezení musí mít k dostupný konstruktor bez parametrů, což `new()` redundantní omezení.

S více typů parametrů, použijte jednu `where` klauzuli pro každý parametr typu, například:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Můžete také připojit omezení zadání parametrů Obecné metody, jak je znázorněno v následujícím příkladu:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Všimněte si, že syntaxe pro popis typu parametru omezení delegáti je stejná jako u metody:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Informace pro obecné delegáty najdete v tématu [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).

Podrobnosti o syntaxi a použití omezení najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [new – omezení](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
