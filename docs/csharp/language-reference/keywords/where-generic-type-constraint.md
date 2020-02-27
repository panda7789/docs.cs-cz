---
title: WHERE (omezení obecného typu) – C# referenční informace
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: d236420c5019f7529b729155b13df50807dc1dab
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626708"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)

Klauzule `where` v obecné definici určuje omezení pro typy, které se používají jako argumenty parametrů typu v obecném typu, metodě, delegátu nebo místní funkci. Omezení mohou určovat rozhraní, základní třídy nebo vyžadovat, aby byl obecný typ odkaz, hodnota nebo nespravovaný typ. Deklaruje možnosti, které musí mít argument typu.

Například můžete deklarovat obecnou třídu, `MyGenericClass`, tak, že parametr typu `T` implementuje rozhraní <xref:System.IComparable%601>:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Další informace o klauzuli WHERE ve výrazu dotazu naleznete v tématu [Where klauzule](where-clause.md).

Klauzule `where` může také zahrnovat omezení základní třídy. Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní (nebo je základní třída) použitá jako argument typu pro tento obecný typ. Pokud je použito omezení základní třídy, musí být uvedena před všemi ostatními omezeními pro tento parametr typu. Některé typy nejsou povoleny jako omezení základní třídy: <xref:System.Object>, <xref:System.Array>a <xref:System.ValueType>. Před C# 7,3, <xref:System.Enum>, <xref:System.Delegate>a <xref:System.MulticastDelegate> byly také zakázány jako omezení základní třídy. Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Klauzule `where` může určit, že typ je `class` nebo `struct`. Omezení `struct` eliminuje nutnost zadat omezení základní třídy `System.ValueType`. Typ `System.ValueType` nesmí být použit jako omezení základní třídy. Následující příklad ukazuje omezení `class` i `struct`:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

Klauzule `where` může zahrnovat omezení `notnull`. Omezení `notnull` omezuje parametr typu na typy, které neumožňují hodnotu null. Tento typ může být [typ hodnoty](../builtin-types/value-types.md) nebo typ odkazu, který neumožňuje hodnotu null. Omezení `notnull` je k dispozici počínaje C# verzí 8,0 pro kód zkompilovaný v [kontextu`nullable enable`](../../nullable-references.md#nullable-contexts). Na rozdíl od jiných omezení, pokud argument typu narušuje omezení `notnull`, kompilátor vygeneruje upozornění namísto chyby. Upozornění se generují jenom v kontextu `nullable enable`.

> [!IMPORTANT]
> Obecné deklarace, které zahrnují omezení `notnull` lze použít v kontextu s možnou hodnotou null, ale kompilátor neuplatňuje omezení.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Klauzule `where` může také zahrnovat omezení `unmanaged`. Omezení `unmanaged` omezuje parametr typu na typy známé jako [nespravované typy](../builtin-types/unmanaged-types.md). Omezení `unmanaged` usnadňuje psaní kódu spolupráce na nízké úrovni v C#. Toto omezení povoluje opakovaně použitelné rutiny ve všech nespravovaných typech. Omezení `unmanaged` nelze kombinovat s omezením `class` nebo `struct`. Omezení `unmanaged` vynutilo, že typ musí být `struct`:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Klauzule `where` může také zahrnovat omezení konstruktoru `new()`. Toto omezení umožňuje vytvořit instanci parametru typu pomocí operátoru `new`. [Omezení New ()](new-constraint.md) umožňuje kompilátoru zjistit, že libovolný zadaný argument typu musí mít přístupný konstruktor bez parametrů. Příklad:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Omezení `new()` se v klauzuli `where` zobrazí jako poslední. Omezení `new()` nelze kombinovat s omezeními `struct` nebo `unmanaged`. Všechny typy, které by splňovaly tato omezení, musí mít přístupný konstruktor bez parametrů, aby omezení `new()` bylo redundantní.

S více parametry typu použijte jednu klauzuli `where` pro každý parametr typu, například:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Omezení můžete také připojit k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Všimněte si, že syntaxe pro popis omezení parametrů typu na delegátech je stejná jako u metod:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Informace o obecných delegátech najdete v tématu [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).

Podrobnosti o syntaxi a použití omezení naleznete v tématu [omezení u parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [C#Odkaz](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Úvod do obecných typů](../../programming-guide/generics/index.md)
- [new – omezení](./new-constraint.md)
- [Omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md)
