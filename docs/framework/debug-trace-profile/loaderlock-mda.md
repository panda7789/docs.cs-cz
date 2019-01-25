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
ms.openlocfilehash: 1001777f00524f3a183e1641718b9d3121c94e66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637934"
---
# <a name="loaderlock-mda"></a>loaderLock – pomocník spravovaného ladění (MDA)
`loaderLock` Pomocníka spravovaného ladění (MDA) upozorní na pokusy pro spuštění spravovaného kódu na vlákno, které drží zámek zavaděče operační systém Microsoft Windows.  Takové spuštění je neplatný, protože to může vést k zablokování a použití knihoven DLL předtím, než se inicializují zavaděčem operačního systému.  
  
## <a name="symptoms"></a>Příznaky  
 Většina běžných chyby při provádění kódu uvnitř zámku zaváděcího programu operačního systému je, že se při pokusu o volání další funkce Win32, které také vyžadují zámek zavaděče zablokování vlákna.  Příkladem takové funkce jsou `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, a `GetModuleHandle`.  Aplikace nemusí zavolat přímo tyto funkce. modul CLR (CLR) může volat tyto funkce v důsledku vyšší úroveň volání, například <xref:System.Reflection.Assembly.Load%2A> nebo první volání na platformu vyvolání metody.  
  
 Zablokování může také dojít, pokud vlákno čeká další vlákno zahájení nebo dokončení.  Jakmile se vlákno spustí nebo dokončí provádění, musíte získat zavaděči operačního systému k doručení událostí na ovlivněných knihovny DLL.  
  
 A konečně existují případy, kdy volání do knihoven DLL může dojít před těmito knihovnami DLL byly správně inicializovány zavaděčem operačního systému.  Na rozdíl od zablokování chyby, které můžete zjistit kontrolou zásobníky všech vláken součástí zablokování, je velmi obtížné diagnostikovat, použití neinicializovaného knihoven DLL bez použití toto MDA.  
  
## <a name="cause"></a>Příčina  
 Smíšená spravovaného a nespravovaného C++ sestavení vytvořené pro rozhraní .NET Framework verze 1.0 nebo 1.1, obecně se pokusí spustit spravovaný kód uvnitř zámku zaváděcího programu, pokud zvláštní pozornost je už zabraný, například propojení s **NOENTRY**.
  
 Smíšená spravovaného a nespravovaného C++ sestavení vytvořené pro rozhraní .NET Framework verze 2.0 jsou méně náchylný k tyto problémy s stejné menší riziko jako aplikace pomocí nespravovaných knihoven DLL, které porušují pravidla operačního systému.  Například, pokud nespravovaná knihovna DLL pro `DllMain` vstupní bod volání `CoCreateInstance` získat spravovaný objekt, který byl zpřístupněn do modelu COM, výsledek je pokus o spuštění uvnitř zámku zaváděcího programu spravovaného kódu. Další informace o problémech zámek zavaděče v rozhraní .NET Framework verze 2.0 nebo novější, naleznete v tématu [inicializace smíšených sestavení](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Rozlišení  
 Ve Visual C++ .NET 2002 a Visual C++ .NET 2003, knihovny DLL zkompilovaná `/clr` – možnost kompilátoru může nedeterministicky vzájemné zablokování při načtení; tento problém se volala smíšené problém zámek DLL načítání nebo zavaděče. V aplikaci Visual C++ 2005 a novějších téměř všechny seznam se odebrala z procesu načítání smíšených knihoven DLL. Existují však některé zbývající scénáře, pro které zavaděč zámku může (deterministicky). Prováděcí účet příčiny a řešení pro zbývající problémy zámek zavaděče, naleznete v tématu [inicializace smíšených sestavení](/cpp/dotnet/initialization-of-mixed-assemblies). Toto téma neidentifikuje váš problém zámek zavaděče, máte k prozkoumání zásobníku vlákna, chcete-li zjistit, proč dochází k zámek zavaděče a pokyny k vyřešení problému. Podívejte se na trasování zásobníku pro vlákno, které se má toto MDA aktivováno.  Vlákno se pokouší o neoprávněně volat do spravovaného kódu při držení zámku zaváděcího programu operačního systému.  Zobrazí se pravděpodobně knihovnu DLL `DllMain` nebo ekvivalentní vstupní bod do zásobníku.  Pravidla operačního systému pro jak právně postupovat z uvnitř jako vstupní bod jsou poměrně omezené.  Tato pravidla bránit žádné spravované spuštění.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Obvykle bude zablokování několik vláken uvnitř procesu.  Jeden z těchto vlákna by mohla být odpovědný za provedení uvolnění paměti, abyste tomuto vzájemnému zablokování může mít významný vliv na celý proces vlákna.  Kromě toho zabrání jakékoli další operace, které vyžadují operačního systému nastavený zámek zavaděče, třeba načítání a uvolňování sestavení nebo knihovny DLL a spouštění nebo zastavování vláken.  
  
 V některých případech neobvyklé je také možné narušení přístupu nebo s podobnými problémy až se spustí v knihovnách DLL, které se volají, než byl inicializován.  
  
## <a name="output"></a>Výstup  
 Toto MDA hlásí, že probíhá pokus o neplatné spravované spuštění.  Je potřeba zkontrolovat zásobníku vlákna, chcete-li zjistit, proč dochází k zámek zavaděče a pokyny k vyřešení problému.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také:
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
