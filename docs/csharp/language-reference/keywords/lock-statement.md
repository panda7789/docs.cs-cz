---
title: Lock – příkaz – reference jazyka C#
description: Použití příkazu uzamknout v jazyce C# k synchronizaci přístupu ke vláknu ke sdílenému prostředku
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406687"
---
# <a name="lock-statement-c-reference"></a>Lock – příkaz (Referenční dokumentace jazyka C#)

`lock`Příkaz získá zámek vzájemného vyloučení pro daný objekt, spustí blok příkazu a pak uvolní zámek. I když je držen zámek, vlákno, které obsahuje zámek, může znovu načíst a uvolnit zámek. Jakékoli jiné vlákno zablokovalo získání zámku a čeká na uvolnění zámku.

`lock`Příkaz má formu.

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

V těle příkazu nelze použít [operátor await](../operators/await.md) `lock` .

## <a name="guidelines"></a>Pokyny

Když synchronizujete přístup vlákna ke sdílenému prostředku, zamkněte instanci vyhrazeného objektu (například `private readonly object balanceLock = new object();` ) nebo jinou instanci, která je pravděpodobně použita jako objekt zámku nesouvisejícími částmi kódu. Vyhněte se použití stejné instance uzamknutého objektu u různých sdílených prostředků, protože by mohlo dojít k zablokování nebo zamykání. Zejména se vyhněte použití následujícího objektu jako zámku objektů:

- `this`, jak je může používat volající jako zámek.
- <xref:System.Type>instance, které mohou být získány operátorem [typeof](../operators/type-testing-and-cast.md#typeof-operator) nebo reflexe.
- instance řetězců, včetně řetězcových literálů, by mohly být [interně](/dotnet/api/system.string.intern#remarks).

Pokud chcete snížit kolizí zámků, podržte zámek pro co nejkratší čas.

## <a name="example"></a>Příklad

Následující příklad definuje `Account` třídu, která synchronizuje přístup k jejímu soukromému `balance` poli uzamčením na vyhrazené `balanceLock` instanci. Použití stejné instance pro uzamykání zajistí, že `balance` pole nelze současně aktualizovat dvěma vlákny, které se pokoušejí `Debit` současně volat metody nebo `Credit` .

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [příkaz Lock](~/_csharplang/spec/statements.md#the-lock-statement) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Klíčová slova jazyka C#](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Přehled primitiv synchronizace](../../../standard/threading/overview-of-synchronization-primitives.md)
