---
title: loaderLock – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dbc6cc814d23923f01eceea70bd2fe45b9cbff8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388196"
---
# <a name="loaderlock-mda"></a>loaderLock – pomocník spravovaného ladění (MDA)
`loaderLock` Pomocník spravovaného ladění (MDA) upozorní na pokusy provést spravovaného kódu na vlákno, které obsahuje zámek zavaděče operačního systému Microsoft Windows.  Takové spuštění je neplatná, protože může vést k zablokování a použití knihovny DLL před nebyly inicializovány zavaděčem operačního systému.  
  
## <a name="symptoms"></a>Příznaky  
 Nejběžnější selhání při provádění kódu uvnitř zámek zavaděče operačního systému je, že se při pokusu o volání dalších funkcí Win32, které také vyžadovat zámek zavaděče zablokování vláken.  Příkladem takové funkce jsou `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, a `GetModuleHandle`.  Aplikace nemusí volat přímo tyto funkce; modul CLR (CLR) může volat tyto funkce v důsledku vyšší úrovně volání jako <xref:System.Reflection.Assembly.Load%2A> nebo první volání platformu vyvolat metodu.  
  
 Blokování může také nastat, pokud vlákno čeká další vlákno začínat nebo končit.  Pokud se vlákna spustí nebo dokončí provádění, musíte získat zámek zavaděče operačního systému k dodávání událostí do ovlivněných knihovny DLL.  
  
 Nakonec jsou případy, kdy volání do knihoven DLL může dojít před tyto knihovny DLL nebyly správně inicializovány zavaděčem operačního systému.  Na rozdíl od zablokování chyby, které může být zjištěném zkoumání zásobníky účastnící se k zablokování podprocesů, je velmi obtížné diagnostikovat použití knihoven DLL, neinicializovaného bez použití tohoto (mda).  
  
## <a name="cause"></a>příčina  
 Smíšené spravované nebo nespravované C++ sestavení vytvořené pro rozhraní .NET Framework verze 1.0 nebo 1.1, obecně se pokusí provést uvnitř zámek zavaděče spravovaného kódu, pokud má zvláštní pozornost nebyly provedeny, například propojení s **/NOENTRY**.
  
 Smíšené spravované nebo nespravované C++ sestavení vytvořené pro rozhraní .NET Framework verze 2.0 jsou méně náchylný k tyto problémy s stejné menší riziko jako aplikace, které používají nespravovaná knihovny DLL, které porušují pravidla operačního systému.  Například, pokud nespravované DLL `DllMain` vstupní bod volání `CoCreateInstance` získat spravovaný objekt, který byl vystaven objektům modelu COM, výsledkem je pokus o spuštění uvnitř zámek zavaděče spravovaného kódu. Další informace o problémech zámek zavaděče v rozhraní .NET Framework verze 2.0 nebo novější, najdete v části [inicializace smíšených sestavení](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Rozlišení  
 Ve Visual C++ .NET 2002 a Visual C++ .NET 2003, knihovny DLL kompilovat s `/clr` – možnost kompilátoru může nedeterministicky zablokování při načítání; tento problém byl volat Smíšený problém DLL načítání nebo zavaděč zámku. V aplikaci Visual C++ 2005 nebo novější téměř všechny nedeterminismy odebral z procesu načítání smíšených knihoven DLL. Existuje však několik zbývající scénáře, pro které zavaděč zámek můžete (deterministicky). Podrobné účet příčiny a řešení problémů zbývající zámek zavaděče, najdete v části [inicializace smíšených sestavení](/cpp/dotnet/initialization-of-mixed-assemblies). Pokud toto téma neidentifikuje váš problém zámek zavaděče, budete muset prozkoumat zásobník vlákna, chcete-li zjistit, proč dochází k zámek zavaděče a jak problém vyřešit. Podívejte se na trasování zásobníku pro vlákno, které tento MDA aktivoval.  Vlákno se pokouší o nelegálního volání do spravovaného kódu držením zámek zavaděče operačního systému.  Zobrazí se pravděpodobně knihovny DLL `DllMain` nebo ekvivalentní vstupního bodu v zásobníku.  Pravidla operačního systému pro souladu s právem jak z uvnitř takové vstupní bod je poměrně omezen.  Tato pravidla bránit žádné spravovaného spouštění.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modulu Runtime  
 Obvykle bude zablokování několik vláken v procesu.  Jedním z těchto vláken je pravděpodobné, že vlákno zodpovědná za provádění uvolňování, takže tento zablokování mají významný vliv na celý proces.  Kromě toho nebude možné žádné další operace, které vyžadují zámek zavaděče operačního systému, jako je načítání a uvolnění sestavení nebo knihovny DLL a spouštění nebo zastavování vláken.  
  
 V některých případech neobvyklou je také možné narušení přístupu nebo podobné problémy, aby se spouštěly v knihovnách DLL, které se nazývají předtím, než byl inicializován.  
  
## <a name="output"></a>Výstup  
 Tato MDA hlásí, že probíhá pokus o neplatný spravovaného spouštění.  Budete muset prozkoumat zásobník vlákna, chcete-li zjistit, proč dochází k zámek zavaděče a jak problém vyřešit.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
