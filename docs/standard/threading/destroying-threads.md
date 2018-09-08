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
ms.openlocfilehash: 9a243c95aff77a5de2b3af15542c0bcc44870333
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205968"
---
# <a name="destroying-threads"></a>Zničení vláken
<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> Metoda se používá k zastavení spravovaným vláknem trvale. Při volání <xref:System.Threading.Thread.Abort%2A>, modul common language runtime vyvolá výjimku <xref:System.Threading.ThreadAbortException> v cílové vlákno, které cílové vlákno může zachytit. Další informace naleznete v tématu <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Pokud je vlákno prováděno nespravovaného kódu při jeho <xref:System.Threading.Thread.Abort%2A> metoda je volána, modul runtime ho označí <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. Pokud se podproces vrací do spravovaného kódu, je vyvolána výjimka.  
  
 Jakmile je přerušeno vlákno, nelze restartovat.  
  
 <xref:System.Threading.Thread.Abort%2A> Metoda nezpůsobí vlákno pro přerušení okamžitě, protože cílové vlákno může zachytit <xref:System.Threading.ThreadAbortException> a provést libovolné množství kódu v `finally` bloku. Můžete volat <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> Pokud budete muset počkat až do ukončení vlákna. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> je blokovacího hovoru, který nevrací, dokud vlákno je ve skutečnosti byl zastaven při provádění nebo volitelný časový limit uplynul. Přerušené vlákno může volat <xref:System.Threading.Thread.ResetAbort%2A> metoda nebo provádět zpracování bez vazby v `finally` blokovat, takže pokud nezadáte vypršení časového limitu, čekání není zaručeno, že na konec.  
  
 Vlákna, která čekají na volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda může dojít k přerušení kvůli ostatní vlákna, které volají <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>ThreadAbortException zpracování  
 Pokud očekáváte, že vaše vlákno přerušeno, buď jako výsledek volání <xref:System.Threading.Thread.Abort%2A> z vlastního kódu nebo v důsledku uvolnění domény aplikace, ve kterém je spuštěn podproces (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> používá <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> ukončení vlákna), musí umět zpracovat vašeho vlákna <xref:System.Threading.ThreadAbortException> a provést libovolné finální zpracování v `finally` klauzule, jak je znázorněno v následujícím kódu.  
  
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
  
 Čistícího kódu musí být v `catch` klauzule nebo `finally` klauzule, protože <xref:System.Threading.ThreadAbortException> je znovu vyvolána systém na konci `finally` klauzuli, nebo na konci `catch` klauzule dojde žádné `finally` klauzule.  
  
 Systém můžete zabránit voláním opětné vyvolání výjimky <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> metody. Nicméně byste měli dělat tento pouze tehdy, pokud váš vlastní kód, který způsobil <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
