---
title: Vyrovnávací paměti pevné velikosti – Průvodce programováním v C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 932ff3d57995ce47c4b74e8e888a479f0d09d0ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397425"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)

V jazyce C# můžete použít příkaz [fixed](../../language-reference/keywords/fixed-statement.md) pro vytvoření vyrovnávací paměti s pevnou velikostí pole v datové struktuře. Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete metody, které podporují spolupráci se zdroji dat z jiných jazyků nebo platforem. Pevné pole může mít libovolné atributy nebo modifikátory, které jsou povoleny pro běžné členy struktury. Jediným omezením je, že typ pole musí být `bool` , `byte` ,,, `char` `short` `int` , `long` , `sbyte` , `ushort` , `uint` , `ulong` , `float` , nebo `double` .

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Poznámky

V bezpečném kódu struktura C#, která obsahuje pole, neobsahuje prvky pole. Místo toho struktura obsahuje odkaz na prvky. Pole s pevnou velikostí můžete vložit do [struktury](../../language-reference/builtin-types/struct.md) , pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.

Velikost následujícího `struct` není závislá na počtu prvků v poli, protože `pathName` je to odkaz:

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

`struct`Může obsahovat vložené pole v nebezpečném kódu. V následujícím příkladu `fixedBuffer` má pole pevnou velikost. Pomocí příkazu vytvoříte `fixed` ukazatel na první prvek. K prvkům pole přistupujete prostřednictvím tohoto ukazatele. `fixed`Příkaz připnete `fixedBuffer` pole instance do konkrétního umístění v paměti.

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

Velikost pole elementu 128 `char` je 256 bajtů. Pevná velikost [znaková](../../language-reference/builtin-types/char.md) vyrovnávací paměť vždy bere dva bajty na znak bez ohledu na kódování. To platí i v případě, že jsou vyrovnávací paměti pro znaky zařazeny do metod nebo struktur rozhraní API pomocí `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi` . Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.

Předchozí příklad ukazuje přístup k `fixed` polím bez připnutí, která je k dispozici počínaje jazykem C# 7,3.

Další společné pole s pevnou velikostí je pole [bool](../../language-reference/builtin-types/bool.md) . Prvky v `bool` poli mají velikost vždy jeden bajt. `bool`pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.

Vyrovnávací paměti pevné velikosti jsou kompilovány s <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> , který instruuje modul CLR (Common Language Runtime), který typ obsahuje nespravované pole, které může potenciálně přetečení. To se podobá paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md), která v modulu CLR automaticky povoluje funkce detekce přetečení vyrovnávací paměti. Předchozí příklad ukazuje, jak může vyrovnávací paměť s pevnou velikostí existovat v `unsafe struct` .

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

Kompilátorem generovaný C# pro `Buffer` je následující atribut:

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

Vyrovnávací paměti pevné velikosti se od standardních polí liší následujícími způsoby:

- Dá se použít jenom v [nezabezpečeném](../../language-reference/keywords/unsafe.md) kontextu.
- Mohou být pouze poli instancí struktur.
- Jsou to vždycky vektory nebo jednorozměrná pole.
- Deklarace by měla obsahovat délku, například `fixed char id[8]` . Nemůžete použít `fixed char id[]` .

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Nezabezpečený kód a ukazatele](index.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [Interoperabilita](../interop/index.md)
