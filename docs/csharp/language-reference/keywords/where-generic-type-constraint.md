---
title: where (omezení obecného typu) (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 94db10c81af55030dfcf6e210a86658c84868e42
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961078"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)

`where` Klauzule v definici obecného určuje omezení na typy, které se používají jako argumenty pro parametry typu v obecného typu, metody, delegáta nebo místní funkce. Omezení můžete určit základní třídy, rozhraní nebo vyžadují být typu odkaz, hodnota nebo nespravovaný typ obecného typu. Kterou deklarují funkce, které musí mít argument typu.

Například je možné deklarovat obecná třída `MyGenericClass`, tak, aby parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Další informace o where – klauzule ve výrazu dotazu naleznete v tématu [kde klauzule](where-clause.md).

`where` Klauzule může také obsahovat omezení základní třídy. Omezení základní třídy uvádí, že typ má být použit jako argument typu pro obecný typu má zadanou třídu jako základní třídu (nebo je, že základní třídy) má být použit jako argument typu pro obecný typu. Pokud se používá k omezení základní třídy, musí být uvedena před všemi ostatními omezeními u tohoto parametru typu. Některé typy nejsou povoleny jako základní třída omezení: <xref:System.Object>, <xref:System.Array>, a <xref:System.ValueType>. Před C# 7.3 <xref:System.Enum>, <xref:System.Delegate>, a <xref:System.MulticastDelegate> byly také povolena jako omezení základní třídy. Následující příklad ukazuje typy, které teď můžou být specifikované jako základní třídu:

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` Klauzule můžete určit, že je typem `class` nebo `struct`. `struct` Omezení eliminuje nutnost zadat omezení základní třídy `System.ValueType`. `System.ValueType` Typ nelze použít jako omezení základní třídy. Následující příklad ukazuje, jak `class` a `struct` omezení:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Může také obsahovat klauzuli `unmanaged` omezení. `unmanaged` Omezení omezuje parametr typu pro typy označované jako **nespravovaného typy**. **Nespravovaný typ** je typ, který není typem odkazu a neobsahuje pole typu odkazu na libovolné úrovni vnoření. `unmanaged` Omezení usnadňuje psaní nízké úrovně vzájemné spolupráce kódu v jazyce C#. Toto omezení umožňuje opakovaně použitelných rutin do všech nespravovaných typů. `unmanaged` Omezení nelze kombinovat s `class` nebo `struct` omezení. `unmanaged` Vynucuje omezení, musí být typu `struct`:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` Klauzule může také obsahovat omezení konstruktoru `new()`. Že omezení díky tomu je možné vytvořit instanci typu pomocí parametru `new` operátor. [Omezení new()](new-constraint.md) umožňuje kompilátoru vědět, že všechny zadaný argument typu musí mít k dispozici přístup bez parametrů--nebo--výchozí konstruktor. Příklad:

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` Omezení, zobrazí se v poslední `where` klauzuli. `new()` Omezení nelze kombinovat s `struct` nebo `unmanaged` omezení. Všechny typy splňující tato omezení musí mít dostupný konstruktor bez parametrů, takže `new()` omezení redundantní.

S více typy parametrů, použijte jednu `where` klauzule pro každý z parametrů typu, například:

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Můžete také připojit omezení k zadání parametrů Obecné metody, jak je znázorněno v následujícím příkladu:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Všimněte si, že syntaxe pro popis omezení parametru typu na delegáty je stejné jako u metod:

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Informace o obecných delegátů, naleznete v tématu [obecných delegátů](../../../csharp/programming-guide/generics/generic-delegates.md).

Podrobnosti o syntaxi a použití omezení najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [new – omezení](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
