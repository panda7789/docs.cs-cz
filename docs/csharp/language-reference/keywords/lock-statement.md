---
title: lock – příkaz (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960949"
---
# <a name="lock-statement-c-reference"></a>lock – příkaz (Referenční dokumentace jazyka C#)
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
  
-   `lock (this)` je nějaký problém, pokud instance je veřejně přístupný.  
  
-   `lock (typeof (MyType))` je nějaký problém, pokud `MyType` je veřejně dostupná.  
  
-   `lock("myLock")` je nějaký problém, protože jakýkoli jiný kód v procesu pomocí stejného řetězce, budou sdílet stejnou zámku.  
  
 Osvědčeným postupem je definovat `private` objekt k uzamčení, nebo `private static` proměnné objektu k ochraně dat, které jsou společné pro všechny instance.  
  
 Nelze použít [await](../../../csharp/language-reference/keywords/await.md) – klíčové slovo v textu `lock` příkazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jednoduché použití vlákna bez nutnosti používat jenom v C#.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vlákna a `lock`. Za předpokladu, `lock` příkaz je k dispozici, je důležité části tohoto bloku příkazů a `balance` nikdy bude záporné číslo.  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Dělení na vlákna](../../programming-guide/concepts/threading/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova příkazů](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [Propojené operace](../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../standard/threading/autoresetevent.md)  
 [Synchronizace vláken](../../programming-guide/concepts/threading/thread-synchronization.md)
