---
title: Novinky v ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: db903f801994202ac50ac72ad5352f20367efed7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337026"
---
# <a name="whats-new-in-adonet"></a>Novinky v ADO.NET

V .NET Framework 4,5 jsou v ADO.NET nové následující funkce.

## <a name="sqlclient-data-provider"></a>Zprostředkovatel dat SqlClient

V .NET Framework Zprostředkovatel dat pro SQL Server v .NET Framework 4,5 jsou tyto nové funkce:

- Klíčová slova připojovacího řetězce atributu ConnectRetryCount a atributu ConnectRetryInterval (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) umožňují řídit funkci odolnosti připojení nečinné.

- Podpora streamování z SQL Server do aplikace podporuje scénáře, kdy data na serveru nejsou strukturovaná.  Další informace najdete v tématu [Podpora pro streamování SqlClient](sqlclient-streaming-support.md) .

- Byla přidána podpora pro asynchronní programování.  Další informace najdete v tématu [asynchronní programování](asynchronous-programming.md) .

- V protokolu rozšířených událostí se teď budou protokolovat chyby připojení. Další informace najdete v tématu [trasování dat v ADO.NET](data-tracing.md).

- SqlClient teď podporuje vysokou dostupnost SQL Server, funkce zotavení po havárii, AlwaysOn. Další informace najdete v tématu [Podpora společnosti SqlClient pro vysokou dostupnost a zotavení po havárii](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Heslo lze předat jako <xref:System.Security.SecureString> při použití SQL Serverho ověřování. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlCredential>.

- Pokud je `TrustServerCertificate` false a `Encrypt` true, název serveru (nebo IP adresa) v certifikátu SQL Server SSL musí přesně odpovídat názvu serveru (nebo IP adrese) zadané v připojovacím řetězci. V opačném případě se pokus o připojení nezdaří. Další informace najdete v popisu možnosti připojení `Encrypt` v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Pokud tato změna způsobí, že existující aplikace už nebude připojená, můžete aplikaci opravit pomocí jedné z následujících možností:

  - Vydejte certifikát, který určuje krátký název v poli běžný název (CN) nebo alternativní název předmětu (SAN). Toto řešení bude fungovat pro zrcadlení databáze.

  - Přidejte alias, který mapuje krátký název na plně kvalifikovaný název domény.

  - V připojovacím řetězci použijte plně kvalifikovaný název domény.

- SqlClient podporuje rozšířenou ochranu. Další informace o Rozšířené ochraně najdete v tématu [připojení k databázovému stroji pomocí rozšířené ochrany](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

- SqlClient podporuje připojení k databázím LocalDB. Další informace najdete v tématu [Podpora SqlClient pro LocalDB](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` je nová hodnota, která má být předána vlastnosti připojení `Type System Version`. Hodnota `Type System Version=Latest;` je nyní zastaralá a byla rovna `Type System Version=SQL Server 2008;`. Další informace najdete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient poskytuje další podporu pro zhuštěné sloupce, funkci přidanou v SQL Server 2008. Pokud vaše aplikace již přistupuje k datům v tabulce, která používá zhuštěné sloupce, měli byste vidět zvýšení výkonu. Sloupec IsColumnSet <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> označuje, zda je sloupec zhuštěným sloupcem, který je členem sady sloupců. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> určuje, zda se jedná o zhuštěný sloupec (Další informace najdete v tématu [SQL Server kolekce schémat](sql-server-schema-collections.md) ). Další informace o zhuštěných sloupcích najdete v tématu [použití zhuštěných sloupců](/sql/relational-databases/tables/use-sparse-columns).

- Sestavení Microsoft. SqlServer. Types. dll, které obsahuje typy prostorových dat, bylo upgradováno z verze 10,0 na verzi 11,0. Aplikace, které odkazují na toto sestavení, mohou selhat. Další informace najdete v tématu [přerušující změny funkcí databázového stroje](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms143179(v=sql.110)).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4,5 přidává rozhraní API, která umožňují nové scénáře při práci s Entity Framework 5,0. Další informace o vylepšeních a funkcích přidaných do Entity Framework 5,0 naleznete v následujících tématech: [co je nového](https://docs.microsoft.com/previous-versions/gg696190(v=vs.103)) a [Entity Framework vydání a správa verzí](/ef/ef6/what-is-new/past-releases).

## <a name="see-also"></a>Viz také:

- [ADO.NET](index.md)
- [Přehled ADO.NET](ado-net-overview.md)
- [SQL Server a ADO.NET](./sql/index.md)
- [Co je nového v WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
