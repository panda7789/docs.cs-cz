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
ms.openlocfilehash: cd77640a6566f3fd94631dac184ae5bc3ffab5d1
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217353"
---
# <a name="loaderlock-mda"></a>loaderLock – pomocník spravovaného ladění (MDA)
`loaderLock` Pomocník pro spravované ladění (MDA) detekuje pokusy o spuštění spravovaného kódu ve vlákně, které má zámek zavaděče operačního systému Microsoft Windows.  Jakékoli takové spuštění je neplatné, protože může vést k zablokování a používání knihoven DLL předtím, než byly inicializovány zavaděčem operačního systému.  
  
## <a name="symptoms"></a>Příznaky  
 Nejběžnějším selháním při spouštění kódu uvnitř zámku zavaděče operačního systému je, že při pokusu o volání dalších funkcí Win32, které také vyžadují zámek zavaděče, budou vlákna zablokována.  Příklady takových funkcí jsou `LoadLibrary`, `GetProcAddress`, `FreeLibrary`a `GetModuleHandle`.  Aplikace nemusí přímo volat tyto funkce; modul CLR (Common Language Runtime) může volat tyto funkce jako výsledek volání vyšší úrovně, jako je například <xref:System.Reflection.Assembly.Load%2A> nebo první volání metody Invoke platformy.  
  
 K zablokování může docházet také v případě, že vlákno čeká na spuštění nebo dokončení jiného vlákna.  Když se vlákno spustí nebo dokončí, musí získat zámek zavaděče operačního systému, aby mohl doručovat události do ovlivněných knihoven DLL.  
  
 Nakonec existují případy, kdy volání do knihoven DLL mohou nastat předtím, než tyto knihovny DLL byly správně inicializovány zavaděčem operačního systému.  Na rozdíl od chyb zablokování, které mohou být diagnostikovány kontrolou zásobníků všech vláken zapojených do zablokování, je velmi obtížné diagnostikovat použití neinicializovaných knihoven DLL bez použití tohoto procesu MDA.  
  
## <a name="cause"></a>Příčina  
 Smíšená spravovaná a C++ nespravovaná sestavení vytvořená pro .NET Framework verze 1,0 nebo 1,1 se obecně pokusí spustit spravovaný kód uvnitř zámku zavaděče, pokud se nebere zvláštní péče, například propojení s **/NOENTRY**.
  
 Smíšená spravovaná a C++ nespravovaná sestavení vytvořená pro .NET Framework verze 2,0 jsou pro tyto problémy méně náchylná a mají stejné snížené riziko jako aplikace využívající nespravované knihovny DLL, které porušují pravidla operačního systému.  Pokud například `DllMain` vstupní bod nespravované knihovny DLL volá `CoCreateInstance` k získání spravovaného objektu, který byl vystaven modelu COM, je výsledkem pokus o spuštění spravovaného kódu uvnitř zámku zavaděče. Další informace o problémech uzamknutí zavaděče v .NET Framework verze 2,0 a novějších naleznete v tématu [inicializace smíšených sestavení](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Řešení  
 V jazyce C++ visual .NET 2002 a C++ Visual .NET 2003 by knihovny DLL zkompilované pomocí možnosti kompilátoru `/clr` mohly při načítání způsobit nedeterministické zablokování; Tento problém se volal při načítání smíšených knihoven DLL nebo potíží s zámkem zavaděče. V jazyce C++ Visual 2005 a novějším byla téměř všechna determinismem odebrána z smíšeného procesu načítání knihovny DLL. Existuje však několik zbývajících scénářů, pro které může dojít k uzamknutí zavaděče (k deterministickému). Podrobný účet příčin a řešení pro zbývající problémy zámků zavaděče naleznete v tématu [inicializace smíšených sestavení](/cpp/dotnet/initialization-of-mixed-assemblies). Pokud toto téma neidentifikuje váš problém uzamknutí zavaděče, je nutné prostudovat zásobník vlákna, abyste zjistili, proč k uzamknutí zavaděče dojde, a jak problém vyřešit. Podívejte se na trasování zásobníku pro vlákno, které aktivovalo Tento MDA.  Vlákno se pokouší o neoprávněné volání spravovaného kódu, zatímco drží zámek zavaděče operačního systému.  Pravděpodobně se v zásobníku zobrazí `DllMain` nebo ekvivalentní vstupní bod knihovny DLL.  Pravidla operačního systému pro to, co můžete právně dělat, se v tomto vstupním bodě poměrně omezí.  Tato pravidla vylučují jakékoli spravované spuštění.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul runtime  
 Obvykle se několik vláken uvnitř procesu zablokuje.  Jedním z těchto vláken je pravděpodobně podproces zodpovědný za provedení uvolňování paměti, takže toto zablokování může mít významný dopad na celý proces.  Kromě toho zabrání žádné další operace, které vyžadují zámek zavaděče operačního systému, jako je načítání a uvolňování sestavení nebo knihoven DLL a spuštění nebo zastavení vláken.  
  
 V některých neobvyklých případech je také možné, že dojde k narušení přístupu nebo k podobným problémům v knihovnách DLL, které jsou volány před inicializací.  
  
## <a name="output"></a>Výstup  
 Tento MDA hlásí, že probíhá pokus o neoprávněné spravované spuštění.  Je nutné prostudovat zásobník vlákna, abyste zjistili, proč k uzamknutí zavaděče dojde, a jak tento problém vyřešit.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Viz také

- [Diagnostikování chyb pomocí asistentů spravovaného ladění](diagnosing-errors-with-managed-debugging-assistants.md)
