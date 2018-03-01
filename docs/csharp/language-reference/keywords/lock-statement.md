---
title: "lock – příkaz (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb48c2b1554ad2817406eaef42b4cb336ea46862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lock-statement-c-reference"></a>lock – příkaz (Referenční dokumentace jazyka C#)
`lock` – Klíčové slovo označí blok příkaz jako důležitý oddíl získání zámku vzájemné vyloučení pro daný objekt, provádění příkazu a pak uvolnění uzamčení. Následující příklad obsahuje `lock` příkaz.  
  
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
  
 Další informace najdete v tématu [vláken synchronizace](../../programming-guide/concepts/threading/thread-synchronization.md).  
  
## <a name="remarks"></a>Poznámky  
 `lock` – Klíčové slovo zajistí, že jedno vlákno nevstupuje kritické části kódu, zatímco jiné vlákno je v části důležité. Pokud jiné vlákno se pokusí zadejte uzamčeném kód, bude čekat, blokovat, dokud uvolnění objektu.  
  
 V části [zřetězení](../../programming-guide/concepts/threading/index.md) popisuje dělení na vlákna.  
  
 `lock` – Klíčové slovo volání <xref:System.Threading.Monitor.Enter%2A> na začátku bloku a <xref:System.Threading.Monitor.Exit%2A> na konci bloku. A <xref:System.Threading.ThreadInterruptedException> je vyvolána, pokud <xref:System.Threading.Thread.Interrupt%2A> přerušení vlákno, které čeká na zadejte `lock` příkaz.  
  
 Obecně není vhodné používat na zamykání `public` typu nebo instancí mimo kontrolu vašeho kódu. Běžné konstrukce `lock (this)`, `lock (typeof (MyType))`, a `lock ("myLock")` porušují tyto obecné zásady:  
  
-   `lock (this)`problém je, pokud instance je přístupná veřejně.  
  
-   `lock (typeof (MyType))`Pokud je problém `MyType` veřejně přístupný.  
  
-   `lock("myLock")`problém je, protože jiný kód v procesu pomocí jednoho řetězce, budou sdílet stejnou zámek.  
  
 Osvědčeným postupem je definovat `private` objekt, který chcete zamknout, nebo `private static` objektová proměnná k ochraně dat, které jsou společné pro všechny instance.  
  
 Nelze použít [await](../../../csharp/language-reference/keywords/await.md) – klíčové slovo v textu `lock` příkaz.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje jednoduchý používání vláken bez blokování v jazyce C#.  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá vláken a `lock`. Tak dlouho, dokud `lock` příkaz, příkaz blok je důležitý oddíl a `balance` nikdy bude záporné číslo.  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Dělení na vlákna](../../programming-guide/concepts/threading/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Klíčová slova příkazů](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [Propojené operace](../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../standard/threading/autoresetevent.md)  
 [Synchronizace vláken](../../programming-guide/concepts/threading/thread-synchronization.md)
