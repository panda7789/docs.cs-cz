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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155929"
---
# <a name="destroying-threads"></a>Zničení vláken

Chcete-li ukončit provádění vlákna, obvykle používáte [model zrušení spolupráce](cancellation-in-managed-threads.md). V některých případech není možné vlákno zastavovat spolupracuje, protože spouští kód třetí strany, který není navržen pro kooperativní zrušení. Metodu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> v .NET Framework lze použít k vynucenému ukončení spravovaného vlákna. Když zavoláte <xref:System.Threading.Thread.Abort%2A>, modul CLR (Common Language Runtime) vyvolá <xref:System.Threading.ThreadAbortException> v cílovém vlákně, které může zachytit cílové vlákno. Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>. Metoda <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> není v rozhraní .NET Core podporována. Pokud potřebujete ukončit provádění kódu třetí strany v .NET Core nuceně, spusťte ho v samostatném procesu a použijte <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.

> [!NOTE]
> Pokud vlákno spouští nespravovaný kód, když je volána jeho metoda <xref:System.Threading.Thread.Abort%2A>, modul runtime ho označí <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. Výjimka je vyvolána, když se vlákno vrátí do spravovaného kódu.  
  
 Jakmile je vlákno přerušeno, nelze jej restartovat.  
  
 Metoda <xref:System.Threading.Thread.Abort%2A> nezpůsobí okamžité přerušení vlákna, protože cílové vlákno může zachytit <xref:System.Threading.ThreadAbortException> a provádět v bloku `finally` libovolné množství kódu. Můžete volat <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>, pokud potřebujete počkat, dokud vlákno neskončí. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> je blokující volání, které nevrací až do chvíle, kdy bylo vlákno skutečně zastaveno nebo byl ukončen nepovinný časový limit. Přerušené vlákno může zavolat metodu <xref:System.Threading.Thread.ResetAbort%2A> nebo provést neohraničené zpracování v bloku `finally`, takže pokud nezadáte časový limit, není zaručeno ukončení čekání.  
  
 Vlákna, která čekají na volání metody <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> lze přerušit jinými vlákny, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Zpracování ThreadAbortException  
 Očekáváte-li, že vlákno bude přerušeno, buď v důsledku volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve které je vlákno spuštěno (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> k ukončení vlákna), vlákno musí zpracovat <xref:System.Threading.ThreadAbortException> a provést jakékoliv konečné zpracování v klauzuli `finally`, jak je znázorněno v následujícím kódu.  
  
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
  
 Váš kód pro vyčištění musí být v klauzuli `catch` nebo v klauzuli `finally`, protože <xref:System.Threading.ThreadAbortException> znovu vyvolán systém na konci `finally` klauzule nebo na konci klauzule `catch`, pokud neexistuje žádná `finally` klauzule.  
  
 Můžete zabránit, aby systém znovu vyvolal výjimku, voláním metody <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>. Měli byste to ale udělat jenom v případě, že váš vlastní kód způsobil <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
