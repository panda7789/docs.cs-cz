---
title: Ladění aplikací Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790315"
---
# <a name="silverlight-debugging"></a>Ladění aplikací Silverlight
Témata v této části popisují prostředí a rozhraní, které modul CLR (Common Language Runtime) poskytuje pro podporu ladění aplikací založených na programu Silverlight, které jsou spuštěny v operačním systému Windows nebo na platformě Macintosh.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [EnumerateCLRs – funkce](enumerateclrs-function.md)  
 Poskytuje mechanismus pro vytváření výčtu CLRs v procesu.  
  
 [CloseCLREnumeration – funkce](closeclrenumeration-function.md)  
 Ukončí všechny platné události před spuštěním CLR, které se nacházejí v poli popisovačů vrácených [funkcí EnumerateCLRs –](enumerateclrs-function.md), a uvolní paměť pro pole popisovače a cestu k řetězci.  
  
 [CreateCoreClrDebugTarget – funkce](createcoreclrdebugtarget-function.md)  
 Vytvoří připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
 [CreateCordbObject – funkce](createcordbobject-function.md)  
 Vytvoří rozhraní ladicího programu, které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.  
  
 [CreateVersionStringFromModule – funkce](createversionstringfrommodule-function.md)  
 Vytvoří řetězec verze z cesty CLR v cílovém procesu.  
  
 [CreateDebuggingInterfaceFromVersion – funkce](createdebugginginterfacefromversion-function-for-silverlight.md)  
 Přijímá řetězec verze CLR vrácený funkcí [CreateVersionStringFromModule – funkce](createversionstringfrommodule-function.md)a vrátí odpovídající rozhraní ladicího programu.  
  
 [CoreClrDebugProcInfo – struktura](coreclrdebugprocinfo-structure.md)  
 Představuje proces, který je spuštěn ve vzdáleném počítači.  
  
 [CoreClrDebugRuntimeInfo – struktura](coreclrdebugruntimeinfo-structure.md)  
 Představuje instanci CLR, která je načtena v procesu ve vzdáleném počítači.  
  
 [GetStartupNotificationEvent – funkce](getstartupnotificationevent-function.md)  
 Vytvoří nebo otevře obslužnou rutinu události, která bude signalizována jakýmkoli modulem CLR (Common Language Runtime), který se načítá v zadaném cílovém procesu.  
  
 [ICoreClrDebugTarget – rozhraní](icoreclrdebugtarget-interface.md)  
 Vytvoří připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
 [InitDbgTransportManager – funkce](initdbgtransportmanager-function.md)  
 Inicializuje správce přenosu pro připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
 [ShutdownDbgTransportManager – funkce](shutdowndbgtransportmanager-function.md)  
 Ukončí Správce přenosů pro připojení ke vzdálenému cílovému počítači.  
  
## <a name="see-also"></a>Viz také:

- [Třídy typu coclass pro ladění](debugging-coclasses.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
- [Globální statické funkce pro ladění](debugging-global-static-functions.md)
- [Výčty pro ladění](debugging-enumerations.md)
- [Struktury pro ladění](debugging-structures.md)
