---
title: Ladění aplikací Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139138"
---
# <a name="silverlight-debugging"></a>Ladění aplikací Silverlight
Témata v této části popisují prostředí a rozhraní, které modul CLR (Common Language Runtime) poskytuje pro podporu ladění aplikací založených na programu Silverlight, které jsou spuštěny v operačním systému Windows nebo na platformě Macintosh.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [EnumerateCLRs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Poskytuje mechanismus pro vytváření výčtu CLRs v procesu.  
  
 [CloseCLREnumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Ukončí všechny platné události před spuštěním CLR, které se nacházejí v poli popisovačů vrácených [funkcí EnumerateCLRs –](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), a uvolní paměť pro pole popisovače a cestu k řetězci.  
  
 [CreateCoreClrDebugTarget – funkce](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Vytvoří připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
 [CreateCordbObject – funkce](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Vytvoří rozhraní ladicího programu, které poskytuje funkce pro vytvoření instance spravované relace ladění na vzdáleném procesu.  
  
 [CreateVersionStringFromModule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Vytvoří řetězec verze z cesty CLR v cílovém procesu.  
  
 [CreateDebuggingInterfaceFromVersion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Přijímá řetězec verze CLR vrácený funkcí [CreateVersionStringFromModule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)a vrátí odpovídající rozhraní ladicího programu.  
  
 [CoreClrDebugProcInfo – struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Představuje proces, který je spuštěn ve vzdáleném počítači.  
  
 [CoreClrDebugRuntimeInfo – struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Představuje instanci CLR, která je načtena v procesu ve vzdáleném počítači.  
  
 [GetStartupNotificationEvent – funkce](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Vytvoří nebo otevře obslužnou rutinu události, která bude signalizována jakýmkoli modulem CLR (Common Language Runtime), který se načítá v zadaném cílovém procesu.  
  
 [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Vytvoří připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
 [InitDbgTransportManager – funkce](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicializuje správce přenosu pro připojení ke vzdálenému cíli pro proces a výčet za běhu.  
  
 [ShutdownDbgTransportManager – funkce](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Ukončí Správce přenosů pro připojení ke vzdálenému cílovému počítači.  
  
## <a name="see-also"></a>Viz také:

- [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
