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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 986b4dee17c41928327e7b2672d641bbb8b16f1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960092"
---
# <a name="destroying-threads"></a>Zničení vláken
<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda se používá k trvalému zastavení spravovaného vlákna. Když zavoláte <xref:System.Threading.Thread.Abort%2A>, modul CLR (Common Language <xref:System.Threading.ThreadAbortException> Runtime) vyvolá v cílovém vlákně, které může zachytit cílové vlákno. Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Pokud vlákno spouští nespravovaný kód, když je <xref:System.Threading.Thread.Abort%2A> jeho metoda volána, modul runtime ho <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>označí. Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.  
  
 Jakmile je vlákno přerušeno, nelze jej restartovat.  
  
 Metoda nezpůsobí okamžité přerušení vlákna, protože cílové vlákno může <xref:System.Threading.ThreadAbortException> zachytit a spustit libovolné `finally` množství kódu v bloku. <xref:System.Threading.Thread.Abort%2A> Můžete zavolat <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> , pokud potřebujete počkat, dokud vlákno neskončí. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>je blokující volání, které nevrací až do doby, kdy bylo vlákno skutečně zastaveno nebo byl ukončen nepovinný časový limit. Přerušené vlákno může zavolat <xref:System.Threading.Thread.ResetAbort%2A> metodu nebo provést neohraničené zpracování `finally` v bloku, takže pokud nezadáte časový limit, není zaručeno ukončení čekání.  
  
 Vlákna, která čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metody, lze přerušit jinými vlákny, které volají. <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>  
  
## <a name="handling-threadabortexception"></a>Zpracování ThreadAbortException  
 Pokud očekáváte, že vlákno bude přerušeno, buď v důsledku volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve které je vlákno spuštěno (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> se k ukončení vláken), vlákno musí zpracovat a provede libovolné konečné zpracování `finally` v klauzuli, jak je znázorněno v následujícím kódu. <xref:System.Threading.ThreadAbortException>  
  
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
  
 Váš kód pro vyčištění musí být v `catch` klauzuli `finally` nebo v klauzuli, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolána systémem na konci `finally` klauzule `finally` nebo na konci `catch` klauzule, pokud neexistuje klauzule.  
  
 Můžete zabránit, aby systém znovu vyvolal výjimku, voláním <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody. Měli byste to však provést pouze v <xref:System.Threading.ThreadAbortException>případě, že váš vlastní kód způsobil.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
