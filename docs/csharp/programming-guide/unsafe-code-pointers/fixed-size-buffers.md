---
title: Buffery s pevnou velikostí – programovací průvodce C#
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157023"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)

V C# můžete použít [příkaz fixed](../../language-reference/keywords/fixed-statement.md) k vytvoření vyrovnávací paměti s polem s pevnou velikostí v datové struktuře. Vyrovnávací paměti s pevnou velikostí jsou užitečné při psaní metod, které interop se zdroji dat z jiných jazyků nebo platforem. Pevné pole může trvat všechny atributy nebo modifikátory, které jsou povoleny pro pravidelné členy struktury. Jediným omezením je, že `bool`typ `byte` `char`pole `short` `int`musí `long` `sbyte`být `ushort` `uint`, `ulong` `float`, `double`, , , , , , , , , nebo .

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Poznámky

V bezpečném kódu c# struktura, která obsahuje pole neobsahuje prvky pole. Místo toho struktura obsahuje odkaz na prvky. Pole s pevnou velikostí můžete vložit [do struktury,](../../language-reference/builtin-types/struct.md) pokud se používá v [nebezpečném](../../language-reference/keywords/unsafe.md) bloku kódu.

Velikost následujícího `struct` nezávisí na počtu prvků v poli, `pathName` protože je odkaz:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` může obsahovat vložené pole v nebezpečném kódu. V následujícím příkladu `fixedBuffer` má pole pevnou velikost. Příkaz slouží `fixed` k vytvoření ukazatele na první prvek. Přístup k prvkům pole prostřednictvím tohoto ukazatele. Příkaz `fixed` připne `fixedBuffer` pole instance na určité místo v paměti.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Velikost pole 128 `char` element je 256 bajtů. Pevná velikost [char](../../language-reference/builtin-types/char.md) vyrovnávací paměti vždy trvat dva bajty na znak, bez ohledu na kódování. To platí i v případě, že jsou vyrovnávací paměti `CharSet = CharSet.Auto` znaku zařazeny do metod rozhraní API nebo struktur s nebo `CharSet = CharSet.Ansi`. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.

Předchozí příklad ukazuje přístup `fixed` k polím bez připnutí, který je k dispozici počínaje C# 7.3.

Dalším běžným polem s pevnou velikostí je [bool](../../language-reference/builtin-types/bool.md) pole. Prvky v `bool` poli jsou vždy jeden bajt ve velikosti. `bool`pole nejsou vhodná pro vytváření bitových polí nebo vyrovnávacích pamětí.

> [!NOTE]
> S výjimkou paměti vytvořené pomocí [stackalloc](../../language-reference/operators/stackalloc.md), kompilátor Jazyka C# a clr (COMMON Language Runtime) neprovádějí žádné kontroly přetečení vyrovnávací paměti zabezpečení. Stejně jako u všech nebezpečných kódů buďte opatrní.

Nebezpečné vyrovnávací paměti se liší od běžných polí následujícími způsoby:

- Nebezpečné vyrovnávací paměti lze použít pouze v nebezpečném kontextu.
- Nebezpečné vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.
- Deklarace pole by měla obsahovat `char id[8]`počet, například . Nelze použít `char id[]`.
- Nebezpečné vyrovnávací paměti mohou být pouze pole instance struktur v nebezpečném kontextu.

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Nebezpečný kód a ukazatele](index.md)
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)
- [Vzájemná funkční spolupráce](../interop/index.md)
