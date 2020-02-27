---
title: Vyrovnávací paměti pevné velikosti – C# Průvodce programováním
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 9005c425badc5a4ed74e6af3447e563daf61229e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627796"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)

V C#nástroji můžete použít příkaz [fixed](../../language-reference/keywords/fixed-statement.md) pro vytvoření vyrovnávací paměti s pevnou velikostí pole v datové struktuře. Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete metody, které podporují spolupráci se zdroji dat z jiných jazyků nebo platforem. Pevné pole může mít libovolné atributy nebo modifikátory, které jsou povoleny pro běžné členy struktury. Jediným omezením je, že typ pole musí být `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`nebo `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Poznámky

V bezpečném kódu C# struktura obsahující pole neobsahuje prvky pole. Místo toho struktura obsahuje odkaz na prvky. Pole s pevnou velikostí můžete vložit do [struktury](../../language-reference/builtin-types/struct.md) , pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.

Následující `struct` mají velikost 8 bajtů. Pole `pathName` je odkazem:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

`struct` může obsahovat vložené pole v nebezpečném kódu. V následujícím příkladu má pole `fixedBuffer` pevnou velikost. Pomocí příkazu `fixed` vytvoříte ukazatel na první prvek. K prvkům pole přistupujete prostřednictvím tohoto ukazatele. Příkaz `fixed` připnete pole instance `fixedBuffer` do konkrétního umístění v paměti.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Velikost elementu 128 `char` pole je 256 bajtů. Pevná velikost [znaková](../../language-reference/builtin-types/char.md) vyrovnávací paměť vždy bere dva bajty na znak bez ohledu na kódování. To platí i v případě, že jsou vyrovnávací paměti pro znaky zařazeny do metod nebo struktur rozhraní API pomocí `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.

Předchozí příklad ukazuje přístup k polím `fixed` bez připnutí, která je k dispozici od C# 7,3.

Další společné pole s pevnou velikostí je pole [bool](../../language-reference/builtin-types/bool.md) . Prvky v poli `bool` mají velikost vždy jeden bajt. `bool` pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.

> [!NOTE]
> S výjimkou paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md) C# kompilátor a modul CLR (Common Language Runtime) neprovádí žádné kontroly přetečení vyrovnávací paměti zabezpečení. Stejně jako u veškerého nebezpečného kódu buďte opatrní.

Nebezpečné vyrovnávací paměti se liší od regulárních polí následujícími způsoby:

- V nebezpečném kontextu můžete použít jenom nebezpečné vyrovnávací paměti.
- Nebezpečné vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.
- Deklarace pole by měla zahrnovat počet, například `char id[8]`. Nemůžete použít `char id[]`.
- Nebezpečné vyrovnávací paměti mohou být pouze pole instancí struktur v nezabezpečeném kontextu.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [Interoperabilita](../interop/index.md)
