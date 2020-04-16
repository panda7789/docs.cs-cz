---
title: where (omezení obecného typu) - C# Reference
ms.date: 04/15/2020
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 5a56b8058735d3ca786520a82424c79d1975bfc4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463015"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)

Klauzule `where` v obecné definici určuje omezení typů, které se používají jako argumenty pro parametry typu v obecném typu, metodě, delegátovi nebo místní funkci. Omezení můžete určit rozhraní, základní třídy nebo vyžadovat obecný typ, který má být odkaz, hodnota nebo nespravovaný typ. Deklarují schopnosti, které musí mít argument typu.

Můžete například deklarovat `MyGenericClass`obecnou třídu , `T` tak, <xref:System.IComparable%601> aby parametr type implementoval rozhraní:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Další informace o where klauzule ve výrazu dotazu naleznete v tématu [kde klauzule](where-clause.md).

Klauzule `where` může také obsahovat omezení základní třídy. Omezení základní třídy uvádí, že typ, který má být použit jako argument typu pro tento obecný typ, má zadanou třídu jako základní třídu nebo je tou základní třídou. Pokud je použito omezení základní třídy, musí se zobrazit před ostatními omezeními tohoto parametru typu. Některé typy jsou zakázány jako omezení <xref:System.Object> <xref:System.Array>základní <xref:System.ValueType>třídy: , a . Před C# 7.3 <xref:System.Delegate>, <xref:System.MulticastDelegate> <xref:System.Enum>, a byly také zakázány jako omezení základní třídy. Následující příklad ukazuje typy, které lze nyní zadat jako základní třídu:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

V kontextu s možnou hodnotou null v c# 8.0 a novější, nullability typu základní třídy je vynuceno. Pokud základní třída nepodléhá hodnotě `Base`null (například ), argument typu musí být nenulovatelný. Pokud je základní třída null `Base?`(například ), argument typu může být buď typ odkazu s možnou hodnotou null nebo nenulelný. Kompilátor vydá upozornění, pokud je argument typu typ typ s možnou hodnotou null, pokud základní třída nepodléhá hodnotě null.

Klauzule `where` může určit, že `class` typ `struct`je nebo nebo . Omezení `struct` odebere potřebu určit omezení základní `System.ValueType`třídy . Typ `System.ValueType` nelze použít jako omezení základní třídy. Následující příklad ukazuje `class` omezení `struct` a omezení:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

V kontextu s možnou hodnotou null v `class` c# 8.0 a novější, omezení vyžaduje typ, který má být typ nenulelného odkazu. Chcete-li povolit typy `class?` odkazů s možnou hodnotou null, použijte omezení, které umožňuje typy odkazů s možnou i nenulovatelné.

Klauzule `where` může `notnull` obsahovat omezení. Omezení `notnull` omezuje parametr typu na typy s možnou nulou. Tento typ může být [typ hodnoty](../builtin-types/value-types.md) nebo typ odkazu s nemožnou hodnotou. Omezení `notnull` je k dispozici počínaje C# 8.0 pro kód zkompilovaný v [ `nullable enable` kontextu](../../nullable-references.md#nullable-contexts). Na rozdíl od jiných omezení, pokud `notnull` argument typu porušuje omezení, kompilátor vygeneruje upozornění namísto chyby. Upozornění jsou generovány `nullable enable` pouze v kontextu.

> [!IMPORTANT]
> Obecná deklarace, `notnull` které obsahují omezení lze použít v kontextu nevšímat neplatné, ale kompilátor nevynucuje omezení.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

Klauzule `where` může také `unmanaged` obsahovat omezení. Omezení `unmanaged` omezuje parametr typu na typy známé jako [nespravované typy](../builtin-types/unmanaged-types.md). Omezení `unmanaged` usnadňuje zápis kódu meziop nižší úrovně v c#. Toto omezení umožňuje opakovaně použitelné rutiny ve všech nespravovaných typech. Omezení `unmanaged` nelze kombinovat s omezení `class` nebo. `struct` Omezení `unmanaged` vynucuje, že `struct`typ musí být :

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

Klauzule `where` může také obsahovat `new()`omezení konstruktoru , . Toto omezení umožňuje vytvořit instanci parametru `new` typu pomocí operátoru. [New() Constraint](new-constraint.md) umožňuje kompilátoru vědět, že jakýkoli argument typu zadaný musí mít přístupný konstruktor bez parametrů. Příklad:

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

Omezení `new()` se zobrazí `where` jako poslední v klauzuli. Omezení `new()` nelze kombinovat s omezeními `struct` `unmanaged` nebo. Všechny typy splňující tato omezení musí mít přístupný `new()` konstruktor bez parametrů, což je nadbytečné.

S více parametry typu `where` použijte jednu klauzuli pro každý parametr typu, například:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Můžete také připojit omezení k parametrům typu obecných metod, jak je znázorněno v následujícím příkladu:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Všimněte si, že syntaxe k popisu omezení parametrů typu u delegátů je stejná jako syntaxe metod:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Informace o obecných delegátech naleznete [v tématu Obecné delegáty](../../programming-guide/generics/generic-delegates.md).

Podrobnosti o syntaxi a použití omezení naleznete v [tématu Omezení parametrů typu](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Úvod do obecných typů](../../programming-guide/generics/index.md)
- [nové omezení](./new-constraint.md)
- [Omezení parametrů typů](../../programming-guide/generics/constraints-on-type-parameters.md)
