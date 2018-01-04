---
title: "Omezení rizik: Vykreslování oken ve WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 032d07b75b96809ff71c7735a267a7351ad25dda
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-wpf-window-rendering"></a>Omezení rizik: Vykreslování oken ve WPF
V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] systémem Windows 8 a vyšší, celé okno je vykreslen bez výstřižek, pokud ji rozšiřuje mimo jednoho zobrazení ve scénáři s více monitorování.  
  
## <a name="impact"></a>Dopad  
 Obecně platí vykreslování celého okna víc monitorů bez výstřižek je očekávané chování. V systému Windows 7 a starší verze, jsou však WPF windows oříznut, pokud rozšířit nad rámec jednoho zobrazení protože vykreslování část okna na druhém monitoru má vliv významně zvýšit výkon.  
  
 Přesné dopad vykreslování WPF windows na monitory v systému Windows 8 a vyšší není přesně vyčíslitelný, protože závisí na velkého počtu faktorů. V některých případech se může stále vytvořit nežádoucí vliv na výkon, hlavně pro uživatele, kteří spustit aplikace náročné na grafiky a windows tažných monitorování. V ostatních případech jednoduše můžete konzistentní chování napříč verze rozhraní .NET Framework.  
  
## <a name="mitigation"></a>Zmírnění  
 Můžete zakázat tuto změnu a vrátit k předchozí chování výstřižek okno WPF při přesahoval jednoho zobrazení. Toto lze provést dvěma způsoby:  
  
-   Přidáním `<EnableMultiMonitorDisplayClipping>` elementu, který chcete `<appSettings>` oddíl v konfiguračním souboru aplikace, můžete zakázat nebo povolit toto chování na aplikace běžící v systému Windows 8 nebo novější. Například následující konfigurační oddíl zakáže vykreslování bez výstřižek:  
  
    ```xml  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
    ```  
  
     `<EnableMultiMonitorDisplayClipping>` Nastavení konfigurace může mít buď ze dvou hodnot:  
  
    -   `true`, chcete-li povolit výstřižek systému windows ke sledování hranice během vykreslování.  
  
    -   `false`, chcete-li zakázat výstřižek systému windows ke sledování hranice během vykreslování.  
  
-   Nastavením <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> vlastnost `true` při spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
