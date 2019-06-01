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
ms.openlocfilehash: fc3f9c9c61afd4c231846adffc4b304a01d59281
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457253"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Čítače výkonu a vnitroprocesorové souběžné aplikace
Použití nástroje Sledování výkonu (Perfmon.exe), je možné odlišit od čítače výkonu na základě za běhu. Toto téma popisuje změny registru potřebná k povolení této funkce.  
  
## <a name="the-default-behavior"></a>Výchozí chování  
 Ve výchozím nastavení zobrazí Monitor výkonu čítače výkonu na základě jednotlivých aplikací. Nicméně existují dva scénáře, ve kterých je to problematické:  
  
- Když monitorujete dvě aplikace, které mají stejný název. Například, pokud obě aplikace jsou s názvem myapp.exe, zobrazí se některá jako **myapp** a ostatní jako **myapp č. 1** v **Instance** sloupce. V takovém případě je tak, aby odpovídaly čítače výkonu ke konkrétní aplikaci. Není jasné, jestli se data shromažďována pro **myapp č. 1** odkazuje na první myapp.exe nebo druhý myapp.exe.  
  
- Pokud aplikace používá více instancí modulu common language runtime. [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Podporuje vnitroprocesové vedle sebe scénáře hostingu; to znamená, může jeden proces nebo aplikace načítají více instancí modulu common language runtime. Pokud si jednu aplikaci s názvem myapp.exe zatížení dvě instance modulu runtime, ve výchozím nastavení, budou označeny v **Instance** jako sloupec **myapp** a **myapp č. 1**. V takovém případě není jasné, jestli **myapp** a **myapp č. 1** označovat dvě aplikace se stejným názvem nebo stejnou aplikaci pomocí dvou modulů runtime. Pokud více aplikací se stejným názvem načíst různými moduly runtime, je ještě lepší nejednoznačnost.  
  
 Můžete nastavit klíč registru, chcete-li odstranit tuto nejednoznačnost. U aplikací vyvinutých pomocí rozhraní .NET Framework 4, tato změna registru přidá identifikátor procesu, za nímž následuje identifikátor instance modulu runtime pro název aplikace **Instance** sloupce. Místo *aplikace* nebo *aplikace*#1, aplikace je nyní označena jako *aplikace*_`p`*processID* \_ `r` *runtimeID* v **Instance** sloupce. Pokud aplikace byla vyvinutá pomocí předchozí verze common language runtime, že instance reprezentována jako *aplikace\_* `p`*processID* za předpokladu, že. NET Framework 4 je nainstalována.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Čítače výkonu pro aplikace vedle sebe v procesu  
 Pro zpracování čítače výkonu pro více common language runtime verze, které jsou hostované v jedné aplikaci, je nutné změnit klíč jednoho registru nastavení, jak je znázorněno v následující tabulce.  
  
|||  
|-|-|  
|Název klíče|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|Název hodnoty|ProcessNameFormat|  
|Typ hodnoty|REG_DWORD|  
|Hodnota|1 (0x00000001)|  
  
 Hodnota 0 pro `ProcessNameFormat` označuje, že výchozí chování je povoleno; který je Perfmon.exe zobrazuje čítače výkonu na základě jednotlivých aplikací. Když nastavíte tuto hodnotu na 1, Perfmon.exe umožňuje rozlišit několik verzí aplikace a poskytuje čítače výkonu na základě za běhu. Jakákoli jiná hodnota parametru `ProcessNameFormat` nastavení klíče registru se neposkytuje podpora a vyhrazené pro budoucí použití.  
  
 Po aktualizaci `ProcessNameFormat` klíč registru nastavení, nebo je nutné restartovat Perfmon.exe ostatní uživatelé čítačů výkonu tak, aby nové instance pojmenování funkce funguje správně.  
  
 Následující příklad ukazuje, jak změnit `ProcessNameFormat` hodnotu prostřednictvím kódu programu.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Pokud tuhle změnu registru provádíte, Perfmon.exe zobrazí názvy aplikací, které jsou cíleny rozhraní .NET Framework 4 jako *aplikace*_`p`*processID* \_ `r` *runtimeID*, kde *aplikace* je název aplikace, *processID* je identifikátor procesu aplikace, a  *runtimeID* je obecný identifikátor modulu runtime jazyka. Například pokud aplikace s názvem myapp.exe zatížení dvě instance modulu common language runtime, Perfmon.exe může určit jednu instanci jako myapp_p1416_r10 a druhý jako myapp_p3160_r10. Identifikátor modulu runtime umožňuje rozlišit pouze moduly Runtime v rámci procesu. neposkytuje žádné další informace o modulu runtime. (Například ID modulu runtime nemá žádný vztah k verzi nebo SKU modulu runtime.)  
  
 Pokud je nainstalované rozhraní .NET Framework 4, registru změna také ovlivní aplikace, které byly vytvořeny pomocí dřívějších verzích rozhraní .NET Framework. Zobrazují se v Perfmon.exe jako *application_* `p`*processID*, kde *aplikace* je název aplikace a *processID* je identifikátor procesu. Například pokud dvě aplikace s názvem myapp.exe čítače výkonu jsou monitorovány, jeden se může zobrazit jako myapp_p23900 a druhý jako myapp_p24908.  
  
> [!NOTE]
>  Identifikátor procesu eliminuje nejednoznačnost řešení dvě aplikace se stejným názvem, které používají starší verze modulu runtime. Identifikátor modulu runtime se nevyžaduje pro předchozí verze, protože předchozí verze common language runtime nepodporují scénáře vedle sebe.  
  
 Pokud rozhraní .NET Framework 4 není k dispozici nebo se odinstaluje, nastavení klíče registru nemá žádný vliv. To znamená, že dvě aplikace se stejným názvem, bude i nadále zobrazovat v Perfmon.exe jako *aplikace* a *aplikace č. 1* (například jako **myapp** a **myapp č. 1**).
