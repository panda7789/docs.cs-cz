---
title: Dělení na vlákna (C#)
ms.date: 07/20/2015
ms.assetid: 236d157d-37c0-4ee8-89fc-721e6c596325
ms.openlocfilehash: 35f0ee3bfd67104d9eaab7c4dde7e35a28a374c5
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934698"
---
# <a name="threading-c"></a>Dělení na vlákna (C#)
Práce s vlákny umožňuje programu jazyka C# provádět souběžné zpracování tak, že máte více než jednu operaci najednou. Například můžete dělení na vlákna pro monitorování vstup od uživatele, provedení úlohy na pozadí a zpracování současných vstupů.  
  
 Vlákna mají následující vlastnosti:  
  
-   Vlákna povolit program provádět souběžné zpracování.  
  
-   Rozhraní .NET Framework <xref:System.Threading> obor názvů umožňuje používat vlákna jednodušší.  
  
-   Vlákna sdílení prostředků aplikace. Další informace najdete v tématu [použití vláken a zřetězení](../../../../../docs/standard/threading/using-threads-and-threading.md).  
  
 Ve výchozím nastavení programu v jazyce C# má jedno vlákno. Pomocná vlákna však můžete vytvořit a použít ke spouštění kódu vytvořeného souběžně s primární vlákno. Tato vlákna se často nazývají *pracovních vláken*.  
  
 Pracovní vlákna je možné provádět časově náročné nebo kritického pro čas úlohy bez obsadit primárnímu vláknu. Například pracovní vlákna se často používají v serverových aplikacích ke splnění požadavků na příchozí bez čekání na dokončení předchozí žádosti. Pracovní vlákna se taky používají k provádění úloh "pozadí" v desktopových aplikací tak, aby hlavního vlákna – která určuje prvky uživatelského rozhraní – zůstane reagovat na akce uživatele.  
  
 Práce s vlákny řeší problémy s propustností a rychlostí odezvy, ale můžou také zavádět sdílení prostředků problémů například zablokování a konflikty časování. Více vláken jsou nejvhodnější pro úlohy, které vyžadují různé prostředky, jako jsou popisovače souborů a připojení k síti. Přiřazení většího počtu vláken na jeden prostředek je pravděpodobně způsobí problémy synchronizace a s často blokované čekající na jiná vlákna vlákna poráží účel používání více vláken.  
  
 Běžné strategie je použití pracovních vláken provádět časově náročné nebo náročné úkoly, které nevyžadují řadu prostředky používané jinými vlákny. Některé prostředky ve svém programu musí být samozřejmě přístup prostřednictvím více vláken. Pro tyto případy <xref:System.Threading> obor názvů obsahuje třídy pro synchronizaci vláken. Tyto třídy zahrnují <xref:System.Threading.Mutex>, <xref:System.Threading.Monitor>, <xref:System.Threading.Interlocked>, <xref:System.Threading.AutoResetEvent>, a <xref:System.Threading.ManualResetEvent>.  
  
 Některé nebo všechny tyto třídy můžete použít pro synchronizaci činností více vláken, ale některé podpora pro dělení na vlákna je podporována v jazyce C#. Například [příkaz Lock](../../../../csharp/language-reference/keywords/lock-statement.md) poskytuje funkce synchronizace prostřednictvím implicitního použití <xref:System.Threading.Monitor>.  
  
> [!NOTE]
>  Počínaje [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], vícevláknové programování je výrazně usnadněna díky <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](https://msdn.microsoft.com/library/dd460688), nové souběžných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na koncepci úkoly spíše než vlákna. Další informace najdete v tématu [paralelního programování](../../../../../docs/standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Synchronizace vláken (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)|Popisuje, jak řídit interakce vlákna.|  
|[Dělení na vlákna](../../../../../docs/standard/threading/index.md)|Popisuje, jak implementovat práce s vlákny v rozhraní .NET Framework.|
