---
title: Ladění aplikací Silverlight
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d20bc002e52c3c6a42b45c0d1c5d559e65dc52c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763660"
---
# <a name="silverlight-debugging"></a>Ladění aplikací Silverlight
Témata v této části popisují prostředí a rozhraní, které modul CLR (CLR) poskytuje pro podporu ladění aplikace programu Silverlight, které jsou spuštěny v operačním systému Windows nebo na platformě Macintosh.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [EnumerateCLRs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.  
  
 [CloseCLREnumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Zavře platné události pokračovat po spuštění CLR nachází v poli popisovačů vrácené [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězce.  
  
 [CreateCoreClrDebugTarget – funkce](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Vytvoří připojení k vzdálené cílové pro výčet procesu a modulu runtime.  
  
 [CreateCordbObject – funkce](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Vytvoří rozhraní ladicího programu, který poskytuje funkce pro vytvoření instance spravované ladicí relace na vzdálený proces.  
  
 [CreateVersionStringFromModule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Vytvoří řetězec verze z cesty CLR v cílovém procesu.  
  
 [CreateDebuggingInterfaceFromVersion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Přijímá řetězec verze modulu CLR vrácená [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)funkci a vrátí odpovídající rozhraní ladicího programu.  
  
 [CoreClrDebugProcInfo – struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Představuje proces, který běží na vzdáleném počítači.  
  
 [CoreClrDebugRuntimeInfo – struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Představuje instanci modulu CLR, který je načten v procesu ve vzdáleném počítači.  
  
 [GetStartupNotificationEvent – funkce](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Vytvoří nebo otevře popisovač události, která bude být signalizován při libovolné CLR (CLR), který se načítá do zadaného cílového procesu.  
  
 [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Vytvoří připojení k vzdálené cílové pro výčet procesu a modulu runtime.  
  
 [InitDbgTransportManager – funkce](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicializuje správce přenosu pro připojení k vzdálené cílové pro výčet procesu a modulu runtime.  
  
 [ShutdownDbgTransportManager – funkce](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Správce přenosu pro připojení k vzdálené cílový počítač vypne.  
  
## <a name="see-also"></a>Viz také:

- [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
