---
title: Zprostředkovatelé dat .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: d343f7be3e26575ee9a1e9ccae9f17314db10ac5
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882103"
---
# <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET Framework
Zprostředkovatel dat .NET Framework se používá pro připojení k databázi, provádění příkazů a načíst výsledky. Tyto výsledky se buď zpracovávají přímo, umístí do <xref:System.Data.DataSet> aby bylo možné vystavit uživateli podle potřeby, kombinované s daty z více zdrojů nebo vzdálený mezi vrstvami. Zprostředkovatelé dat .NET framework jsou zjednodušené, vytvoření minimální vrstvy mezi zdrojem dat a kódu, aniž byste museli obětovat funkčnost zvýšit výkon.  
  
 V následující tabulce jsou uvedeny zprostředkovatele dat, které jsou zahrnuty v rozhraní .NET Framework.  
  
|Zprostředkovatel dat .NET framework|Popis|  
|-------------------------------------------------------------------------------|-----------------|  
|Zprostředkovatel dat .NET framework pro SQL Server|Poskytuje přístup k datům pro Microsoft SQL Server. Používá <xref:System.Data.SqlClient> oboru názvů.|  
|Zprostředkovatel dat .NET framework pro OLE DB|Pro zdroje dat vystavena s použitím technologie OLE DB. Používá <xref:System.Data.OleDb> oboru názvů.|  
|Zprostředkovatel dat .NET framework pro ODBC|Pro zdroje dat vystavena s použitím ODBC. Používá <xref:System.Data.Odbc> oboru názvů.|  
|Zprostředkovatel dat .NET framework pro Oracle|Pro Oracle datového zdroje. Zprostředkovatel dat .NET Framework pro Oracle podporuje software klienta Oracle version 8.1.7 a novější a používá <xref:System.Data.OracleClient> oboru názvů.|  
|Zprostředkovatel EntityClient|Poskytuje přístup k datům pro Entity Data Model (EDM) aplikace. Používá <xref:System.Data.EntityClient> oboru názvů.|  
|Zprostředkovatel dat .NET framework pro SQL Server Compact 4.0.|Poskytuje přístup k datům pro Microsoft SQL Server Compact 4.0. Používá [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) oboru názvů.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Základní objekty zprostředkovatele dat .NET Framework  
 Následující tabulka uvádí čtyři základní objekty, které společně tvoří zprostředkovatele dat .NET Framework.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Connection`|Naváže připojení ke konkrétnímu zdroji dat. Základní třída pro všechny `Connection` objekty je <xref:System.Data.Common.DbConnection> třídy.|  
|`Command`|Provede příkaz proti datovému zdroji. Zpřístupňuje `Parameters` a můžete spustit v oboru `Transaction` z `Connection`. Základní třída pro všechny `Command` objekty je <xref:System.Data.Common.DbCommand> třídy.|  
|`DataReader`|Ze zdroje dat čte pouze vpřed, jen pro čtení datový proud s daty. Základní třída pro všechny `DataReader` objekty je <xref:System.Data.Common.DbDataReader> třídy.|  
|`DataAdapter`|Naplní `DataSet` a překládá se aktualizace se zdrojem dat. Základní třída pro všechny `DataAdapter` objekty je <xref:System.Data.Common.DbDataAdapter> třídy.|  
  
 Kromě základních tříd uvedených v tabulce výše v tomto dokumentu zprostředkovatele dat .NET Framework obsahuje také tříd uvedených v následující tabulce.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Transaction`|Příkazy v transakcích ve zdroji dat využívá. Základní třída pro všechny `Transaction` objekty je <xref:System.Data.Common.DbTransaction> třídy. ADO.NET také poskytuje podporu pro transakce pomocí třídy v <xref:System.Transactions> oboru názvů.|  
|`CommandBuilder`|Pomocný objekt, který automaticky generuje příkaz Vlastnosti `DataAdapter` nebo informace o parametrech z uložené procedury je odvozen a naplní `Parameters` kolekce `Command` objektu. Základní třída pro všechny `CommandBuilder` objekty je <xref:System.Data.Common.DbCommandBuilder> třídy.|  
|`ConnectionStringBuilder`|Pomocný objekt, který poskytuje jednoduchý způsob, jak vytvářet a spravovat obsah připojovací řetězec používaný `Connection` objekty. Základní třída pro všechny `ConnectionStringBuilder` objekty je <xref:System.Data.Common.DbConnectionStringBuilder> třídy.|  
|`Parameter`|Definuje vstupní, výstupní a návratovou hodnotu parametrů pro příkazy a uložené procedury. Základní třída pro všechny `Parameter` objekty je <xref:System.Data.Common.DbParameter> třídy.|  
|`Exception`|Vrátí, když dojde k chybě ve zdroji dat. Zprostředkovatelé dat .NET Framework pro klienta došlo k chybě, vyvolat výjimky na rozhraní .NET Framework. Základní třída pro všechny `Exception` objekty je <xref:System.Data.Common.DbException> třídy.|  
|`Error`|Poskytuje informace z upozornění a chyby vrácené zdroje dat.|  
|`ClientPermission`|K dispozici pro rozhraní .NET Framework data provider atributy zabezpečení přístupu kódu. Základní třída pro všechny `ClientPermission` objekty je <xref:System.Data.Common.DBDataPermission> třídy.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>Zprostředkovatel dat .NET framework pro SQL Server (SqlClient)  
 Zprostředkovatele dat .NET Framework pro SQL Server (SqlClient) používá vlastní protokol pro komunikaci se serverem SQL. Je nenáročná a provádí dobrých výsledků, protože je optimalizována pro přístup k systému SQL Server přímo bez přidání vrstvu pro OLE DB nebo připojení ODBC (Open Database). Na následujícím obrázku se liší od zprostředkovatele dat .NET Framework pro SQL Server pomocí zprostředkovatele dat .NET Framework pro OLE DB. Komunikuje se ke zdroji dat OLE DB pomocí součásti služby technologie OLE DB, která poskytuje sdružování připojení a transakce služby a zprostředkovatele OLE DB pro zdroj dat zprostředkovatele dat .NET Framework pro OLE DB.  
  
> [!NOTE]
>  Zprostředkovatel dat .NET Framework pro ODBC má podobnou architekturu pro zprostředkovatele dat .NET Framework pro OLE DB; například volání do jako součást služby ODBC.  
  
 ![Zprostředkovatelé dat](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porovnání zprostředkovatele dat .NET Framework pro SQL Server a zprostředkovatele dat .NET Framework pro OLE DB  
  
 .NET Framework Data Provider pro SQL Server třídy se nacházejí v <xref:System.Data.SqlClient> oboru názvů.  
  
 Zprostředkovatel dat .NET Framework pro SQL Server podporuje místní a distribuované transakce. Pro distribuované transakce, zprostředkovatele dat .NET Framework pro SQL Server, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti o transakci ze Windows součásti služby nebo <xref:System.Transactions>. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.SqlClient` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>Zprostředkovatel dat .NET framework pro OLE DB  
 Zprostředkovatele dat .NET Framework pro OLE DB (OleDb) využívá nativní OLE DB pomocí zprostředkovatele komunikace s objekty COM k zajištění přístupu k datům. Zprostředkovatel dat .NET Framework pro OLE DB podporuje místní a distribuované transakce. Pro distribuované transakce zprostředkovatele dat .NET Framework pro OLE DB, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti o transakci ze Windows součásti služby. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny zprostředkovatelů, které byly testovány pomocí ADO.NET.  
  
|Ovladač|Poskytovatel|  
|------------|--------------|  
|SQLOLEDB|Zprostředkovatel Microsoft OLE DB pro SQL Server|  
|MSDAORA|Zprostředkovatel Microsoft OLE DB pro Oracle|  
|Microsoft.Jet.OLEDB.4.0|Zprostředkovatel OLE DB pro Microsoft Jet|  
  
> [!NOTE]
>  Nedoporučujeme používat databázi aplikace Access (Jet) jako zdroj dat pro vícevláknové aplikace, jako jsou třeba aplikace ASP.NET. Pokud Jet je nutné použít jako zdroj dat pro aplikaci ASP.NET, uvědomte si, že aplikace ASP.NET připojení k databázi aplikace Access můžou mít problémy s připojením.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB nepodporuje rozhraní OLE DB verze 2.5. Zprostředkovatelé technologie OLE DB, která vyžadují podporu pro rozhraní OLE DB 2.5 nebude fungovat správně s zprostředkovatele dat .NET Framework pro OLE DB. To zahrnuje zprostředkovatel Microsoft OLE DB pro Exchange a zprostředkovatele Microsoft OLE DB pro publikování na Internetu.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB nefunguje s zprostředkovatele OLE DB pro rozhraní ODBC (MSDASQL). Chcete-li přístup ke zdroji dat rozhraní ODBC použitím technologie ADO.NET, použijte zprostředkovatele dat .NET Framework pro ODBC.  
  
 Zprostředkovatel dat .NET framework pro OLE DB třídy se nacházejí v <xref:System.Data.OleDb> oboru názvů. Následující příklad kódu ukazuje, jak zahrnout `System.Data.OleDb` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET framework pro ODBC  
 Zprostředkovatele dat .NET Framework pro ODBC (Odbc) využívá nativní správce ovladačů ODBC (DM) k zajištění přístupu k datům. Zprostředkovatel dat rozhraní ODBC podporuje místní a distribuované transakce. Pro distribuované transakce poskytovatel dat rozhraní ODBC, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti o transakci ze Windows součásti služby. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny ovladače rozhraní ODBC testováním s využitím ADO.NET.  
  
|Ovladač|  
|------------|  
|SQL Server|  
|Ovladač Microsoft ODBC pro Oracle|  
|Ovladače Microsoft Access (*.mdb)|  
  
 Zprostředkovatel dat .NET framework pro ODBC – třídy se nacházejí v <xref:System.Data.Odbc> oboru názvů.  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.Odbc` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  Zprostředkovatel dat .NET Framework pro ODBC vyžaduje součásti MDAC 2.6 nebo novější, a je doporučena MDAC 2.8 SP1. MDAC 2.8 SP1 si můžete stáhnout [středisko pro vývojáře úložiště a přístup k datům](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET framework pro Oracle  
 Zprostředkovatel dat .NET Framework pro Oracle (OracleClient) umožňuje přístup k datům pro Oracle zdrojům dat prostřednictvím připojení klientský software Oracle. Zprostředkovatel dat podporuje verzi klientského softwaru Oracle 8.1.7 nebo vyšší verze. Zprostředkovatel dat podporuje místní a distribuované transakce. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Zprostředkovatel dat .NET Framework pro Oracle vyžaduje klientský software Oracle (verze 8.1.7 nebo vyšší verze) v systému, před připojením ke zdroji dat Oracle.  
  
 Zprostředkovatel dat .NET framework pro Oracle třídy se nacházejí v <xref:System.Data.OracleClient> obor názvů a jsou obsaženy v `System.Data.OracleClient.dll` sestavení. Je třeba odkazovat i `System.Data.dll` a `System.Data.OracleClient.dll` Pokud kompilujete aplikace, která používá poskytovatele dat.  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.OracleClient` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Výběr zprostředkovatele dat .NET Framework  
 V závislosti na návrhu a datového zdroje pro vaši aplikaci podle vašeho výběru zprostředkovatele dat .NET Framework může zlepšit výkon, možnosti a integrita vaší aplikace. Následující tabulka popisuje výhody a omezení pro každého poskytovatele dat .NET Framework.  
  
|Poskytovatel|Poznámky|  
|--------------|-----------|  
|Zprostředkovatel dat .NET framework pro SQL Server|Doporučuje se pro aplikace střední vrstvy, které používají Microsoft SQL Server.<br /><br /> Doporučuje se pro jednovrstvou aplikace, které používají Microsoft Database Engine (MSDE) nebo SQL Server.<br /><br /> Doporučuje namísto použití zprostředkovatele OLE DB pro SQL Server (SQLOLEDB) pomocí zprostředkovatele dat .NET Framework pro OLE DB používat.|  
|Zprostředkovatel dat .NET framework pro OLE DB|Pro SQL Server zprostředkovatele dat .NET Framework pro SQL Server doporučuje namísto tohoto zprostředkovatele.<br /><br /> Doporučuje se pro jednovrstvou aplikace, které používají databáze aplikace Microsoft Access. Použití databáze aplikace Access pro aplikace střední vrstvy se nedoporučuje.|  
|Zprostředkovatel dat .NET framework pro ODBC|Doporučuje se pro střední a jedné vrstvy aplikace, které používají zdroje dat ODBC.|  
|Zprostředkovatel dat .NET framework pro Oracle|Doporučuje se pro střední a jedné vrstvy aplikace, které používají Oracle datového zdroje.|  
  
## <a name="entityclient-provider"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient se používá pro přístup k datům na základě na Entity Data Model (EDM). Na rozdíl od jiných rozhraní .NET Framework data zprostředkovatele nelze pracovat přímo se zdrojem dat. Místo toho používá Entity SQL ke komunikaci se příslušný prostředkovatel data. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
