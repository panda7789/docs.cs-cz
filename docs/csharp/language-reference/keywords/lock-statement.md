---
title: příkaz lock - odkaz Jazyka C#
description: Použití příkazu lock jazyka C# k synchronizaci přístupu podprocesu ke sdílenému prostředku
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713391"
---
# <a name="lock-statement-c-reference"></a>příkaz lock (odkaz C# )

Příkaz `lock` získá zámek vzájemné vyloučení pro daný objekt, provede blok příkazu a potom uvolní zámek. Zatímco zámek je držen, podproces, který drží zámek můžete znovu získat a uvolnit zámek. Jakékoli jiné vlákno je blokován o získání zámku a čeká, dokud zámek je uvolněna.

Prohlášení `lock` je ve formě

```csharp
lock (x)
{
    // Your code...
}
```

kde `x` je výraz typu [odkazu](reference-types.md). Je to přesně ekvivalentní

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

Vzhledem k tomu, kód používá [try... finally](try-finally.md) blokovat, zámek je uvolněna i v případě, `lock` že je vyvolána výjimka v rámci těla příkazu.

Nelze použít operátor [await](../operators/await.md) v textu příkazu. `lock`

## <a name="remarks"></a>Poznámky

Při synchronizaci přístupu podprocesu ke sdílenému prostředku, `private readonly object balanceLock = new object();`zámek na vyhrazené instance objektu (například) nebo jiné instance, která je nepravděpodobné, že bude použit jako objekt zámku nesouvisející části kódu. Vyhněte se použití stejné instance objektu zámku pro různé sdílené prostředky, protože by mohlo vést k zablokování nebo konflikty zámku. Zejména se vyhněte použití následující jako zámek objekty:

- `this`, protože jej mohou volající používat jako zámek.
- <xref:System.Type>instance, protože ty mohou být získány [typem operátoru](../operators/type-testing-and-cast.md#typeof-operator) nebo odrazem.
- řetězcové instance, včetně řetězcových literál, protože mohou být [internovány](/dotnet/api/system.string.intern#remarks).

## <a name="example"></a>Příklad

Následující příklad definuje `Account` třídu, která synchronizuje `balance` přístup k jeho `balanceLock` soukromé pole uzamčením na vyhrazené instanci. Použití stejné instance pro uzamčení `balance` zajišťuje, že pole nelze aktualizovat současně dvěma vlákny, které se pokoušejí volat metody `Debit` nebo `Credit` současně.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkazu zámku](~/_csharplang/spec/statements.md#the-lock-statement) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Referenční dokumentace k jazyku C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)
