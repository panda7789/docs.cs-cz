---
description: volatile – reference jazyka C#
title: volatile – reference jazyka C#
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: bb89e99e8e28ff1e263817f498619dbfae700a50
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141696"
---
# <a name="volatile-c-reference"></a>volatile (Referenční dokumentace jazyka C#)

`volatile`Klíčové slovo označuje, že pole může být upraveno více vlákny, které jsou spuštěny ve stejnou dobu. Kompilátor, systém modulu runtime a i hardware mohou změnit uspořádání čtení a zápisů do umístění paměti z důvodů výkonu. Pro pole, která jsou deklarována, `volatile` se tyto optimalizace nevztahují. Přidání `volatile` modifikátoru zajistí, že všechna vlákna budou sledovat nestálá zápisy provedené jakýmkoli jiným vláknem v pořadí, ve kterém byly provedeny. Neexistuje žádná záruka na jedno celkové řazení stálých zápisů, které se zobrazuje ze všech vláken provádění.

`volatile`Klíčové slovo lze použít pro pole těchto typů:

- Odkazové typy.
- Typy ukazatelů (v nezabezpečeném kontextu). Všimněte si, že i když samotný ukazatel může být volatile, objekt, na který odkazuje, nemůže být. Jinými slovy, nelze deklarovat "ukazatel na volatili".
- Jednoduché typy jako `sbyte` , `byte` , `short` , `ushort` , `int` , `uint` ,, a `char` `float` `bool` .
- `enum`Typ s jedním z následujících základních typů: `byte` , `sbyte` , `short` , `ushort` , `int` , nebo `uint` .
- Parametry obecného typu označují, že se jedná o odkazové typy.
- <xref:System.IntPtr> a <xref:System.UIntPtr>.

Jiné typy, včetně `double` a `long` , nelze označit, `volatile` protože čtení a zápisy do polí těchto typů nelze zaručit jako atomické. Chcete-li chránit více vlákenně přístup k těmto typům polí, použijte <xref:System.Threading.Interlocked> členy třídy nebo chraňte přístup pomocí [`lock`](lock-statement.md) příkazu.

`volatile`Klíčové slovo lze použít pouze pro pole `class` nebo `struct` . Místní proměnné nelze deklarovat `volatile` .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat veřejnou proměnnou pole jako `volatile` .

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

Následující příklad ukazuje, jak lze vytvořit pomocné nebo pracovní vlákno, a použít jej k paralelnímu zpracování s primárním vláknem. Další informace o multithreading najdete v tématu [spravovaná vlákna](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

S `volatile` modifikátorem přidaným do deklarace na `_shouldStop` místě získáte vždy stejné výsledky (podobně jako v výňatku zobrazeném v předchozím kódu). Nicméně bez tohoto modifikátoru u `_shouldStop` člena není chování předvídatelné. `DoWork`Metoda může optimalizovat přístup členů, což má za následek čtení zastaralých dat. Vzhledem k povaze programování s více vlákny je počet zastaralých čtení nepředvídatelný. Různá spuštění programu budou mít trochu odlišné výsledky.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Specifikace jazyka C#: klíčové slovo volatile](../../../../_csharplang/spec/classes.md#volatile-fields)
- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [příkaz Lock](lock-statement.md)
- <xref:System.Threading.Interlocked>
