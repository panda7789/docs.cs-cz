---
title: Enum – klíčové C# slovo – Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 417f02ce9e8ee88edeb2a4dab88111cae39a8a4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771857"
---
# <a name="enum-c-reference"></a>enum (Referenční dokumentace jazyka C#)

Klíčové slovo `enum` slouží k deklaraci výčtu, odlišného typu, který se skládá ze sady pojmenovaných konstant nazývaných seznam enumerátorů.

Obvykle je vhodné definovat výčet přímo v rámci oboru názvů tak, aby všechny třídy v oboru názvů měly přístup k tomuto rozhraní s rovností pohodlí. Výčty ale mohou být také vnořené v rámci třídy nebo struktury.

Ve výchozím nastavení má první enumerátor hodnotu 0 a hodnota každého úspěšného enumerátoru se zvýší o 1. Například v následujícím výčtu je `Sat` `0``Sun` `1``Mon` `2`a tak dále.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Enumerátory mohou použít inicializátory k přepsání výchozích hodnot, jak je znázorněno v následujícím příkladu.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

V tomto výčtu je sekvence prvků nucená začít od `1` místo `0`. Nicméně, včetně konstanty, která má hodnotu 0, je doporučeno. Další informace naleznete v tématu [výčtové typy](../../programming-guide/enumeration-types.md).

Každý typ výčtu má podkladový typ, který může být libovolný [celočíselný numerický typ](../builtin-types/integral-numeric-types.md). Typ [znaku](char.md) nemůže být základní typ výčtu. Výchozí podkladový typ prvků výčtu je [int](../builtin-types/integral-numeric-types.md). Chcete-li deklarovat výčet jiného integrálního typu, jako je například [Byte](../builtin-types/integral-numeric-types.md), použijte dvojtečku za identifikátor následovaný typem, jak je znázorněno v následujícím příkladu.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Proměnné typu výčtu lze přiřadit libovolnou hodnotu v rozsahu základního typu; hodnoty nejsou omezeny na pojmenované konstanty.

Výchozí hodnotou `enum E` je hodnota vytvořená `(E)0`výrazu.

> [!NOTE]
> Enumerátor nemůže v názvu obsahovat prázdné znaky.

Nadřízený typ Určuje, kolik úložiště je přiděleno pro každý enumerátor. Nicméně explicitní přetypování je nezbytné pro převod z `enum` typu na celočíselný typ. Například následující příkaz přiřadí enumerátor `Sun` proměnné typu [int](../builtin-types/integral-numeric-types.md) pomocí přetypování pro převod z `enum` na `int`.

```csharp
int x = (int)Day.Sun;
```

Když použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> pro výčet, který obsahuje prvky, které mohou být kombinovány s bitovou operací `OR`, atribut má vliv na chování `enum` při použití s některými nástroji. Tyto změny si můžete všimnout, když použijete nástroje, jako jsou metody třídy <xref:System.Console> a vyhodnocovací filtr výrazů. (Viz třetí příklad.)

## <a name="robust-programming"></a>Robustní programování

Stejně jako u jakékoli konstanty jsou všechny odkazy na jednotlivé hodnoty výčtu převedeny na číselné literály v době kompilace. To může způsobit problémy se správou verzí, jak je popsáno v [konstantách](../../programming-guide/classes-and-structs/constants.md).

Přiřazení dalších hodnot novým verzím výčtů nebo změna hodnot členů výčtu v nové verzi může způsobit problémy závislého zdrojového kódu. Hodnoty výčtu jsou často používány v příkazech [Switch](switch.md) . Pokud byly do `enum`ho typu přidány další prvky, lze výchozí oddíl příkazu switch vybrat neočekávaně.

Pokud jiný vývojář používá váš kód, měli byste poskytnout pokyny, jak má jejich kód reagovat, pokud jsou nové prvky přidány do libovolného `enum`ho typu.

## <a name="example"></a>Příklad

V následujícím příkladu je deklarován výčet `Day`. Dva enumerátory jsou explicitně převedeny na celé číslo a přiřazeny celočíselným proměnným.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Příklad

V následujícím příkladu je použita možnost základního typu k deklarování `enum`, jejichž členové jsou typu `long`. Všimněte si, že i když je nadřízený typ výčtu `long`, musí být členy výčtu stále explicitně převedeny na typ `long` pomocí přetypování.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití a vliv atributu <xref:System.FlagsAttribute?displayProperty=nameWithType> u deklarace `enum`.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentáře

Pokud `Flags`odeberete, v příkladu se zobrazí následující hodnoty:

`5`

`5`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Výčtové typy](../../programming-guide/enumeration-types.md)
- [Klíčová slova jazyka C#](index.md)
- [Celočíselné typy](../builtin-types/integral-numeric-types.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Zásady vytváření názvů výčtu](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
