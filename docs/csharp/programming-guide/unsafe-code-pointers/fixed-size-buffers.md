---
title: Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9158550885ea0a95a56f318362b21db48e648234
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)

V jazyce C#, můžete použít [pevné](../../language-reference/keywords/fixed-statement.md) příkaz k vytvoření vyrovnávací paměti s pevnou velikost pole ve struktuře data. Vyrovnávací paměti pevné velikosti jsou užitečné, když píšete tohoto zprostředkovatele komunikace s zdroje dat pro metody z dalších jazyků nebo platformy. Pole pevné může trvat všechny atributy nebo modifikátory, které jsou povoleny pro regulární struktura členy. Pouze omezení je, že musí být typ pole `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, nebo `double`.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Poznámky

Struktury jazyka C# obsahující pole v bezpečném kódu neobsahuje prvků pole. Místo toho struct obsahuje odkaz na elementy. Můžete vložit pole s pevnou velikostí v [struktura](../../language-reference/keywords/struct.md) při použití v [unsafe](../../language-reference/keywords/unsafe.md) blok kódu.

Následující `struct` je velikost 8 bajtů. `pathName` Pole je odkaz:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A `struct` může obsahovat vložené pole v nezabezpečený kód. V následujícím příkladu `fixedBuffer` pole má pevnou velikost. Můžete použít `fixed` příkaz k vytvoření ukazatel na první prvek. Elementy pole přistupujete prostřednictvím tento ukazatel. `fixed` Příkaz PIN `fixedBuffer` pole instance do určitého umístění v paměti.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

Velikost 128 elementu `char` pole je 256 bajtů. Pevná velikost [char](../../language-reference/keywords/char.md) vyrovnávací paměti vždy provést dva bajty na znak, bez ohledu na to, kódování. To platí i když vyrovnávací paměti char přeuspořádány metody rozhraní API nebo struktury s `CharSet = CharSet.Auto` nebo `CharSet = CharSet.Ansi`. Další informace naleznete v tématu <xref:System.Runtime.InteropServices.CharSet>.

V předchozím příkladu představuje přístup k `fixed` pole bez připojení, které je k dispozici počínaje C# 7.3...

Další běžné pole pevné velikosti je [bool](../../language-reference/keywords/bool.md) pole. Prvky v `bool` pole jsou vždy jeden bajt velikost. `bool` pole nejsou vhodné pro vytváření bitová pole nebo vyrovnávací paměti.

> [!NOTE]
> S výjimkou paměti vytvořené pomocí [stackalloc](../../language-reference/keywords/stackalloc.md), kompilátor jazyka C# a modul CLR (CLR) neprovádějte žádné kontroly přetečení vyrovnávací paměti zabezpečení. Stejně jako u všech nezabezpečený kód, buďte opatrní.

Nezabezpečené vyrovnávací paměti se liší od regulární pole následujícími způsoby:

- Nezabezpečené vyrovnávací paměti můžete použít pouze v kontextu unsafe.
- Nezabezpečené vyrovnávací paměti jsou vždy vektory nebo jednorozměrná pole.
- Deklarace pole by měla obsahovat počet, jako například `char id[8]`. Nemůžete použít `char id[]`.
- Nezabezpečené vyrovnávací paměti lze pouze pole instance struktury v kontextu unsafe.

## <a name="see-also"></a>Viz také

[Průvodce programováním v jazyce C#](../index.md)  
[Nebezpečný kód a ukazatele](index.md)  
[fixed – příkaz](../../language-reference/keywords/fixed-statement.md)  
[Interoperabilita](../interop/index.md)
