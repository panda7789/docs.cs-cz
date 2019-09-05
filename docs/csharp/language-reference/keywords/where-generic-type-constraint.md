---
title: WHERE (omezení obecného typu) – C# referenční informace
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 4e51c5dd226533e7d1ce79a136dba19cbb252f92
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253918"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)

`where` Klauzule v obecné definici určuje omezení pro typy, které se používají jako argumenty pro parametry typu v obecném typu, metodě, delegátu nebo místní funkci. Omezení mohou určovat rozhraní, základní třídy nebo vyžadovat, aby byl obecný typ odkaz, hodnota nebo nespravovaný typ. Deklaruje možnosti, které musí mít argument typu.

Můžete například deklarovat obecnou třídu `MyGenericClass`, například parametr `T` typu implementuje <xref:System.IComparable%601> rozhraní:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Další informace o klauzuli WHERE ve výrazu dotazu naleznete v tématu [Where klauzule](where-clause.md).

`where` Klauzule může také zahrnovat omezení základní třídy. Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní (nebo je základní třída) použitá jako argument typu pro tento obecný typ. Pokud je použito omezení základní třídy, musí být uvedena před všemi ostatními omezeními pro tento parametr typu. Některé typy nejsou povoleny jako omezení základní třídy: <xref:System.Object>, <xref:System.Array>a <xref:System.ValueType>. Před C# 7,3 <xref:System.Enum>,, <xref:System.Delegate>a bylytakézakázányjakoomezenízákladnítřídy.<xref:System.MulticastDelegate> Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

Klauzule může určit, že typ `class` je nebo `struct`. `where` Omezení eliminuje nutnost zadat `System.ValueType`omezení základní třídy. `struct` `System.ValueType` Typ nelze použít jako omezení základní třídy. Následující příklad ukazuje obě `class` omezení a: `struct`

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` Klauzule může`notnull` zahrnovat omezení. `notnull` Omezení omezuje parametr typu na typy, které nejsou null. Tento typ může být [typ hodnoty](struct.md) nebo typ odkazu, který neumožňuje hodnotu null. Omezení je dostupné od začátku v C# 8,0 pro [ `nullable enable` ](../../nullable-references.md#nullable-contexts)kód zkompilovaný v kontextu. `notnull` Na rozdíl od jiných omezení, pokud argument typu v rozporu `notnull` s omezením, kompilátor vygeneruje upozornění namísto chyby. Upozornění se generují jenom v `nullable enable` kontextu. 

> [!IMPORTANT]
> Obecné deklarace, které obsahují `notnull` omezení, mohou být použity v oblivious kontextu s možnou hodnotou null, ale kompilátor neuplatňuje omezení.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Klauzule může také `unmanaged` obsahovat omezení. `where` Omezení omezuje parametr typu na typy známé jako [nespravované typy.](../builtin-types/unmanaged-types.md) `unmanaged` Omezení usnadňuje psaní kódu spolupráce na nízké úrovni v C# `unmanaged` Toto omezení povoluje opakovaně použitelné rutiny ve všech nespravovaných typech. Omezení nelze kombinovat `class` s omezením or `struct`. `unmanaged` Omezení vynutilo, že typ musí `struct`být: `unmanaged`

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Klauzule může také zahrnovat `new()`omezení konstruktoru. `where` Toto omezení umožňuje vytvořit instanci parametru typu pomocí `new` operátoru. [Omezení New ()](new-constraint.md) umožňuje, aby kompilátor věděl, že libovolný zadaný argument typu musí mít přístupný parametr bez parametrů, nebo konstruktor default--. Příklad:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Omezení `new()` se`where` v klauzuli zobrazí jako poslední. Omezení nelze kombinovat `struct` s omezeními nebo `unmanaged`. `new()` Všechny typy vyhovující těmto omezením musí mít přístupný konstruktor bez parametrů, což omezení je `new()` redundantní.

S více parametry typu použijte jednu `where` klauzuli pro každý parametr typu, například:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Omezení můžete také připojit k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Všimněte si, že syntaxe pro popis omezení parametrů typu na delegátech je stejná jako u metod:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Informace o obecných delegátech najdete v tématu [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).

Podrobnosti o syntaxi a použití omezení naleznete v tématu [omezení u parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Úvod do obecných typů](../../programming-guide/generics/index.md)
- [new – omezení](./new-constraint.md)
- [Omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md)
