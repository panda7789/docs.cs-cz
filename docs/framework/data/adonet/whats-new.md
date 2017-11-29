---
title: "Jaký & č. 39; s nového v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9c0c9eb02cb95522d04765f454cd870f01a633f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="what39s-new-in-adonet"></a>Jaký & č. 39; s nového v technologii ADO.NET
Následující funkce jsou v nové [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="sqlclient-data-provider"></a>Zprostředkovatel dat SqlClient  
 Následující funkce jsou v nové [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] v [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:  
  
-   ConnectRetryCount a ConnectRetryInterval připojovací řetězec klíčová slova (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) umožňuje řídit funkci odolnosti nečinné připojení.  
  
-   Podpora z streamování [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] aplikace podporuje scénáře, kde nestrukturovaných dat na serveru.  V tématu [podpora streamování SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) Další informace.  
  
-   Byla přidána podpora pro asynchronní programování.  V tématu [asynchronní programování](../../../../docs/framework/data/adonet/asynchronous-programming.md) Další informace.  
  
-   Počet selhání připojení bude nyní přihlášeni rozšířené události protokolu. Další informace najdete v tématu [Data trasování v ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).  
  
-   SqlClient teď obsahuje podporu pro [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]na vysokou dostupnost, funkce obnovení po havárii, AlwaysOn. Další informace najdete v tématu [SqlClient podporu pro vysokou dostupnost a zotavení po havárii](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).  
  
-   Heslo lze předat jako <xref:System.Security.SecureString> při použití [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] ověřování. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlCredential>.  
  
-   Při `TrustServerCertificate` hodnotu false a `Encrypt` probíhá hodnotu PRAVDA, server název (nebo IP adresu) [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] certifikát SSL musí přesně shodovat, název serveru (nebo IP adresu) zadaný v připojovacím řetězci. Pokus o připojení, jinak nebude úspěšná. Další informace najdete v části Popis `Encrypt` možnost připojení v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
     Pokud se tato změna způsobí, že do již nemůže připojit existující aplikaci, můžete je vyřešit aplikace pomocí jednoho z následujících akcí:  
  
    -   Vydejte certifikát, který určuje krátký název v poli Common Name (CN) nebo alternativní název předmětu (SAN). Toto řešení bude fungovat pro zrcadlení databáze.  
  
    -   Přidejte alias, který mapuje krátký název plně kvalifikovaný název domény.  
  
    -   Použijte název plně kvalifikované domény v připojovacím řetězci.  
  
-   SqlClient podporuje rozšířené ochrany. Další informace o rozšířené ochrany najdete v tématu [připojení databáze modul pomocí rozšířené ochrany](http://go.microsoft.com/fwlink/?LinkId=219978).  
  
-   SqlClient podporuje připojení k databázím LocalDB. Další informace najdete v tématu [SqlClient podpora LocalDB](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).  
  
-   `Type System Version=SQL Server 2012;`je nová hodnota předat `Type System Version` vlastnost připojení. `Type System Version=Latest;` Hodnota je zastaralá a byl proveden ekvivalentní `Type System Version=SQL Server 2008;`. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
-   SqlClient poskytuje další podporu pro zhuštěné sloupce, funkce, která byla přidána v systému SQL Server 2008. Pokud vaše aplikace již získá přístup k datům v tabulce, která používá zhuštěné sloupce, měli byste vidět zvýšení výkonu. Sloupec IsColumnSet <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> značí, zda sloupec zhuštěný sloupec, který je členem skupiny sadu sloupců. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>značí, zda sloupec zhuštěný sloupec (viz [kolekcemi schémat SQL serveru](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) Další informace). Další informace o zhuštěné sloupce najdete v tématu [pomocí zhuštěné sloupce](http://go.microsoft.com/fwlink/?LinkId=224244).  
  
-   Sestavení Microsoft.SqlServer.Types.dll, který obsahuje typy prostorových dat, byl upgradován z verze 10.0 na verze 11.0. Aplikace, které odkazují na toto sestavení může selhat. Další informace najdete v tématu [nejnovějších změn databáze modul funkce](http://go.microsoft.com/fwlink/?LinkId=224367).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] Přidá rozhraní API, které umožňují nové scénáře, jako při práci s Entity Framework 5.0. Další informace o vylepšení a funkce, které byly přidány do Entity Framework 5.0 naleznete v následujících tématech: [co je nového](http://go.microsoft.com/fwlink/?LinkID=251106) a [Entity Framework verze a verze](http://go.microsoft.com/fwlink/?LinkId=234899).  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET – přehled](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [Co je nového ve službě WCF Data Services](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
