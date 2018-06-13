---
title: Dělení na vlákna (C#)
ms.date: 07/20/2015
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
ms.openlocfilehash: 9f1c7071972d8e449bc06054fbe6d70e447b694f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335832"
---
# <a name="threading-c"></a>Dělení na vlákna (C#)
Dělení na vlákna umožňuje vašeho programu C# k provedení souběžné zpracování, takže můžete provést více než jednu operaci najednou. Například můžete dělení na vlákna monitorovat vstup od uživatele, provedení úlohy na pozadí a zpracování souběžných datové proudy vstupu.  
  
 Vlákna mít následující vlastnosti:  
  
-   Vlákna povolit vašeho programu k provedení souběžné zpracování.  
  
-   Rozhraní .NET Framework <xref:System.Threading> použití vláken snazší díky oboru názvů.  
  
-   Vlákna sdílet prostředky aplikace. Další informace najdete v tématu [použití vláken a zřetězení](../../../../../docs/standard/threading/using-threads-and-threading.md).  
  
 Ve výchozím nastavení má programu v C# jedno vlákno. Pomocná vláken však můžete vytvořit a používají ke spouštění kódu paralelně s primární vlákno. Tyto vláken se často nazývají *pracovních vláken*.  
  
 Pracovní vlákna slouží k provádění úloh časově náročné nebo kritický pro čas bez třeba zadávat primární vlákno. Například pracovních vláken se často používají v serverových aplikacích ke splnění příchozí požadavky bez čekání na předchozí požadavek dokončit. Pracovní vlákna slouží také k provedení úlohy na "pozadí" v aplikací klasické pracovní plochy, aby hlavního vlákna – které jednotky prvky uživatelského rozhraní – zůstane reagují na akce uživatele.  
  
 Dělení na vlákna řeší problémy s propustnost a kratší reakční doby, ale můžou taky vést sdílení prostředků problémy, jako je blokování a konflikty časování. Více vláken jsou nejvhodnější pro úlohy, které vyžadují různé prostředky, jako jsou popisovače souborů a připojení k síti. Přiřazení více vláken na jediném prostředku je může způsobit problémy s synchronizací a nutnosti vláken při čekání na další vláken často zablokované účinně chrání před účel používání více vláken.  
  
 Strategie běžné je použít k provedení časově náročné pracovních vláken nebo kritický pro čas úlohy, které nevyžadují řadu prostředky využívané třídou jiná vlákna. Samozřejmě některé v programu musí být přístup k prostředkům více vláken. Pro tyto případy <xref:System.Threading> obor názvů obsahuje třídy pro synchronizaci vláken. Zahrnout tyto třídy <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, a <xref:System.Threading.ManualResetEvent>.  
  
 Pomocí některé nebo všechny tyto třídy můžete synchronizovat aktivity z více vláken, ale podporuje někteří podporu pro dělení na vlákna jazyka C#. Například [Lock – příkaz](../../../../csharp/language-reference/keywords/lock-statement.md) poskytuje funkce synchronizace prostřednictvím implicitní použití <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], vícevláknové programování je výrazně jednodušší s <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), nové souběžných kolekce tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na konceptu úkolů, nikoli vláken. Další informace najdete v tématu [paralelní programování](../../../../../docs/standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vícevláknové aplikace (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)|Popisuje postup vytvoření a používání vláken.|  
|[Parametry a návratové hodnoty pro procedury ve více vláknech (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Popisuje, jak předat a vrátí parametry s vícevláknové aplikace.|  
|[Návod: Multithreading s komponentou BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Ukazuje, jak vytvořit jednoduchou aplikaci s více vlákny.|  
|[Synchronizace vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Popisuje, jak řídit interakce vláken.|  
|[Časovače vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)|Popisuje postup spouštění procedur v samostatných vláknech v pevných intervalech.|  
|[Přístup z více vláken sdružování (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)|Popisuje, jak používat fond pracovních vláken, které jsou spravovány systémem.|  
|[Postupy: použití fondu vláken (C#)](../../../../csharp/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Demonstruje synchronizované používání více vláken ve fondu vláken.|  
|[Dělení na vlákna](../../../../../docs/standard/threading/index.md)|Popisuje, jak implementovat dělení na vlákna v rozhraní .NET Framework.|
