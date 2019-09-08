---
title: Novinky v ADO.NET
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 0a02ca3885524c5fcf8def603acdce33a972d283
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791261"
---
# <a name="whats-new-in-adonet"></a>Novinky v ADO.NET

V .NET Framework 4,5 jsou v ADO.NET nové následující funkce.

## <a name="sqlclient-data-provider"></a>Zprostředkovatel dat SqlClient

V .NET Framework Zprostředkovatel dat pro SQL Server v .NET Framework 4,5 jsou tyto nové funkce:

- Klíčová slova připojovacího řetězce atributu ConnectRetryCount a<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>atributu ConnectRetryInterval () umožňují řídit funkci odolnosti připojení nečinné.

- Podpora streamování z SQL Server do aplikace podporuje scénáře, kdy data na serveru nejsou strukturovaná.  Další informace najdete v tématu [Podpora pro streamování SqlClient](sqlclient-streaming-support.md) .

- Byla přidána podpora pro asynchronní programování.  Další informace najdete v tématu [asynchronní programování](asynchronous-programming.md) .

- V protokolu rozšířených událostí se teď budou protokolovat chyby připojení. Další informace najdete v tématu [trasování dat v ADO.NET](data-tracing.md).

- SqlClient teď podporuje vysokou dostupnost SQL Server, funkce zotavení po havárii, AlwaysOn. Další informace najdete v tématu [Podpora společnosti SqlClient pro vysokou dostupnost a zotavení po havárii](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Heslo lze předat jako <xref:System.Security.SecureString> při použití SQL Server ověřování. Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlCredential>.

- Pokud `TrustServerCertificate` je hodnota false `Encrypt` a má hodnotu true, název serveru (nebo IP adresa) v SQL Server certifikát SSL musí přesně odpovídat názvu serveru (nebo IP adrese) zadané v připojovacím řetězci. V opačném případě se pokus o připojení nezdaří. Další informace najdete v popisu `Encrypt` možnosti připojení v <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>tématu.

  Pokud tato změna způsobí, že existující aplikace už nebude připojená, můžete aplikaci opravit pomocí jedné z následujících možností:

  - Vydejte certifikát, který určuje krátký název v poli běžný název (CN) nebo alternativní název předmětu (SAN). Toto řešení bude fungovat pro zrcadlení databáze.

  - Přidejte alias, který mapuje krátký název na plně kvalifikovaný název domény.

  - V připojovacím řetězci použijte plně kvalifikovaný název domény.

- SqlClient podporuje rozšířenou ochranu. Další informace o Rozšířené ochraně najdete v tématu [připojení k databázovému stroji pomocí rozšířené ochrany](https://go.microsoft.com/fwlink/?LinkId=219978).

- SqlClient podporuje připojení k databázím LocalDB. Další informace najdete v tématu [Podpora SqlClient pro LocalDB](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;`je nová hodnota, která se má `Type System Version` předat vlastnosti připojení. Hodnota je nyní zastaralá a byla navázána `Type System Version=SQL Server 2008;`jako ekvivalentní. `Type System Version=Latest;` Další informace naleznete v tématu <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient poskytuje další podporu pro zhuštěné sloupce, funkci přidanou v SQL Server 2008. Pokud vaše aplikace již přistupuje k datům v tabulce, která používá zhuštěné sloupce, měli byste vidět zvýšení výkonu. Sloupec IsColumnSet pro <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> označuje, zda je sloupec zhuštěným sloupcem, který je členem sady sloupců. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>označuje, zda se jedná o zhuštěný sloupec (Další informace naleznete v tématu [SQL Server Collection schemas](sql-server-schema-collections.md) ). Další informace o zhuštěných sloupcích najdete v tématu [použití zhuštěných sloupců](https://go.microsoft.com/fwlink/?LinkId=224244).

- Sestavení Microsoft. SqlServer. Types. dll, které obsahuje typy prostorových dat, bylo upgradováno z verze 10,0 na verzi 11,0. Aplikace, které odkazují na toto sestavení, mohou selhat. Další informace najdete v tématu [přerušující změny funkcí databázového stroje](https://go.microsoft.com/fwlink/?LinkId=224367).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4,5 přidává rozhraní API, která umožňují nové scénáře při práci s Entity Framework 5,0. Další informace o vylepšeních a funkcích, které byly přidány do Entity Framework 5,0, naleznete v následujících tématech: [Novinky](https://go.microsoft.com/fwlink/?LinkID=251106) a [verze Entity Framework verzí a verzí](https://go.microsoft.com/fwlink/?LinkId=234899).

## <a name="see-also"></a>Viz také:

- [ADO.NET](index.md)
- [Přehled ADO.NET](ado-net-overview.md)
- [SQL Server a ADO.NET](./sql/index.md)
- [Co je nového v WCF Data Services 5,0](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
