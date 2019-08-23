---
title: Čítače výkonu a vnitroprocesorové souběžné aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c583e9568a55b994f0516af2dcdf29f0d0f21fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967278"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Čítače výkonu a vnitroprocesorové souběžné aplikace
Pomocí nástroje sledování výkonu (Perfmon. exe) je možné odlišit čítače výkonu v závislosti na modulu runtime. Toto téma popisuje změnu registru nutnou k povolení této funkce.  
  
## <a name="the-default-behavior"></a>Výchozí chování  
 Ve výchozím nastavení monitor výkonu zobrazuje čítače výkonu na základě jednotlivých aplikací. Existují však dva scénáře, ve kterých je to problematické:  
  
- Když sledujete dvě aplikace, které mají stejný název. Například pokud jsou obě aplikace pojmenovány MyApp. exe, jedna se zobrazí jako MyApp a druhá jako **MyApp # 1** ve sloupci **instance** . V takovém případě je obtížné porovnat čítač výkonu s určitou aplikací. Není jasné, zda data shromážděná pro **MyApp # 1** odkazují na první MyApp. exe nebo druhý myapp. exe.  
  
- Když aplikace používá více instancí modulu CLR (Common Language Runtime). .NET Framework 4 podporuje scénáře souběžného hostování v procesu; To znamená, že jeden proces nebo aplikace může načíst více instancí modulu CLR (Common Language Runtime). Pokud jedna aplikace s názvem MyApp. exe načte dvě instance modulu runtime, budou ve výchozím nastavení označeny ve sloupci **instance** jako **MyApp** a **MyApp # 1**. V tomto případě není jasné, zda **MyApp** a **MyApp # 1** odkazují na dvě aplikace se stejným názvem nebo na stejnou aplikaci se dvěma moduly runtime. Pokud více aplikací se stejným názvem načte více modulů runtime, nejednoznačnost je ještě větší.  
  
 Můžete nastavit klíč registru, který eliminuje tuto nejednoznačnost. U aplikací vyvinutých pomocí .NET Framework 4 přidá tato změna registru identifikátor procesu následovaný identifikátorem instance modulu runtime do názvu aplikace ve sloupci **instance** . Namísto #1 *aplikace* nebo *aplikace*je nyní aplikace označena jako *Application*_`p`*ProcessID*\_`r`*runtimeID* ve sloupci **instance** . Pokud byla aplikace vyvinuta pomocí předchozí verze modulu CLR (Common Language Runtime), je tato instance reprezentovaná jako *Application\_* `p`*ProcessID* , pokud je nainstalovaná .NET Framework 4.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Čítače výkonu pro vnitroprocesové souběžné aplikace  
 Chcete-li zpracovat čítače výkonu pro více verzí modulu CLR, které jsou hostovány v jediné aplikaci, je nutné změnit nastavení jednoho klíče registru, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Název klíče|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|Název hodnoty|ProcessNameFormat|  
|Typ hodnoty|REG_DWORD|  
|Value|1 (0x00000001)|  
  
 Hodnota 0 pro `ProcessNameFormat` označuje, že je povoleno výchozí chování. to znamená, že nástroj Perfmon. exe zobrazuje čítače výkonu pro jednotlivé aplikace. Když nastavíte hodnotu 1, program Perfmon. exe nejednoznačně vyřadí více verzí aplikace a poskytuje čítače výkonu pro jednotlivé moduly runtime. Jakákoli jiná hodnota `ProcessNameFormat` nastavení klíče registru není podporována a je vyhrazena pro budoucí použití.  
  
 Po aktualizaci `ProcessNameFormat` nastavení klíče registru je nutné restartovat soubor Perfmon. exe nebo všechny další uživatele čítačů výkonu, aby nová funkce pro pojmenovávání instancí fungovala správně.  
  
 Následující příklad ukazuje, jak změnit `ProcessNameFormat` hodnotu programově.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Když uděláte tuto změnu v registru, nástroj Perfmon. exe zobrazí názvy aplikací, které cílí na .NET Framework 4 jako *Application*_`p`*ProcessID*\_`r`*runtimeID*, kde *aplikace* je název aplikace, *ProcessID* je identifikátor procesu aplikace a *runtimeID* je identifikátor společného jazykového modulu runtime. Například pokud aplikace s názvem MyApp. exe načte dvě instance modulu CLR (Common Language Runtime), program Perfmon. exe může identifikovat jednu instanci jako myapp_p1416_r10 a druhou jako myapp_p3160_r10. Identifikátor modulu runtime nejednoznačně modul runtime v rámci procesu; neposkytuje žádné další informace o modulu runtime. (Například běhové ID nemá žádný vztah k verzi nebo SKU modulu runtime.)  
  
 Pokud je nainstalovaná .NET Framework 4, změna registru ovlivní také aplikace, které byly vyvinuty pomocí předchozích verzí .NET Framework. Zobrazují se v souboru Perfmon. exe jako *Application_* `p`*ProcessID*, kde *aplikace* je název aplikace a *ProcessID* je identifikátor procesu. Například pokud jsou monitorovány čítače výkonu dvou aplikací s názvem MyApp. exe, může se jedna zobrazit jako myapp_p23900 a druhá jako myapp_p24908.  
  
> [!NOTE]
> Identifikátor procesu eliminuje nejednoznačnost při řešení dvou aplikací se stejným názvem, které používají starší verze modulu runtime. Identifikátor modulu runtime není pro předchozí verze vyžadován, protože předchozí verze modulu CLR (Common Language Runtime) nepodporují souběžné scénáře.  
  
 Pokud .NET Framework 4 není k dispozici nebo byl odinstalován, nastavení klíče registru nemá žádný vliv. To znamená, že se dvě aplikace se stejným názvem budou dál zobrazovat v souboru Perfmon. exe jako *aplikace* a *aplikace # 1* (například jako **MyApp** a **MyApp # 1**).
