---
title: "Migrace z rozhraní .NET Framework 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework 4.5, migrating from 1.1
- .NET Framework 1.1, migrating to .NET Framework 4.5
ms.assetid: 7ead0cb3-3b19-414a-8417-a1c1fa198d9e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d54fac935e7b1fad6b07a3a6cf2031dbca702cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-from-the-net-framework-11"></a>Migrace z rozhraní .NET Framework 1.1
[!INCLUDE[win7](../../../includes/win7-md.md)]a novějších verzích operačního systému Windows nepodporuje [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)]. V důsledku toho aplikace cílené [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] nespustí bez úprav na [!INCLUDE[win7](../../../includes/win7-md.md)] nebo novější verze operačního systému. Toto téma popisuje kroky potřebné ke spuštění aplikace s cílem [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] pod [!INCLUDE[win7](../../../includes/win7-md.md)] a novějších verzích operačního systému Windows. Další informace o [!INCLUDE[net_v11_long](../../../includes/net-v11-long-md.md)] a [!INCLUDE[win8](../../../includes/win8-md.md)], najdete v části [spuštění rozhraní .NET Framework 1.1 aplikace ve Windows 8 a novějších verzích](../../../docs/framework/install/run-net-framework-1-1-apps.md).  
  
## <a name="retargeting-or-recompiling"></a>Změna orientace nebo nutnosti rekompilace  
 Existují dva způsoby, jak získat aplikace, který byl kompilován s použitím [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] ke spuštění na [!INCLUDE[win7](../../../includes/win7-md.md)] nebo novějšího operačního systému Windows:  
  
-   Můžete změnit cíl aplikací pro spuštění pod [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Změna orientace vyžaduje, abyste přidali [ \<supportedRuntime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) element do konfiguračního souboru aplikace, která povolí jeho spuštění v rámci [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Konfigurační soubor má následující podobu:  
  
    ```xml  
    <configuration>   
       <startup>  
          <supportedRuntime version="v4.0"/>  
       </startup>  
    </configuration>  
    ```  
  
-   Můžete znovu zkompiluje aplikace s kompilátoru, která je cílena [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Pokud jste použili k vývoji a kompilaci řešení Visual Studio 2003, můžete otevřít řešení v [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] a použít **projektu kompatibility** dialogové okno Převést z formátů používaných soubory řešení a projektu Visual Studio 2003 k Microsoft Build Engine (MSBuild) formát používaný [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)].  
  
 Bez ohledu na to, jestli chcete znovu zkompiluje nebo změnu cílové aplikace musíte určit, jestli vaše aplikace je ovlivňován změny zavedené v novějších verzích rozhraní .NET Framework. Tyto změny jsou dvou typů:  
  
-   Nejnovější změny, které došlo mezi [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] a novějších verzích rozhraní .NET Framework.  
  
-   Typy a členy typu, které byly označeny jako zastaralé nebo zastaralé mezi [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] a novějších verzích rozhraní .NET Framework.  
  
 Ať už změnu cílové aplikace nebo znovu zkompiluje ho, měli byste prostudovat nejnovější změny a zastaralé typy a členy pro každou verzi rozhraní .NET Framework, která byla vydána po [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
## <a name="breaking-changes"></a>Nejnovější změny  
 Když dojde k narušující změně, v závislosti na konkrétní změnu alternativní řešení může být k dispozici pro změnit cíl necílené i aplikace. V některých případech můžete přidat jako podřízený element [ \<runtime >](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) prvek konfiguračního souboru aplikace k obnovení předchozího chování. Například následující konfigurační soubor obnoví řetězec porovnání a řazení chování používány [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)] a dá se použít buď s přesměrovanou nebo překompilovanou aplikací.  
  
```xml  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
 V některých případech ale může mít k úpravě zdrojového kódu a znovu zkompiluje vaší aplikace.  
  
 Při posoudit dopad možných nejnovějších změn ve vaší aplikaci, musí přečíst seznamy následující změny:  
  
-   [Nejnovější změny v rozhraní .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=125263) změny dokumentů v [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] které můžou ovlivnit aplikaci, která je cílena [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)].  
  
-   [Změny v rozhraní .NET Framework 3.5 SP1](http://go.microsoft.com/fwlink/?LinkID=186989) dokumenty změny mezi [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)].  
  
-   [Rozhraní .NET framework 4 migrace problémy](../../../docs/framework/migration-guide/net-framework-4-migration-issues.md) dokumenty změny mezi [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
## <a name="obsolete-types-and-members"></a>Zastaralé typy a členy  
 Dopad zastaralé typy a členy se poněkud liší od revidovaných aplikací a aplikace. Použití zastaralé typy a členy neovlivní přesměrovanou aplikaci, pokud zastaralý typ nebo člen fyzicky odebrala se z jeho sestavení. Nutnosti rekompilace aplikaci, která používá zastaralé typy nebo členy obvykle vytváří kompilátor varování místo chybě kompilátoru. V některých případech ale vyvolá chybu kompilátoru a kód, který používá zastaralý typ nebo člen nekompiluje úspěšně. V takovém případě musí přepsat zdrojový kód, který volá zastaralé typ nebo člen předtím, než můžete znovu zkompiluje vaší aplikace. Další informace o zastaralé typy a členy najdete v tématu [co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md).  
  
 K posouzení dopad typy a členy, kteří jsou zastaralé od verze [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], najdete v části [co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md). Zkontrolujte seznam zastaralé typy a člena [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)], [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]a [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].
