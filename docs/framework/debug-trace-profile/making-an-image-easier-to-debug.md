---
title: Usnadnění ladění obrázku
ms.date: 03/30/2017
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c58008bc621ea95fbb2e4cc5e7d4521576aca37c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="making-an-image-easier-to-debug"></a>Usnadnění ladění obrázku
Při kompilaci nespravovaného kódu je možné nakonfigurovat spustitelnou bitovou kopii pro ladění nastavením přepínačů IDE nebo parametrů příkazového řádku. Například můžete použít nebo**Zi** možnost příkazového řádku v jazyce Visual C++ a požádejte ho pro vydávání soubory ladění symbolu (.pdb přípona souboru). Podobně /**Od** říká možnost příkazového řádku kompilátoru zakázat optimalizace. Výsledný kód pracuje pomaleji, ale je snadnější v něm v případě potřeby provádět ladění.  
  
 Při kompilaci spravovaného kódu rozhraní .NET Framework kompilují kompilátory jazyků jako Visual C++, Visual Basic a C# vlastní zdrojové programy do jazyka MSIL (Microsoft Intermediate Language). Jazyk MSIL je následně těsně před spuštěním překompilován JIT kompilátorem do nativního strojového kódu. Stejně jako u nespravovaného kódu je možné nakonfigurovat spustitelnou bitovou kopii pro ladění nastavením přepínačů IDE nebo parametrů příkazového řádku. Kromě toho lze kompilaci JIT nastavit pro ladění v podstatě stejným způsobem.  
  
 Tato konfigurace JIT má dva aspekty:  
  
-   Je možné požadovat po JIT kompilátoru generování informací o sledování. To umožňuje ladicímu programu nalézt shodu se svým protějškem strojového kódu řetězce jazyka MSIL a sledovat, kde jsou uloženy místní proměnné a argumenty funkce.  V rozhraní .NET Framework 2.0 bude kompilátor JIT vždy generovat informace o sledování, a není tedy nutné o ně žádat.  
  
-   Je možné požadovat po kompilátoru JIT, aby neprováděl optimalizaci výsledného strojového kódu.  
  
 Za normálních okolností kompilátoru, která generuje MSIL nastaví tyto možnosti JIT kompilátoru správně, na základě přepínačů IDE nebo možnosti příkazového řádku zadáte, například /**Od**.  
  
 V některých případech bude zapotřebí změnit chování kompilátoru JIT tak, aby bylo možné strojový kód, který generuje, snadněji ladit. Například může být třeba generovat informace o sledování JIT pro sestavení prodejní verze nebo pro optimalizaci řízení. To lze provést pomocí inicializačního souboru (.ini).  
  
 Pokud se například sestavení, které je třeba ladit, nazývá MyApp.exe, je možné vytvořit textový soubor s názvem MyApp.ini ve stejné složce jako MyApp.exe, který bude obsahovat tyto tři řádky:  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 Hodnotu každé možnosti lze nastavit na 0 nebo 1 a chybějící možnost bude mít výchozí hodnotu 0. Nastavení volby `GenerateTrackingInfo` na hodnotu 1 a volby `AllowOptimize` na hodnotu 0 poskytuje nejjednodušší ladění.  
  
> [!NOTE]
>  V rozhraní .NET Framework 2.0 bude JIT kompilátor vždy generovat informace o sledování bez ohledu na hodnotu volby `GenerateTrackingInfo`, nicméně hodnota volby `AllowOptimize` má účinek. Při použití [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) předkompilovat Nativní bitová kopie bez optimalizace, musí být soubor .ini v cílové složce s `AllowOptimize=0` při Ngen.exe provede. Pokud máte předkompilovaných sestavení bez optimalizace, musíte odebrat předkompilovaných kódu pomocí NGen.exe **/ uninstall** možnost před opětovným spuštěním Ngen.exe předkompilovat kód jako optimalizované. Není-li ve složce k dispozici soubor .ini, provede soubor Ngen.exe předkompilování kódu jako optimalizovaného.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> určuje nastavení sestavení. **Atribut DebuggableAttribute** zahrnuje dvě pole, které záznam nastavení pro zda by měl optimalizace kompilátoru za běhu, a generovat informace o sledování. V rozhraní .NET Framework 2.0 bude JIT kompilátor vždy generovat informace o sledování.  
  
> [!NOTE]
>  Pro maloobchodní sestavení, kompilátory není nastaveno žádné **atribut DebuggableAttribute**. Výchozím chováním JIT kompilátoru je generování nejvyššího výkonu strojového kódu s nejtěžší možností ladění. Povolením JIT sledování se snižuje výkon a vypnutím optimalizace se výkon razantně snižuje.  
  
> [!NOTE]
>  **Atribut DebuggableAttribute** se vztahují na celé sestavení v čase, nikoli na jednotlivé moduly v rámci sestavení. Nástroje pro vývoj musí proto přiřadit vlastní atributy token metadata sestavení, pokud sestavení se již byly vytvořeny, nebo k třídě volá **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. Nástroj ALink bude povýšit, pak tyto **atribut DebuggableAttribute** atributů z modulů sestavení stanou součástí. Pokud dojde ke konfliktu, operace nástroje ALink se nezdaří.  
  
> [!NOTE]
>  V rozhraní .NET Framework verze 1.0, Microsoft Visual C++ compiler přidá **atribut DebuggableAttribute** při **/CLR** a **/Zi** – možnosti kompilátoru nejsou zadány. V rozhraní .NET Framework verze 1.1, musíte buď přidat **DebugabbleAttribute** ručně v kódu nebo použití **/ASSEMBLYDEBUG** – možnost linkeru.  
  
## <a name="see-also"></a>Viz také  
 [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)  
 [Povolení JIT – ladění Attach](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [Povolení profilace](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
