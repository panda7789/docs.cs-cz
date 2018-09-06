---
title: Lock – příkaz (referenční dokumentace jazyka C#)
description: Použijte příkaz lock jazyka C# k synchronizaci přístupu vláken k sdíleného prostředku
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858353"
---
# <a name="lock-statement-c-reference"></a>Lock – příkaz (referenční dokumentace jazyka C#)

`lock` Příkaz získá zámek pro vzájemné vyloučení pro daný objekt, provede blok příkazů a poté uvolní zámek. Dokud je držen zámek, vlákna, která je držitelem zámku znovu získat a uvolní zámek. Jiné vlákno se blokuje získání zámku a čeká na zámek je uvolněn.

`lock` Příkaz má formát

```csharp
lock (x)
{
    // Your code...
}
```

kde `x` je výraz [odkazovat na typ](reference-types.md). To je přesně odpovídá

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

Protože kód používá [try... finally](try-finally.md) bloku, zámek je všeobecně dostupné i v případě, že dojde k výjimce v těle `lock` příkaz.

Nelze použít [await](await.md) – klíčové slovo v textu `lock` příkazu.

## <a name="remarks"></a>Poznámky

Při synchronizaci přístupu vláken sdílený prostředek uzamčení na instanci vyhrazené objektu (například `private readonly object balanceLock = new object();`) nebo do jiné instance, která pravděpodobně nebude používat jako objekt zámek nesouvisejících částí kódu. Vyhněte se použití stejné instance objektu zámku pro různé sdílené prostředky, protože může dojít k zablokování nebo lock kolize. Konkrétně se vyhněte se použití

- `this` (by mohly používat volající jako uzamčení),
- <xref:System.Type> instance (může být možné získat [typeof](typeof.md) operátor nebo reflexi),
- řetězec instance, včetně řetězcové literály

jako objekty zámku.

## <a name="example"></a>Příklad

Následující příklad definuje `Account` třídu, která se synchronizuje přístup k jeho privátní `balance` pole, a to na vyhrazené zamykání `balanceLock` instance. Použití stejné instance pro uzamčení zajišťuje, že `balance` pole nejde aktualizovat současně dvěma vlákny pokusu o volání `Debit` nebo `Credit` metod současně.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Referenční dokumentace jazyka C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova příkazů](statement-keywords.md)
- [Propojené operace](../../../standard/threading/interlocked-operations.md)
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)