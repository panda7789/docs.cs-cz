---
title: volatile (Referenční dokumentace jazyka C#)
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: fd81c0c36cb88b971539e843e3e1f2096a73d40e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152774"
---
# <a name="volatile-c-reference"></a>volatile (Referenční dokumentace jazyka C#)

`volatile` – Klíčové slovo určuje, že pole může být upraveno ve víc vláknech, které jsou spuštěny ve stejnou dobu. Kompilátor, systém modulu runtime a dokonce i hardware mohou změnit uspořádání operací čtení a zápisu do umístění v paměti z důvodů výkonu. Pole, které jsou deklarovány `volatile` se nevztahují tato optimalizace. Přidávání `volatile` modifikátor zajistí, že všechna vlákna budou sledovat volatile zápisy provádí ostatní vlákna v pořadí, ve kterém byly provedeny. Není zaručeno jeden celkový řazení volatile zápisů pohledu ze všech vláken, která.
  
`volatile` – Klíčové slovo lze použít u polí těchto typů:  
  
- Typy odkazů.  
- Typy ukazatelů (v nezabezpečeném kontextu.). Všimněte si, že i když se ukazatel sám, může být typu volatile, objekt, který odkazuje na nelze. Jinými slovy nelze deklarovat "ukazatel na volatile."  
- Jednoduché typy, jako `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, a `bool`.  
- `enum` Typ s jedním z následujících základních typů: `byte`, `sbyte`, `short`, `ushort`, `int`, nebo `uint`.  
- Parametry obecného typu známé jako referenční typy.
- <xref:System.IntPtr> a <xref:System.UIntPtr>.  

Jiné typy, včetně `double` a `long`, nemohou být označeny `volatile` protože čtení a zápis do polí těchto typů nelze zaručit bylo atomické. Chcete-li chránit vícevláknový přístup k těmto typům pole, použijte <xref:System.Threading.Interlocked> členy třídy nebo chránit pomocí přístupu [ `lock` ](lock-statement.md) příkazu.

`volatile` – Klíčové slovo lze použít pouze pro pole `class` nebo `struct`. Místní proměnné nelze použít deklaraci `volatile`.
  
## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat proměnnou veřejné pole jako `volatile`.  
  
[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

Následující příklad ukazuje, jak můžete vytvořit a používá ke zpracování paralelní s ním primární vlákno pomocné nebo pracovní vlákno. Další informace o multithreading, viz [dělení na spravovaná vlákna](../../../standard/threading/index.md).
  
[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

S `volatile` modifikátor přidána do deklarace `_shouldStop` na místě, vždy dosáhnete stejných výsledků (podobně jako výňatek je znázorněno v předchozím kódu). Ale bez tento modifikátor `_shouldStop` člen, nepředvídatelné chování. `DoWork` Metoda může optimalizovat přístup ke členu, což vede k zastaralých dat pro čtení. Vzhledem k povaze vícevláknového programování je počet zastaralých čtení nepředvídatelné. Během různých spuštění programu se poněkud liší výsledkům.

## <a name="c-language-specification"></a>Specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [C#Specifikace jazyka: volatile – klíčové slovo](../../../../_csharplang/spec/classes.md#volatile-fields)
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](modifiers.md)
- [Příkaz Lock](lock-statement.md)
- <xref:System.Threading.Interlocked> Třída
