---
title: enum – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 634fbd846993d32ae529f87e96fd91857e5c1883
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028276"
---
# <a name="enum-c-reference"></a>enum (Referenční dokumentace jazyka C#)

`enum` – Klíčové slovo se používá k deklaraci výčet, odlišné typ, který se skládá ze sady pojmenované konstanty názvem seznamu enumerátor.  

Obvykle je nejvhodnější definovat výčet přímo v oboru názvů, aby všechny třídy v oboru názvů můžete přistupovat pomocí stejné pohodlí. Výčet však mohou být také vnořené ve třídě nebo struktuře.

Ve výchozím nastavení první enumerátor má hodnotu 0 a hodnotu každé následných enumerátor je zvýšenou o hodnotu 1. Například v následujícím výčtu `Sat` je `0`, `Sun` je `1`, `Mon` je `2`, a tak dále.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Výčty můžete použít inicializátory přepsat výchozí hodnoty, jak je znázorněno v následujícím příkladu.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

V tento výčet je nucen pořadí elementů spuštění z `1` místo `0`. Nicméně se doporučuje včetně konstanta, která má hodnotu 0. Další informace najdete v tématu [výčtové typy](../../programming-guide/enumeration-types.md).

Každý typ výčtu je základní typ, který mohou být jakéhokoli typu integrální s výjimkou [char](char.md). Základní typ výčtu elementů výchozí hodnota je [int](int.md). Výčet integrální jiného typu, například deklarovat [bajtů](byte.md), použijte středník po identifikátor následovaný typem, jak je znázorněno v následujícím příkladu.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Seznam schválených typy výčtu [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), nebo [ulong](ulong.md).

Proměnné typu `Day` lze přiřadit žádnou hodnotu v rozsahu základní typ; hodnoty nejsou omezeny na pojmenované konstanty.

Výchozí hodnota `enum E` je hodnota vyprodukované výraz `(E)0`.

> [!NOTE]
> Enumerátor nesmí obsahovat prázdné znaky v názvu.

Základní typ Určuje, jak velké úložiště je přidělen pro každý enumerátor. Nicméně je nutné převést z explicitní přetypování `enum` typu integrální typ. Například následující příkaz přiřadí enumerátor `Sun` proměnné typu [int](int.md) pomocí přetypování převést z `enum` k `int`.

```csharp
int x = (int)Day.Sun;
```

Když použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> pro výčet, který obsahuje prvky, které mohou být kombinovány s bitové `OR` operace atribut má vliv na chování `enum` při použití s některé nástroje. Tyto změny může dojít, při použití nástrojů, jako <xref:System.Console> třídy metody a vyhodnocovací filtr výrazů. (Podívejte se na třetí příklad).

## <a name="robust-programming"></a>Robustní programování

Stejně jako v jakékoli konstanta všechny odkazy na jednotlivé hodnoty výčtu jsou převedeny na číselné literály v době kompilace. To můžete vytvořit potenciální problémy správy verzí, jak je popsáno v [konstanty](../../programming-guide/classes-and-structs/constants.md).

Přiřazení dalších hodnot k nové verze výčty nebo změna hodnot výčtu členy v nové verzi může způsobit problémy závislé zdrojového kódu. Hodnoty výčtu jsou často používány v [přepínač](switch.md) příkazy. Pokud do nebyly přidané další prvky `enum` typu, výchozí část výrazu switch, který lze vybrat neočekávaně.

Pokud jinými vývojáři použít kódu, měli byste jim poskytnout pokyny o tom, jak by měl svůj kód reagovat Pokud nové prvky jsou přidány do žádné `enum` typy.

## <a name="example"></a>Příklad

V následujícím příkladu, výčet, `Day`, je deklarován. Dva výčty explicitně převést na celé číslo a přiřazený k proměnné celé číslo.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Příklad

V následujícím příkladu je základní typ možnost používá k deklaraci `enum` jejíž členové jsou typu `long`. Všimněte si, že i když je základní typ výčtu `long`, členové výčtu stále musí být explicitně převést na typ `long` pomocí přetypování.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití a účinku <xref:System.FlagsAttribute?displayProperty=nameWithType> atributu u `enum` deklarace.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentáře

Pokud odeberete `Flags`, v příkladu se zobrazí následující hodnoty:

`5`

`5`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

[Referenční dokumentace jazyka C#](../index.md)  
[Výčtové typy](../../programming-guide/enumeration-types.md)  
[Klíčová slova jazyka C#](index.md)  
[Tabulka celočíselných typů](integral-types-table.md)  
[Tabulka předdefinovaných typů](built-in-types-table.md)  
[Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)  
[Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)  
[Zásady vytváření názvů výčtu](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
