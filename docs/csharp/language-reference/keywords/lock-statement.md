---
title: příkaz Lock – C# odkaz
ms.custom: seodec18
description: Použití příkazu C# Lock k synchronizaci přístupu ke vláknu ke sdílenému prostředku
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 70fcd8041946f2b1db3b37de79318b87771ee676
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168766"
---
# <a name="lock-statement-c-reference"></a>Lock – příkazC# (Referenční dokumentace)

`lock` Příkaz získá zámek vzájemného vyloučení pro daný objekt, spustí blok příkazu a pak uvolní zámek. I když je držen zámek, vlákno, které obsahuje zámek, může znovu načíst a uvolnit zámek. Jakékoli jiné vlákno zablokovalo získání zámku a čeká na uvolnění zámku.

`lock` Příkaz má formu.

```csharp
lock (x)
{
    // Your code...
}
```

kde `x` je výraz [typu odkazu](reference-types.md). Je přesně stejný jako

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

Vzhledem k tomu, že kód používá [Try... finally](try-finally.md) Block, zámek je uvolněn i v případě, že je vyvolána výjimka v těle `lock` příkazu.

V těle `lock` příkazu nelze použít [operátor await](../operators/await.md) .

## <a name="remarks"></a>Poznámky

Když synchronizujete přístup vlákna ke sdílenému prostředku, zamkněte instanci vyhrazeného objektu (například `private readonly object balanceLock = new object();`) nebo jinou instanci, která je pravděpodobně použita jako objekt zámku nesouvisejícími částmi kódu. Vyhněte se použití stejné instance uzamknutého objektu u různých sdílených prostředků, protože by mohlo dojít k zablokování nebo zamykání. Zejména se vyhněte použití následujícího objektu jako zámku objektů:

- `this`, jak je může používat volající jako zámek.
- <xref:System.Type>instance, které mohou být získány operátorem [typeof](../operators/type-testing-and-cast.md#typeof-operator) nebo reflexe.
- instance řetězců, včetně řetězcových literálů, by mohly být [interně](/dotnet/api/system.string.intern#remarks).

## <a name="example"></a>Příklad

Následující příklad definuje `Account` třídu, která synchronizuje přístup k jejímu soukromému `balance` poli uzamčením na vyhrazené `balanceLock` instanci. Použití stejné instance pro uzamykání zajistí, že `balance` pole nelze současně aktualizovat dvěma vlákny, které se pokoušejí současně `Debit` volat metody nebo `Credit` .

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkaz Lock](~/_csharplang/spec/statements.md#the-lock-statement) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)
