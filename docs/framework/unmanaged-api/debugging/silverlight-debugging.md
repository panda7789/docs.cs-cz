---
title: "Ladění aplikací Silverlight"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6869e58ca47b7b55a5b988e0f6ae4a224f0f35a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="silverlight-debugging"></a>Ladění aplikací Silverlight
Témata v této části popisují prostředí a rozhraní, které modul CLR (CLR) poskytuje pro podporu ladění aplikace založená na technologii Silverlight, které běží na operačním systému Windows, nebo na platformě Macintosh.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [EnumerateCLRs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Poskytuje mechanismus pro vytvoření výčtu CLRs v procesu.  
  
 [CloseCLREnumeration – funkce](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Zavře platný události pokračovat spuštění CLR umístěný v pole vrácené obslužné rutiny [enumerateclrs – funkce](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)a uvolní paměť pro cestu pole popisovač a řetězec.  
  
 [CreateCoreClrDebugTarget – funkce](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Vytvoří připojení ke vzdálené cíle pro výčet proces a modulu runtime.  
  
 [CreateCordbObject – funkce](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Vytvoří rozhraní ladicí program, který poskytuje funkci pro vytvoření instance spravované ladicí relace na vzdálený proces.  
  
 [CreateVersionStringFromModule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Vytvoří řetězec verze z cesty CLR v Cílový proces.  
  
 [CreateDebuggingInterfaceFromVersion – funkce](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Přijímá řetězec verze CLR vrácená z [createversionstringfrommodule – funkce](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)fungovat a vrátí odpovídající rozhraní ladicího programu.  
  
 [CoreClrDebugProcInfo – struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Představuje proces, který běží na vzdáleném počítači.  
  
 [CoreClrDebugRuntimeInfo – struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Reprezentuje instanci CLR, který je načten do procesu ve vzdáleném počítači.  
  
 [GetStartupNotificationEvent – funkce](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Vytvoří nebo otevře popisovač události, který se bude dát signál při jakékoli modul common language runtime (CLR), se načítá v zadaný cílový proces.  
  
 [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Vytvoří připojení ke vzdálené cíle pro výčet proces a modulu runtime.  
  
 [InitDbgTransportManager – funkce](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicializuje správce přenosu pro připojení k vzdálené cíle pro výčet proces a modulu runtime.  
  
 [ShutdownDbgTransportManager – funkce](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Správce přenosu pro připojení k vzdálené cílový počítač vypne.  
  
## <a name="see-also"></a>Viz také  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
