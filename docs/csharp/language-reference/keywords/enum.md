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
ms.openlocfilehash: fb11fb1a81b8407e2585e32d4217e08a75ea19b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605816"
---
# <a name="enum-c-reference"></a>enum (Referenční dokumentace jazyka C#)

`enum` Klíčové slovo se používá k deklaraci výčtu, odlišného typu, který se skládá ze sady pojmenovaných konstant označované jako seznam enumerátorů.

Obvykle je vhodné definovat výčet přímo v rámci oboru názvů tak, aby všechny třídy v oboru názvů měly přístup k tomuto rozhraní s rovností pohodlí. Výčty ale mohou být také vnořené v rámci třídy nebo struktury.

Ve výchozím nastavení má první enumerátor hodnotu 0 a hodnota každého úspěšného enumerátoru se zvýší o 1. Například v následujícím výčtu `Sat` je `0`, `Sun` `1`je ,atakdále.`Mon` `2`

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Enumerátory mohou použít inicializátory k přepsání výchozích hodnot, jak je znázorněno v následujícím příkladu.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

V tomto výčtu je sekvence prvků nucená začít od `1` `0`místo. Nicméně, včetně konstanty, která má hodnotu 0, je doporučeno. Další informace naleznete v tématu [výčtové typy](../../programming-guide/enumeration-types.md).

Každý typ výčtu má podkladový typ, který může být libovolný [celočíselný numerický typ](../builtin-types/integral-numeric-types.md). Typ [znaku](char.md) nemůže být základní typ výčtu. Výchozí podkladový typ prvků výčtu je [int](../builtin-types/integral-numeric-types.md). Chcete-li deklarovat výčet jiného integrálního typu, jako je například [Byte](../builtin-types/integral-numeric-types.md), použijte dvojtečku za identifikátor následovaný typem, jak je znázorněno v následujícím příkladu.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Proměnné typu výčtu lze přiřadit libovolnou hodnotu v rozsahu základního typu; hodnoty nejsou omezeny na pojmenované konstanty.

Výchozí hodnota `enum E` je hodnota vytvořená výrazem `(E)0`.

> [!NOTE]
> Enumerátor nemůže v názvu obsahovat prázdné znaky.

Nadřízený typ Určuje, kolik úložiště je přiděleno pro každý enumerátor. Nicméně explicitní přetypování je nezbytné pro převod `enum` typu na celočíselný typ. Například následující `Sun` příkaz přiřadí enumerátor proměnné typu [int](../builtin-types/integral-numeric-types.md) pomocí přetypování pro převod z `enum` na. `int`

```csharp
int x = (int)Day.Sun;
```

Když použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> na výčet, který obsahuje prvky, které mohou být kombinovány s `OR` bitovou operací, atribut `enum` má vliv na chování při použití s některými nástroji. Tyto změny si můžete všimnout, když použijete nástroje, jako <xref:System.Console> jsou metody třídy a vyhodnocovací filtr výrazů. (Viz třetí příklad.)

## <a name="robust-programming"></a>Robustní programování

Stejně jako u jakékoli konstanty jsou všechny odkazy na jednotlivé hodnoty výčtu převedeny na číselné literály v době kompilace. To může způsobit problémy se správou verzí, jak [](../../programming-guide/classes-and-structs/constants.md)je popsáno v konstantách.

Přiřazení dalších hodnot novým verzím výčtů nebo změna hodnot členů výčtu v nové verzi může způsobit problémy závislého zdrojového kódu. Hodnoty výčtu jsou často používány v příkazech [Switch](switch.md) . Pokud byly do `enum` typu přidány další prvky, lze výchozí oddíl příkazu switch vybrat neočekávaně.

Pokud jiný vývojář používá váš kód, měli byste poskytnout pokyny, jak by měl kód reagovat, pokud jsou přidány nové prvky do `enum` libovolného typu.

## <a name="example"></a>Příklad

V následujícím příkladu je deklarován výčet `Day`,. Dva enumerátory jsou explicitně převedeny na celé číslo a přiřazeny celočíselným proměnným.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Příklad

V následujícím příkladu je použita možnost základního typu k deklaraci `enum` , jejichž členové jsou typu. `long` Všimněte si, že i když je `long`podkladový typ výčtu, musí být členy výčtu stále explicitně převedeny na typ `long` pomocí přetypování.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití a účinek <xref:System.FlagsAttribute?displayProperty=nameWithType> atributu `enum` deklarace.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentáře

Pokud odeberete `Flags`, v příkladu se zobrazí následující hodnoty:

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
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
- [Zásady vytváření názvů výčtu](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
