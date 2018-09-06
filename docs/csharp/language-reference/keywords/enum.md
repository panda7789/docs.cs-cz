---
title: enum – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: a64559ac1127f5ec296cf3892dd521c3ad8ac2be
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43875461"
---
# <a name="enum-c-reference"></a>enum (Referenční dokumentace jazyka C#)

`enum` – Klíčové slovo se používá k deklaraci výčtu, odlišný typ, který se skládá ze sady pojmenovaných konstant označovaného jako seznam výčtu.  

Obvykle je vhodné definovat výčet přímo v rámci oboru názvů tak, aby všechny třídy v oboru názvů můžete přistupovat pomocí stejné usnadnění. Výčet však také může být vnořena v rámci třídy nebo struktury.

Ve výchozím nastavení první čítače mají hodnotu 0 a hodnotu každé po sobě jdoucích enumerátoru se zvýší o 1. Například v následujícím výčet `Sat` je `0`, `Sun` je `1`, `Mon` je `2`a tak dále.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Enumerátory lze inicializátory přepsat výchozí hodnoty, jak je znázorněno v následujícím příkladu.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

V tomto výčtu řadu prvků, musí spustit z `1` místo `0`. Nicméně se doporučuje včetně konstantu, která má hodnotu 0. Další informace najdete v tématu [výčtové typy](../../programming-guide/enumeration-types.md).

Každý typ výčtu se základní typ, který může být libovolný integrální typ kromě [char](char.md). Výchozí základní typ výčtu prvků je [int](int.md). Chcete-li deklarovat výčet jiného celočíselného typu, například [bajtů](byte.md), použijte dvojtečku za identifikátorem a potom podle typu, jak je znázorněno v následujícím příkladu.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Seznam schválených typy výčtu [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), nebo [ulong](ulong.md).

Proměnné typu `Day` lze přiřadit jakoukoli hodnotu v rozsahu podkladový typ; hodnoty nejsou omezené na pojmenované konstanty.

Výchozí hodnota `enum E` je hodnotu vytvořenou testovaným výraz `(E)0`.

> [!NOTE]
> Enumerátor nemůže obsahovat prázdné znaky v názvu.

Základní typ Určuje, kolik úložiště je alokováno pro každý čítač. Explicitní přetypování je však potřeba převést z `enum` typ celočíselného typu. Například následující příkaz přiřadí enumerátor `Sun` na proměnnou typu [int](int.md) pomocí přetypování pro převod z `enum` k `int`.

```csharp
int x = (int)Day.Sun;
```

Pokud použijete <xref:System.FlagsAttribute?displayProperty=nameWithType> na výčet, který obsahuje prvky, které můžete kombinovat pomocí logické bitové `OR` operaci, atribut má vliv na chování `enum` při jeho použití s některé nástroje. Můžete si tyto změny při použití nástroje, jako <xref:System.Console> třídy, metody a vyhodnocovací filtr výrazů. (Viz třetí příklad).

## <a name="robust-programming"></a>Robustní programování

Stejně jako u libovolná konstanta se všechny odkazy na jednotlivé hodnoty výčtu převedou na číselné literály v době kompilace. To může způsobit potenciální problémy s verzí, jak je popsáno v [konstanty](../../programming-guide/classes-and-structs/constants.md).

Další hodnoty přiřadit nové verze výčtů nebo změna hodnoty výčtu členů v nové verzi může způsobovat problémy pro závislé zdrojový kód. Hodnoty výčtu jsou často používány v [přepnout](switch.md) příkazy. Pokud další prvky byly přidány do `enum` neočekávaně lze vybrat typ, výchozí část příkazu switch.

Pokud ostatní vývojáři používat váš kód, byste měli poskytnout pokyny o jak svůj kód by měl reagovat při přidání nové prvky k libovolnému `enum` typy.

## <a name="example"></a>Příklad

V následujícím příkladu, výčtu, `Day`, je deklarována. Dva enumerátory jsou explicitně převést na celé číslo a přiřazeny celočíselné proměnné.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Příklad

V následujícím příkladu se používá možnost Základní typ pro deklaraci `enum` jejíž členové jsou typu `long`. Všimněte si, že i když je základní typ výčtu `long`, členy výčtu stále musí být explicitně převeden na typ `long` pomocí přetypování.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje použití a účinku <xref:System.FlagsAttribute?displayProperty=nameWithType> atribut na `enum` deklarace.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Komentáře

Pokud odeberete `Flags`, v příkladu se zobrazí následující hodnoty:

`5`

`5`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)  
- [Výčtové typy](../../programming-guide/enumeration-types.md)  
- [Klíčová slova jazyka C#](index.md)  
- [Tabulka celočíselných typů](integral-types-table.md)  
- [Tabulka předdefinovaných typů](built-in-types-table.md)  
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)  
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)  
- [Zásady vytváření názvů výčtu](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
