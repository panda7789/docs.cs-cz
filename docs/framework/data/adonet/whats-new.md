---
title: Novinky v ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 90352d3e3d52430d515460cdcc9b6d177976c0b8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191441"
---
# <a name="whats-new-in-adonet"></a>Novinky v ADO.NET
Následující funkce jsou novinkou [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="sqlclient-data-provider"></a>Zprostředkovatel dat SqlClient  
 Následující funkce jsou novinkou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:  
  
-   Atributy ConnectRetryCount a ConnectRetryInterval připojovací řetězec klíčová slova (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) můžete ovládat funkce odolnosti proti chybám nečinné připojení.  
  
-   Podpora v systému SQL Server k aplikaci streamování podporuje scénáře, ve kterém se Nestrukturovaná data na serveru.  Zobrazit [podpora streamování SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) Další informace.  
  
-   Byla přidána podpora pro asynchronní programování.  Zobrazit [Asynchronous Programming](../../../../docs/framework/data/adonet/asynchronous-programming.md) Další informace.  
  
-   Chyby připojení se teď protokolované v protokolu rozšířené události. Další informace najdete v tématu [trasování Data v ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).  
  
-   SqlClient teď obsahují podporu pro SQL Server vysokou dostupnost, funkce pro zotavení po havárii, AlwaysOn. Další informace najdete v tématu [podpora klienta SqlClient pro vysokou dostupnost, zotavení po havárii](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).  
  
-   Heslo lze předat jako <xref:System.Security.SecureString> při použití ověřování systému SQL Server. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlCredential>.  
  
-   Když `TrustServerCertificate` má hodnotu false a `Encrypt` má hodnotu true, název serveru (nebo IP adresa) v certifikátu SSL SQL serveru musí přesně odpovídat název serveru (nebo IP adresu) zadaná v připojovacím řetězci. V opačném případě se nezdaří pokus o připojení. Další informace najdete v popisu `Encrypt` možnost připojení v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
     Pokud se tato změna způsobí, že se už připojit existující aplikaci, je opravit aplikaci pomocí jednoho z následujících akcí:  
  
    -   Vydejte certifikát, který určuje krátký název do pole běžný název (CN) nebo alternativní název předmětu (SAN). Toto řešení bude fungovat na zrcadlení databáze.  
  
    -   Přidáte alias, který se mapuje plně kvalifikovaný název domény krátký název.  
  
    -   Použijte plně kvalifikovaný název domény v připojovacím řetězci.  
  
-   SqlClient podporuje rozšířenou ochranu. Další informace o rozšířené ochrany najdete v tématu [připojení k databázi modul pomocí rozšířené ochrany](https://go.microsoft.com/fwlink/?LinkId=219978).  
  
-   SqlClient podporuje připojení k databázím LocalDB. Další informace najdete v tématu [podpora klienta SqlClient pro LocalDB](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).  
  
-   `Type System Version=SQL Server 2012;` je nová hodnota pro předání `Type System Version` vlastnost připojení. `Type System Version=Latest;` Hodnota je zastaralá a má za cíl ekvivalentní `Type System Version=SQL Server 2008;`. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
-   SqlClient poskytuje další podporu pro sadu zhuštěných sloupců, funkce, která byla přidána do systému SQL Server 2008. Pokud už vaše aplikace přistupuje k datům v tabulce, která používá sadu zhuštěných sloupců, měli byste vidět zvýšení výkonu. Sloupec IsColumnSet <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> značí, zda je sloupec zhuštěný sloupec, který je členem sady sloupců. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> Určuje, zda je sloupec sadu zhuštěných sloupců (viz [kolekce schémat SQL serveru](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) Další informace). Další informace o sadu zhuštěných sloupců, naleznete v tématu [pomocí zhuštěné sloupce](https://go.microsoft.com/fwlink/?LinkId=224244).  
  
-   Sestavení Microsoft.SqlServer.Types.dll, který obsahuje typy prostorových dat byla upgradována z verze 10.0 na verze 11.0. Aplikace, které odkazují na toto sestavení může selhat. Další informace najdete v tématu [Breaking Changes funkce databázového stroje](https://go.microsoft.com/fwlink/?LinkId=224367).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] Přidá rozhraní API, která umožňují nové scénáře, jako při práci s Entity Framework 5.0. Další informace o vylepšení a funkcí, které byly přidány do Entity Framework 5.0 naleznete v následujících tématech: [Co je nového](https://go.microsoft.com/fwlink/?LinkID=251106) a [Entity Framework vydání a správa verzí](https://go.microsoft.com/fwlink/?LinkId=234899).  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [Co je nového ve službě WCF Data Services 5.0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
