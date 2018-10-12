---
title: Dělení na vlákna (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 704bb04b-ff23-471d-ab12-3cec1c2bca59
ms.openlocfilehash: 366c88db5d229120b1e626f275b4eeb8ecd42dba
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123095"
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
>  Počínaje [!INCLUDE[net_v40_long](~/includes/net-v40-long-md.md)], vícevláknové programování je výrazně usnadněna díky <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> třídy, [paralelní LINQ (PLINQ)](../../../../standard/parallel-programming/parallel-linq-plinq.md), nové souběžných kolekcí tříd v <xref:System.Collections.Concurrent?displayProperty=nameWithType> obor názvů a nové programovací model, který je založen na koncepci úkoly spíše než vlákna. Další informace najdete v tématu [paralelního programování](../../../../standard/parallel-programming/index.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Dělení na vlákna](../../../../standard/threading/index.md)|Popisuje, jak implementovat práce s vlákny v rozhraní .NET Framework.|
