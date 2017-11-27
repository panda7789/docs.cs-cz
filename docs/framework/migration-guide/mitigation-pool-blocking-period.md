---
title: "Omezení rizik: Fond Blocking období"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92d2de20-79be-4df1-b182-144143a8866a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8749e2d7b91e611ee153c6f36708fa34a44ecccd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-pool-blocking-period"></a>Omezení rizik: Fond Blocking období
Odebrali jsme blokování období fondu připojení pro připojení k databázím Azure SQL.  
  
## <a name="additional-description"></a>Další popis  
 V [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a starší verze, když aplikace zaznamená přechodné chybě při připojování k databázi, pokus o připojení nejde opakovat rychle, protože fond připojení ukládá do mezipaměti chyby a znovu vyvolá po dobu 5 sekund do 1 min. Další informace najdete v tématu [SQL sdružování připojení serveru (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md). Toto chování je problematické pro připojení k databázím Azure SQL, které často dojde k chybě přechodné chyby, které jsou obvykle obnovit z během několika sekund. Funkce připojení k fondu blokování znamená, že aplikace nemůže připojit k databázi pro rozsáhlé období, i když je databáze dostupná. Toto chování je obzvláště problematické pro webové aplikace, která připojení k databázím Azure SQL a které jsou nutné k vykreslení během několika sekund.  
  
 Od verze [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], připojení otevřené žádosti o známé databází Azure SQL (*. database.windows.net, \*. database.chinacloudapi.cn, \*. database.usgovcloudapi.net, \*. database.cloudapi.de), Otevřete chyb připojení se neukládají do mezipaměti. Pro všechny ostatní pokusy o připojení i nadále vynucovat blokování období fondu připojení.  
  
## <a name="impact"></a>Dopad  
 Tato změna umožňuje otevřete pokus o připojení k okamžitě opakovat u databází Azure SQL, a tím zvýšení výkonu aplikací povolenou podporu cloudu.  
  
## <a name="mitigation"></a>Zmírnění  
 Aplikace, které jsou negativně ovlivněn touto změnou, blokování období fondu připojení se dá nakonfigurovat pomocí nastavení nové <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnost.  Hodnota vlastnosti je členem skupiny <xref:System.Data.SqlClient.PoolBlockingPeriod?displayProperty=nameWithType> výčet, který může mít jednu ze tří hodnot:  
  
-   `PoolBlockingPeriod.AlwaysBlock` 
  
-   `PoolBlockingPeriod.Auto`  
  
-   `PoolBlockingPeriod.NeverBlock` 
  
 Předchozí chování může být obnovena nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.PoolBlockingPeriod%2A> vlastnost `PoolBlockingPeriod.AlwaysBlock`.  
  
## <a name="see-also"></a>Viz také  
 [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
