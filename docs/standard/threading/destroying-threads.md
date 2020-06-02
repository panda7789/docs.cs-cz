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
ms.openlocfilehash: 9f69773ec19008ebafd28a68e4e2007b6f9bb979
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279812"
---
# <a name="destroying-threads"></a>Zničení vláken

Chcete-li ukončit provádění vlákna, obvykle používáte [model zrušení spolupráce](cancellation-in-managed-threads.md). V některých případech není možné vlákno zastavovat spolupracuje, protože spouští kód třetí strany, který není navržen pro kooperativní zrušení. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metodu v .NET Framework lze použít k vynucenému ukončení spravovaného vlákna. Když zavoláte <xref:System.Threading.Thread.Abort%2A> , modul CLR (Common Language Runtime) vyvolá <xref:System.Threading.ThreadAbortException> v cílovém vlákně, které může zachytit cílové vlákno. Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Metoda není v rozhraní .NET Core podporována. Pokud potřebujete ukončit provádění kódu třetí strany vynuceně v .NET Core, spusťte ho v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

> [!NOTE]
> Pokud vlákno spouští nespravovaný kód <xref:System.Threading.Thread.Abort%2A> , když je jeho metoda volána, modul runtime ho označí <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> . Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.  
  
 Jakmile je vlákno přerušeno, nelze jej restartovat.  
  
 <xref:System.Threading.Thread.Abort%2A>Metoda nezpůsobí okamžité přerušení vlákna, protože cílové vlákno může zachytit <xref:System.Threading.ThreadAbortException> a spustit libovolné množství kódu v `finally` bloku. Můžete zavolat, <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Pokud potřebujete počkat, dokud vlákno neskončí. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>je blokující volání, které nevrací až do doby, kdy bylo vlákno skutečně zastaveno nebo byl ukončen nepovinný časový limit. Přerušené vlákno může zavolat <xref:System.Threading.Thread.ResetAbort%2A> metodu nebo provést neohraničené zpracování v `finally` bloku, takže pokud nezadáte časový limit, není zaručeno ukončení čekání.  
  
 Vlákna, která čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, lze přerušit jinými vlákny, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> .  
  
## <a name="handling-threadabortexception"></a>Zpracování ThreadAbortException  
 Pokud očekáváte, že vlákno bude přerušeno, buď v důsledku volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve které je vlákno spuštěno ( <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> se k ukončení vlákna), vlákno musí zpracovat <xref:System.Threading.ThreadAbortException> a provést jakékoliv konečné zpracování v `finally` klauzuli, jak je znázorněno v následujícím kódu.  
  
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
  
 Váš kód pro vyčištění musí být v `catch` klauzuli nebo v `finally` klauzuli, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolána systémem na konci `finally` klauzule nebo na konci `catch` klauzule, pokud neexistuje `finally` klauzule.  
  
 Můžete zabránit, aby systém znovu vyvolal výjimku, voláním <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody. Měli byste to však provést pouze v případě, že váš vlastní kód způsobil <xref:System.Threading.ThreadAbortException> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
