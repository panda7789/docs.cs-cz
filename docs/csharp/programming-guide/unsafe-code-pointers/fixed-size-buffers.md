---
title: Velikost vyrovnávací paměti – pevná C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 2d0a4f829f6fe4d9662e25a4d8fd3936d2afd7f1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242475"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)

V jazyce C#, můžete použít [oprava](../../language-reference/keywords/fixed-statement.md) příkaz vytvoří vyrovnávací paměti s pevnou velikostí pole v datové struktuře. Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete tohoto zprostředkovatele komunikace s objekty zdroje dat pro metody v jiných jazycích či platformách. Oprava pole můžete provést všechny atributy nebo modifikátory, které jsou povoleny pro členy struktury regulárních. Jediným omezením je, že musí být typu pole `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Poznámky

V nouzovém kódu struktura jazyka C#, která obsahuje pole neobsahuje prvků pole. Místo toho struktura obsahuje odkaz na prvky. Můžete vložit pole s pevnou velikostí v [struktury](../../language-reference/keywords/struct.md) když se používá v [unsafe](../../language-reference/keywords/unsafe.md) blok kódu.

Následující `struct` je velikosti 8 bajtů. `pathName` Pole je odkaz:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` může obsahovat vložené pole v nezabezpečený kód. V následujícím příkladu `fixedBuffer` pole má pevnou velikost. Můžete použít `fixed` příkaz Vytvořit ukazatel na první prvek. Přístup k prvkům pole pomocí tohoto ukazatele. `fixed` Příkaz PIN kódy `fixedBuffer` pole instance na konkrétní umístění v paměti.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Velikost 128 elementu `char` pole je 256 bajtů. Pevná velikost [char](../../language-reference/keywords/char.md) vyrovnávacích pamětí vždy provést dva bajty na znak, bez ohledu na to, kódování. To platí i, když jsou char vyrovnávací paměti zařazeny do metody rozhraní API nebo struktury s `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.

Předchozí příklad ukazuje `fixed` pole bez Připnutí, které je k dispozici od verze C# 7.3.

Další běžné pevnou velikost pole je [bool](../../language-reference/keywords/bool.md) pole. Prvky v `bool` pole jsou vždy jeden bajt velikosti. `bool` pole nejsou vhodné pro vytvoření bitové pole nebo vyrovnávací paměti.

> [!NOTE]
> S výjimkou paměti vytvořené využitím [stackalloc](../../language-reference/keywords/stackalloc.md), kompilátor jazyka C# a common language runtime (CLR) nebude provádět žádné bezpečnostní kontroly přetečení vyrovnávací paměti. Stejně jako u všech nebezpečný kód, buďte opatrní.

Nezabezpečené vyrovnávací paměti se liší od pravidelných polí následujícími způsoby:

- Nezabezpečené vyrovnávací paměti lze použít pouze v nezabezpečeném kontextu.
- Nezabezpečené vyrovnávací paměti jsou vždy vektorů nebo jednorozměrná pole.
- Deklarace pole by měla obsahovat počet, jako například `char id[8]`. Nemůžete použít `char id[]`.
- Nezabezpečené vyrovnávací paměti může být pouze pole instancí struktur v nezabezpečeném kontextu.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../index.md)  
- [Nebezpečný kód a ukazatele](index.md)  
- [fixed – příkaz](../../language-reference/keywords/fixed-statement.md)  
- [Interoperabilita](../interop/index.md)
