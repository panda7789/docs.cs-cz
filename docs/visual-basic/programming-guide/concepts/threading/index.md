---
title: Dělení na vlákna (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
ms.openlocfilehash: fd1530a2b03c01b0a1cba0ce3ed4e18f2bf29046
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874830"
---
# <a name="threading-visual-basic"></a>Dělení na vlákna (Visual Basic)
Práce s vlákny umožňuje programu jazyka Visual Basic k provedení souběžné zpracování tak, že máte více než jednu operaci najednou. Například můžete dělení na vlákna pro monitorování vstup od uživatele, provedení úlohy na pozadí a zpracování současných vstupů.  
  
 Vlákna mají následující vlastnosti:  
  
-   Vlákna povolit program provádět souběžné zpracování.  
  
-   Rozhraní .NET Framework <xref:System.Threading> obor názvů umožňuje používat vlákna jednodušší.  
  
-   Vlákna sdílení prostředků aplikace. Další informace najdete v tématu [použití vláken a zřetězení](../../../../standard/threading/using-threads-and-threading.md).  
  
 V aplikaci Visual Basic má ve výchozím nastavení jedno vlákno. Pomocná vlákna však můžete vytvořit a použít ke spouštění kódu vytvořeného souběžně s primární vlákno. Tato vlákna se často nazývají *pracovních vláken*.  
  
 Pracovní vlákna je možné provádět časově náročné nebo kritického pro čas úlohy bez obsadit primárnímu vláknu. Například pracovní vlákna se často používají v serverových aplikacích ke splnění požadavků na příchozí bez čekání na dokončení předchozí žádosti. Pracovní vlákna se taky používají k provádění úloh "pozadí" v desktopových aplikací tak, aby hlavního vlákna – která určuje prvky uživatelského rozhraní – zůstane reagovat na akce uživatele.  
  
 Práce s vlákny řeší problémy s propustností a rychlostí odezvy, ale můžou také zavádět sdílení prostředků problémů například zablokování a konflikty časování. Více vláken jsou nejvhodnější pro úlohy, které vyžadují různé prostředky, jako jsou popisovače souborů a připojení k síti. Přiřazení většího počtu vláken na jeden prostředek je pravděpodobně způsobí problémy synchronizace a s často blokované čekající na jiná vlákna vlákna poráží účel používání více vláken.  
  
 Běžné strategie je použití pracovních vláken provádět časově náročné nebo náročné úkoly, které nevyžadují řadu prostředky používané jinými vlákny. Některé prostředky ve svém programu musí být samozřejmě přístup prostřednictvím více vláken. Pro tyto případy <xref:System.Threading> obor názvů obsahuje třídy pro synchronizaci vláken. Tyto třídy zahrnují <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, a <xref:System.Threading.ManualResetEvent>.  
  
 Některé nebo všechny tyto třídy můžete použít pro synchronizaci činností více vláken, ale některé podpora pro dělení na vlákna je podporována v jazyce Visual Basic. Například [příkaz SyncLock](../../../../visual-basic/language-reference/statements/synclock-statement.md) poskytuje funkce synchronizace prostřednictvím implicitního použití <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], vícevláknové programování je výrazně usnadněna díky <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), nové souběžných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na koncepci úkoly spíše než vlákna. Další informace najdete v tématu [paralelního programování](../../../../standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vícevláknové aplikace (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)|Popisuje postup vytvoření a používání vláken.|  
|[Parametry a návratové hodnoty pro procedury ve více vláknech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)|Popisuje, jak předat a vrátí parametry s aplikací s více vlákny.|  
|[Návod: Multithreading s komponentou BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)|Ukazuje, jak vytvořit jednoduchou aplikaci s více vlákny.|  
|[Synchronizace vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)|Popisuje, jak řídit interakce vlákna.|  
|[(Visual Basic) sdružování vláken](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)|Popisuje způsob použití fondu pracovních vláken, které jsou spravované systémem.|  
|[Postupy: použití fondu vláken (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)|Ukazuje použití synchronizované z více vláken ve fondu vláken.|  
|[Dělení na vlákna](../../../../standard/threading/index.md)|Popisuje, jak implementovat práce s vlákny v rozhraní .NET Framework.|
