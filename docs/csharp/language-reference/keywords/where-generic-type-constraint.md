---
title: WHERE (omezení obecného typu) – Reference jazyka C#
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 406c710cd884363c32b98336717732a09b3d1fc1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401872"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)

`where`Klauzule v obecné definici určuje omezení pro typy, které se používají jako argumenty pro parametry typu v obecném typu, metodě, delegátu nebo místní funkci. Omezení mohou určovat rozhraní, základní třídy nebo vyžadovat, aby byl obecný typ odkaz, hodnota nebo nespravovaný typ. Deklaruje možnosti, které musí mít argument typu.

Můžete například deklarovat obecnou třídu, například `MyGenericClass` parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Další informace o klauzuli WHERE ve výrazu dotazu naleznete v tématu [Where klauzule](where-clause.md).

`where`Klauzule může také zahrnovat omezení základní třídy. Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní třídu nebo je základní třída. Pokud je použito omezení základní třídy, musí být uvedena před všemi ostatními omezeními pro tento parametr typu. Některé typy nejsou povoleny jako omezení základní třídy: <xref:System.Object> , <xref:System.Array> a <xref:System.ValueType> . Před C# 7,3, <xref:System.Enum> , a <xref:System.Delegate> <xref:System.MulticastDelegate> byly také zakázány jako omezení základní třídy. Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:

[!code-csharp[using an interface constraint](snippets/GenericWhereConstraints.cs#2)]

V kontextu s možnou hodnotou null v jazyce C# 8,0 a novějším je vynutila hodnota null typu základní třídy. Pokud základní třída nemůže mít hodnotu null (například `Base` ), argument typu nesmí mít hodnotu null. Pokud je základní třídou Nullable (například `Base?` ), může být argumentem typu buď typ odkazu s možnou hodnotou null, nebo odkaz, který nepovoluje hodnotu null. Kompilátor vydá upozornění, pokud je argumentem typu typ odkazu s možnou hodnotou null, pokud základní třída nemůže mít hodnotu null.

`where`Klauzule může určit, že typ je `class` nebo `struct` . `struct`Omezení eliminuje nutnost zadat omezení základní třídy `System.ValueType` . `System.ValueType`Typ nelze použít jako omezení základní třídy. Následující příklad ukazuje obě `class` `struct` omezení a:

[!code-csharp[using the class and struct constraints](snippets/GenericWhereConstraints.cs#3)]

V kontextu s možnou hodnotou null v jazyce C# 8,0 a vyšší `class` omezení vyžaduje, aby typ byl odkazový typ, který nemůže být null. Chcete-li povolit typy odkazů s možnou hodnotou null, použijte `class?` omezení, které umožňuje přístup s možnou hodnotou null i odkaz na jiný typ.

`where`Klauzule může zahrnovat `notnull` omezení. `notnull`Omezení omezuje parametr typu na typy, které nejsou null. Tento typ může být [typ hodnoty](../builtin-types/value-types.md) nebo typ odkazu, který neumožňuje hodnotu null. `notnull`Omezení je k dispozici počínaje jazykem C# 8,0 pro kód zkompilovaný v [ `nullable enable` kontextu](../../nullable-references.md#nullable-contexts). Na rozdíl od jiných omezení, pokud argument typu v rozporu s `notnull` omezením, kompilátor vygeneruje upozornění namísto chyby. Upozornění se generují jenom v `nullable enable` kontextu.

> [!IMPORTANT]
> Obecné deklarace, které obsahují `notnull` omezení, mohou být použity v oblivious kontextu s možnou hodnotou null, ale kompilátor neuplatňuje omezení.

[!code-csharp[using the nonnull constraint](snippets/GenericWhereConstraints.cs#NotNull)]

`where`Klauzule může také obsahovat `unmanaged` omezení. `unmanaged`Omezení omezuje parametr typu na typy známé jako [nespravované typy](../builtin-types/unmanaged-types.md). `unmanaged`Omezení usnadňuje psaní kódu spolupráce na nízké úrovni v jazyce C#. Toto omezení povoluje opakovaně použitelné rutiny ve všech nespravovaných typech. `unmanaged`Omezení nelze kombinovat s `class` `struct` omezením or. `unmanaged`Omezení vynutilo, že typ musí být `struct` :

[!code-csharp[using the unmanaged constraint](snippets/GenericWhereConstraints.cs#4)]

`where`Klauzule může také zahrnovat omezení konstruktoru `new()` . Toto omezení umožňuje vytvořit instanci parametru typu pomocí `new` operátoru. [Omezení New ()](new-constraint.md) umožňuje kompilátoru zjistit, že libovolný zadaný argument typu musí mít přístupný konstruktor bez parametrů. Příklad:

[!code-csharp[using the new constraint](snippets/GenericWhereConstraints.cs#5)]

`new()`Omezení se v klauzuli zobrazí jako poslední `where` . `new()`Omezení nelze kombinovat s `struct` `unmanaged` omezeními nebo. Všechny typy vyhovující těmto omezením musí mít přístupný konstruktor bez parametrů, což omezení je `new()` redundantní.

S více parametry typu použijte jednu `where` klauzuli pro každý parametr typu, například:

[!code-csharp[using multiple where constraints](snippets/GenericWhereConstraints.cs#6)]

Omezení můžete také připojit k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#7)]

Všimněte si, že syntaxe pro popis omezení parametrů typu na delegátech je stejná jako u metod:

[!code-csharp[where constraints with generic methods](snippets/GenericWhereConstraints.cs#8)]

Informace o obecných delegátech najdete v tématu [Obecné delegáty](../../programming-guide/generics/generic-delegates.md).

Podrobnosti o syntaxi a použití omezení naleznete v tématu [omezení u parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Úvod do obecných typů](../../programming-guide/generics/index.md)
- [nové omezení](./new-constraint.md)
- [Omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md)
