---
title: "Čítače výkonu a vnitroprocesorové souběžné aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: acbdf1ff1f2827bf607c2f838685d5161af61fd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Čítače výkonu a vnitroprocesorové souběžné aplikace
Použití nástroje Sledování výkonu (Perfmon.exe), je možné rozlišit čítače výkonu na základě za běhu. Toto téma popisuje změnu registru potřebné pro tuto funkci povolit.  
  
## <a name="the-default-behavior"></a>Výchozí chování  
 Sledování výkonu ve výchozím nastavení, zobrazí čítače výkonu na základě jednotlivých aplikací. Nicméně existují dva scénáře, ve kterých jde problematické:  
  
-   Když monitorujete dvě aplikace, které mají stejný název. Například, pokud jsou obě aplikace myapp.exe, zobrazí se některá jako **Moje aplikace** a jiných jako **myapp č. 1** v **Instance** sloupce. V takovém případě je tak, aby odpovídaly čítače výkonu ke konkrétní aplikaci. Není jasné, jestli se data shromažďují pro **myapp č. 1** odkazuje na první myapp.exe nebo druhý myapp.exe.  
  
-   Pokud aplikace používá více instancí modul common language runtime. [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Podporuje v procesu scénáře hostingu vedle sebe; to znamená, může na jednom procesu nebo aplikaci načíst více instancí modul common language runtime. Pokud jednu aplikaci s názvem myapp.exe zatížení dvě instance runtime, ve výchozím nastavení, budou označeny v **Instance** sloupec jako **Moje aplikace** a **myapp č. 1**. V takovém případě není jasné zda **Moje aplikace** a **myapp č. 1** označovat dvě aplikace se stejným názvem nebo do stejné aplikace se dvěma moduly runtime. Pokud se více aplikací se stejným názvem načíst více moduly runtime, je ještě lepší nejednoznačnosti.  
  
 Můžete nastavit klíč registru, který tento nejasnostem. Pro aplikace vyvinuté pomocí [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], tato změna registru přidá identifikátor procesu, za nímž následuje identifikátor instance modul runtime na název aplikace v **Instance** sloupce. Místo *aplikace* nebo *aplikace*#1, aplikace je nyní označena jako *aplikace*_`p`*processID* \_ `r` *runtimeID* v **Instance** sloupce. Pokud aplikace byla vyvinutá pomocí předchozí verze modulu CLR, že instance reprezentována jako *aplikace\_*`p`*processID* za předpokladu, že [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] je nainstalovaná.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Čítače výkonu pro aplikace v rámci procesu vedle sebe  
 Pro zpracování čítače výkonu pro více běžné language runtime verze, které jsou hostované v jedné aplikaci, musíte změnit jeden klíč nastavení, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Název klíče|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\. NETFramework\Performance|  
|Název hodnoty|ProcessNameFormat|  
|Typ hodnoty|REG_DWORD|  
|Hodnota|1 (0x00000001)|  
  
 Hodnota 0 pro `ProcessNameFormat` označuje, že výchozí chování je povoleno; je Perfmon.exe zobrazuje čítače výkonu na základě jednotlivých aplikací. Pokud tuto hodnotu nastavíte na 1, Perfmon.exe umožňuje rozlišit několik verzí aplikace a poskytuje čítače výkonu na základě za běhu. Žádné jiné hodnoty pro `ProcessNameFormat` nastavení klíče registru je nepodporovaná a vyhrazená pro budoucí použití.  
  
 Po provedení aktualizace `ProcessNameFormat` klíče registru nastavení, je nutné restartovat Perfmon.exe nebo nějaké jiné příjemce čítačů výkonu, aby nová instance pojmenování funkce funguje správně.  
  
 Následující příklad ukazuje, jak změnit `ProcessNameFormat` hodnotu prostřednictvím kódu programu.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Pokud tuhle změnu registru provádíte, Perfmon.exe zobrazuje názvy aplikace cílených [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jako *aplikace*_`p`*processID* \_ `r` *runtimeID*, kde *aplikace* je název aplikace, *processID* je identifikátor procesu aplikace, a  *runtimeID* je obecný identifikátor runtime jazyka. Například pokud aplikace s názvem myapp.exe zatížení dvě instance modul common language runtime, Perfmon.exe může identifikovat jedna instance jako myapp_p1416_r10 a druhý jako myapp_p3160_r10. Identifikátor runtime jenom umožňuje rozlišit moduly Runtime v rámci procesu; neposkytuje žádné další informace o modulu runtime. (Například ID modulu runtime neobsahuje žádný vztah k verze nebo verze SKU modulu runtime.)  
  
 Pokud [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] je nainstalovaná, registru ovlivní tato změna také aplikace vyvinuté pomocí starší verze rozhraní .NET Framework. Zobrazují se v Perfmon.exe jako *application_*`p`*processID*, kde *aplikace* je název aplikace a *processID* je identifikátor procesu. Například pokud jsou čítače výkonu dvou aplikací s názvem myapp.exe, jedna, může vypadat myapp_p23900 a druhý jako myapp_p24908.  
  
> [!NOTE]
>  Identifikátor procesu eliminuje nejednoznačnosti překladu dvě aplikace se stejným názvem, které používají starší verze modulu runtime. Identifikátor runtime se nevyžaduje pro předchozí verze, protože předchozí verze modulu CLR nepodporují scénáře vedle sebe.  
  
 Pokud [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] není k dispozici nebo se odinstaluje, nastavení klíče registru nemá žádný vliv. To znamená, že dvě aplikace se stejným názvem bude i nadále zobrazovat v Perfmon.exe jako *aplikace* a *aplikace č. 1* (například jako **Moje aplikace** a **myapp č. 1**).
