---
title: volatilní - C# Reference
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712842"
---
# <a name="volatile-c-reference"></a>volatile (Referenční dokumentace jazyka C#)

Klíčové `volatile` slovo označuje, že pole může být změněno více vlákny, které jsou spuštěny současně. Kompilátor, runtime systém a dokonce i hardware může změnit uspořádání čtení a zápisy do umístění v paměti z důvodů výkonu. Pole, která `volatile` jsou deklarována, nepodléhají těmto optimalizacím. Přidání `volatile` modifikátor zajišťuje, že všechna vlákna budou sledovat těkavé zápisy prováděné jiným vláknem v pořadí, ve kterém byly provedeny. Neexistuje žádná záruka jednoho celkového pořadí volatile zápisy, jak je vidět ze všech vláken provádění.

Klíčové `volatile` slovo lze použít pro pole těchto typů:

- Referenční typy.
- Typy ukazatelů (v nebezpečném kontextu). Všimněte si, že i když samotný ukazatel může být volatilní, objekt, na který odkazuje, nemůže. Jinými slovy nelze deklarovat "ukazatel na volatilní."
- Jednoduché typy, `sbyte` `byte`například , `uint` `char`, `float` `short` `ushort` `int`, `bool`, , , a .
- Typ `enum` s jedním z následujících `byte` `sbyte`základních `short` `ushort`typů: , , , , `int`, nebo `uint`.
- Parametry obecného typu, o kterých je známo, že se považují za typy odkazů.
- <xref:System.IntPtr> a <xref:System.UIntPtr>.

Jiné typy, `double` `long`včetně a `volatile` , nelze označit, protože čtení a zápisy do polí těchto typů nelze zaručit, že jsou atomické. Chcete-li chránit vícevláknový přístup k těmto <xref:System.Threading.Interlocked> typům polí, [`lock`](lock-statement.md) použijte členy třídy nebo chraňte přístup pomocí příkazu.

Klíčové `volatile` slovo lze použít pouze `class` pro `struct`pole nebo . Místní proměnné nelze `volatile`deklarovat .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat proměnnou veřejného pole jako `volatile`.

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

Následující příklad ukazuje, jak pomocné nebo pracovní vlákno lze vytvořit a použít k provádění zpracování paralelně s primární vlákno. Další informace o vícevláknovém řízení naleznete v [tématu Managed Threading](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

S `volatile` modifikátor přidán `_shouldStop` do deklarace na místě, budete vždy získat stejné výsledky (podobně jako výňatek je uvedeno v předchozím kódu). Však bez tohoto modifikátoru `_shouldStop` na člena chování je nepředvídatelné. Metoda `DoWork` může optimalizovat přístup člena, výsledkem čtení zastaralých dat. Vzhledem k povaze vícevláknové programování počet zastaralých čtení je nepředvídatelné. Různé běhy programu bude produkovat poněkud odlišné výsledky.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Specifikace jazyka C#: těkavé klíčové slovo](../../../../_csharplang/spec/classes.md#volatile-fields)
- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory](index.md)
- [příkaz lock](lock-statement.md)
- <xref:System.Threading.Interlocked>
