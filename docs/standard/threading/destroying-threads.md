---
title: Zničení vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: 842ca4ff17f9cbab3a1518d2dea37436c9b23f9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155929"
---
# <a name="destroying-threads"></a>Zničení vláken

Chcete-li ukončit provádění podprocesu, obvykle používáte [model zrušení spolupráce](cancellation-in-managed-threads.md). Někdy není možné zastavit vlákno kooperativně, protože spustí kód třetí strany, který není určen pro kooperativní zrušení. Metodu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> v rozhraní .NET Framework lze použít k násilnému ukončení spravovaného vlákna. Při volání <xref:System.Threading.Thread.Abort%2A>, common language runtime <xref:System.Threading.ThreadAbortException> vyvolá v cílovévlákno, které může zachytit cílové vlákno. Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> není podporována v .NET Core. Pokud potřebujete ukončit provádění kódu třetí strany násilně v .NET Core, spusťte jej v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.

> [!NOTE]
> Pokud vlákno provádí nespravovaný <xref:System.Threading.Thread.Abort%2A> kód při volání jeho <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>metody, modul runtime jej označí . Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.  
  
 Jakmile je vlákno přerušeno, nelze jej restartovat.  
  
 Metoda <xref:System.Threading.Thread.Abort%2A> nezpůsobí vlákno přerušit okamžitě, protože cílové vlákno <xref:System.Threading.ThreadAbortException> můžete zachytit a spustit libovolné `finally` množství kódu v bloku. Můžete volat, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> pokud potřebujete počkat, dokud vlákno skončí. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>je blokující volání, které se nevrátí, dokud vlákno skutečně zastavilo provádění nebo neuplynul volitelný časový limit. Přerušené vlákno může <xref:System.Threading.Thread.ResetAbort%2A> volat metodu nebo provádět `finally` neomezené zpracování v bloku, takže pokud nezadáte časový čas, čekání není zaručeno ukončení.  
  
 Podprocesy, které čekají na <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> volání metody může být přerušena jinými vlákny, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Zpracování výjimky ThreadAbortException  
 Pokud očekáváte, že vaše vlákno bude přerušeno, buď v důsledku <xref:System.Threading.Thread.Abort%2A> volání z vlastního kódu, nebo v<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> důsledku <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> uvolnění domény aplikace, ve <xref:System.Threading.ThreadAbortException> které je vlákno spuštěno (používá k ukončení podprocesů), musí vlákno zpracovat a provést konečné zpracování v `finally` klauzuli, jak je znázorněno v následujícím kódu.  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 Váš kód pro vyčištění musí `catch` být `finally` v klauzuli <xref:System.Threading.ThreadAbortException> nebo klauzuli, protože je znovu `finally` vyvolánsystémem na konci `catch` klauzule nebo `finally` na konci klauzule, pokud neexistuje žádná klauzule.  
  
 Můžete zabránit systému znovu vyvolání výjimky <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> voláním metody. Měli byste to však provést pouze <xref:System.Threading.ThreadAbortException>v případě, že vlastní kód způsobil .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Použití vláken a zřetězení](../../../docs/standard/threading/using-threads-and-threading.md)
