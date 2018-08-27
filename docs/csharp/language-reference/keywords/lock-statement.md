---
title: Lock – příkaz (referenční dokumentace jazyka C#)
description: 'Lock – klíčové slovo se používá v dělení na vlákna '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931190"
---
# <a name="lock-statement-c-reference"></a>Lock – příkaz (referenční dokumentace jazyka C#)

`lock` – Klíčové slovo označí blok příkazu jako kritickou sekci tak, že získání zámku vzájemné vyloučení pro daný objekt, provede příkaz a pak uzamčení uvolní. Následující příklad obsahuje `lock` příkazu.

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

Další informace najdete v tématu [vlákna synchronizace](../../programming-guide/concepts/threading/thread-synchronization.md).

## <a name="remarks"></a>Poznámky

`lock` – Klíčové slovo se zajistí, že jedno vlákno nezadá důležité části kódu, zatímco jiné vlákno je v části důležité. Pokud jiné vlákno se pokusí zadejte uzamčené kódu, bude čekat, blokovat, dokud se neuvolní objektu.

V části [zřetězení](../../programming-guide/concepts/threading/index.md) popisuje dělení na vlákna.

`lock` – Klíčové slovo volání <xref:System.Threading.Monitor.Enter%2A> na začátku bloku a <xref:System.Threading.Monitor.Exit%2A> na konci bloku. A <xref:System.Threading.ThreadInterruptedException> je vyvolána, pokud <xref:System.Threading.Thread.Interrupt%2A> přeruší podproces, který čeká na zadání `lock` příkazu.

Obecně se vyhýbejte zamykání `public` typu nebo instance mimo kontrolu kódu. Běžné konstrukce `lock (this)`, `lock (typeof (MyType))`, a `lock ("myLock")` porušují tyto obecné zásady:

- `lock (this)` je nějaký problém, pokud instance je veřejně přístupný.

- `lock (typeof (MyType))` je nějaký problém, pokud `MyType` je veřejně dostupná.

- `lock("myLock")` je nějaký problém, protože jakýkoli jiný kód v procesu pomocí stejného řetězce, budou sdílet stejnou zámku.

Osvědčeným postupem je definovat `private` objekt k uzamčení, nebo `private static` proměnné objektu k ochraně dat, které jsou společné pro všechny instance.

Nelze použít [await](await.md) – klíčové slovo v textu `lock` příkazu.

## <a name="example---threads-without-locking"></a>Příklad – bez blokování vlákna

Následující příklad ukazuje, jednoduché použití vlákna bez nutnosti používat jenom v C#:

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a>Příklad: vlákna používají zamykání

Následující příklad používá vlákna a `lock`. Za předpokladu, `lock` příkaz je k dispozici, je důležité části tohoto bloku příkazů a `balance` nikdy bude záporné číslo:

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [Referenční dokumentace jazyka C#](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Dělení na vlákna](../../programming-guide/concepts/threading/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Klíčová slova příkazů](statement-keywords.md)
- [Propojené operace](../../../standard/threading/interlocked-operations.md)
- [AutoResetEvent](../../../standard/threading/autoresetevent.md)
- [Synchronizace vláken](../../programming-guide/concepts/threading/thread-synchronization.md)