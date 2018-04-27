---
title: Data trasování v technologii ADO.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a752a5-d2a9-4335-a382-b58690ccb79f
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 377c69feda356aee9e11720cf12c9c97158d45a7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="data-tracing-in-adonet"></a>Data trasování v technologii ADO.NET
ADO.NET funkce integrované data trasování funkce, které podporuje zprostředkovatele dat .NET pro SQL Server, Oracle, technologie OLE DB a rozhraní ODBC, jakož i technologie ADO.NET <xref:System.Data.DataSet>a protokoly sítě systému SQL Server.  
  
 Data trasování volání rozhraní API přístup může pomoci diagnostikovat následující problémy:  
  
-   Neshoda schémat mezi program klienta a databází.  
  
-   Databáze nedostupnosti nebo síťové problémy knihovny.  
  
-   Nesprávný SQL zda pevného programového nebo generovaných aplikací.  
  
-   Nesprávný programovací logiku.  
  
-   Problémy vyplývající z interakce mezi více součástí ADO.NET nebo mezi ADO.NET a vlastní součásti.  
  
 Pro podporu různých trasování technologie, je rozšiřitelný, trasování, takže vývojáři mohou sledovat potíže na libovolnou úroveň zásobníku aplikace. I když trasování není funkce pouze ADO.NET, zprostředkovatelé Microsoft využít výhod zobecněný trasování a instrumentace rozhraní API.  
  
 Další informace o nastavení a konfigurace spravovaných trasování v ADO.NET najdete v tématu [přístup k datům trasování](http://msdn.microsoft.com/library/hh880086.aspx).  
  
## <a name="accessing-diagnostic-information-in-the-extended-events-log"></a>Přístup k diagnostické informace v protokolu rozšířené události  
 V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server, přístup k datům trasování ([Data trasování přístup](http://msdn.microsoft.com/library/hh880086.aspx)) byl aktualizovaný, aby bylo snazší snazší ke korelaci událostí klienta s diagnostické informace, jako je například selhání připojení z připojení k serveru prstence vyrovnávací paměti a aplikace informace o výkonu v rozšířené události protokolu. Informace o čtení protokolu rozšířených událostí najdete v tématu [Data relace události zobrazení](http://msdn.microsoft.com/library/hh710068\(SQL.110\).aspx).  
  
 Pro operace připojení ADO.NET odešle klient ID připojení. Pokud se nepovede připojit, dostanete cyklické vyrovnávací paměti připojení ([řešení potíží s připojením v systému SQL Server 2008 s cyklické vyrovnávací paměti připojení](http://go.microsoft.com/fwlink/?LinkId=207752)) a najděte `ClientConnectionID` pole a získání diagnostických informací připojení se nezdařilo. ID připojení klienta jsou protokolovány v cyklické vyrovnávací paměti pouze v případě, že dojde k chybě. (V případě selhání připojení před odesláním paketu před přihlašováním, který nebude vygenerováno ID připojení klienta.) ID připojení klienta je identifikátor GUID 16 bajtů. Můžete také získat připojení klienta ID ve výstupu cíl rozšířených událostí, pokud `client_connection_id` akce se přidá k událostem v relaci rozšířených událostí. Můžete povolit přístup k trasování dat a znovu spusťte příkaz připojení a sledovat `ClientConnectionID` pole přístup do dat trasování, pokud potřebujete další pomoc diagnostiky ovladače klienta.  
  
 Můžete získat klienta ID připojení prostřednictvím kódu programu pomocí `SqlConnection.ClientConnectionID` vlastnost.  
  
 `ClientConnectionID` Je k dispozici pro <xref:System.Data.SqlClient.SqlConnection> objekt, který úspěšně naváže připojení. Pokud se nezdaří pokus o připojení, `ClientConnectionID` mohou být k dispozici prostřednictvím `SqlException.ToString`.  
  
 ADO.NET rovněž odesílá ID aktivity specifické pro vlákno Pokud jsou spuštěné relace s povolenou možností TRACK_CAUSAILITY ID aktivity zachytí ve relace rozšířených událostí. Pro problémy s výkonem s aktivním připojení, můžete získat ID aktivity trasování přístup dat klienta (`ActivityID` pole) a poté vyhledejte ID aktivity ve výstupu rozšířené události. ID aktivity v rozšířených událostí je 16 bajtů GUID (není stejný jako identifikátor GUID pro ID připojení klienta), do spolu s čtyř bajtů pořadové číslo. Pořadové číslo představuje pořadí žádost v rámci vlákna a určuje relativní řazení batch a příkazy RPC pro vlákno. `ActivityID` Je aktuálně volitelně odeslán pro batch příkazů jazyka SQL a žádosti RPC při zapnutém trasování přístup dat na a 18 bit ve službě data access trasování word konfigurace je zapnutý.  
  
 Tady je ukázka, která používá [!INCLUDE[tsql](../../../../includes/tsql-md.md)] zahájíte relaci rozšířených událostí, která se uloží na cyklické vyrovnávací paměti a budou si poznamenejte ID aktivity odeslaných z klienta na RPC a dávkové operace.  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
```  
  
## <a name="see-also"></a>Viz také  
 [Trasování sítě v rozhraní .NET Framework](../../../../docs/framework/network-programming/network-tracing.md)  
 [Trasování a instrumentace aplikací](../../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
