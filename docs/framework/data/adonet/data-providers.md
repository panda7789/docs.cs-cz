---
title: Zprostředkovatelé dat .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: fc338b176ee0b20800b83febe05ed2fe695cecb0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949818"
---
# <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET Framework
Zprostředkovatel dat .NET Framework slouží k připojení k databázi, provádění příkazů a načítání výsledků. Tyto výsledky jsou buď zpracovávány přímo, umístěny v <xref:System.Data.DataSet> a, aby je bylo možné zpřístupnit uživateli podle potřeby, v kombinaci s daty z více zdrojů nebo vzdáleně vydanými mezi vrstvami. Poskytovatelé dat .NET Framework jsou odlehčení a vytvářejí minimální vrstvu mezi zdrojem dat a kódem a zvyšují výkon, aniž by došlo ke ztrátě funkčnosti.  
  
 V následující tabulce jsou uvedeni poskytovatelé dat, kteří jsou součástí .NET Framework.  
  
|Poskytovatel dat .NET Framework|Popis|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET Framework Zprostředkovatel dat SQL Server|Poskytuje přístup k datům pro Microsoft SQL Server. <xref:System.Data.SqlClient> Používá obor názvů.|  
|.NET Framework Zprostředkovatel dat OLE DB|Pro zdroje dat, které jsou vystaveny pomocí OLE DB. <xref:System.Data.OleDb> Používá obor názvů.|  
|.NET Framework Zprostředkovatel dat pro rozhraní ODBC|Pro zdroje dat, které jsou vystaveny pomocí rozhraní ODBC. <xref:System.Data.Odbc> Používá obor názvů.|  
|Zprostředkovatel dat .NET Framework pro Oracle|Pro zdroje dat Oracle. Zprostředkovatel dat .NET Framework pro Oracle podporuje klientský software Oracle verze 8.1.7 a novější a používá <xref:System.Data.OracleClient> obor názvů.|  
|Zprostředkovatel EntityClient|Poskytuje přístup k datům pro aplikace model EDM (Entity Data Model) (EDM). <xref:System.Data.EntityClient> Používá obor názvů.|  
|.NET Framework Zprostředkovatel dat pro SQL Server Compact 4,0.|Poskytuje přístup k datům pro Microsoft SQL Server Compact 4,0. Používá obor názvů [System. data. SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) .|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Základní objekty zprostředkovatelů dat .NET Framework  
 Následující tabulka popisuje čtyři základní objekty, které tvoří poskytovatele dat .NET Framework.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Connection`|Naváže připojení ke konkrétnímu zdroji dat. Základní třída pro všechny `Connection` objekty <xref:System.Data.Common.DbConnection> je třída.|  
|`Command`|Spustí příkaz proti zdroji dat. Zpřístupňuje `Parameters` a může provést v oboru `Transaction` `Connection`a. Základní třída pro všechny `Command` objekty <xref:System.Data.Common.DbCommand> je třída.|  
|`DataReader`|Přečte datový proud dat jen pro čtení z datového zdroje, který je jen pro čtení. Základní třída pro všechny `DataReader` objekty <xref:System.Data.Common.DbDataReader> je třída.|  
|`DataAdapter`|Naplní `DataSet` a vyřeší aktualizace se zdrojem dat. Základní třída pro všechny `DataAdapter` objekty <xref:System.Data.Common.DbDataAdapter> je třída.|  
  
 Kromě základních tříd uvedených v tabulce výše v tomto dokumentu obsahuje poskytovatel .NET Framework dat také třídy uvedené v následující tabulce.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Transaction`|Zařadí příkazy v transakcích ve zdroji dat. Základní třída pro všechny `Transaction` objekty <xref:System.Data.Common.DbTransaction> je třída. ADO.NET také poskytuje podporu pro transakce pomocí tříd v <xref:System.Transactions> oboru názvů.|  
|`CommandBuilder`|Pomocný objekt, který automaticky generuje vlastnosti `DataAdapter` příkazu nebo odvozuje informace o parametrech z uložené procedury a naplní `Parameters` kolekci `Command` objektu. Základní třída pro všechny `CommandBuilder` objekty <xref:System.Data.Common.DbCommandBuilder> je třída.|  
|`ConnectionStringBuilder`|Pomocný objekt, který poskytuje jednoduchý způsob, jak vytvořit a spravovat obsah připojovacích řetězců používaných `Connection` objekty. Základní třída pro všechny `ConnectionStringBuilder` objekty <xref:System.Data.Common.DbConnectionStringBuilder> je třída.|  
|`Parameter`|Definuje vstupní, výstupní a návratové parametry hodnot pro příkazy a uložené procedury. Základní třída pro všechny `Parameter` objekty <xref:System.Data.Common.DbParameter> je třída.|  
|`Exception`|Vrátí se, když dojde k chybě ve zdroji dat. Aby došlo k chybě v klientovi, .NET Framework Zprostředkovatelé dat vyvolají výjimku .NET Framework. Základní třída pro všechny `Exception` objekty <xref:System.Data.Common.DbException> je třída.|  
|`Error`|Zpřístupňuje informace z upozornění nebo chyby vrácené zdrojem dat.|  
|`ClientPermission`|Zadáno pro .NET Framework atributů zabezpečení přístupu kódu poskytovatele dat. Základní třída pro všechny `ClientPermission` objekty <xref:System.Data.Common.DBDataPermission> je třída.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET Framework Zprostředkovatel dat pro SQL Server (SqlClient)  
 .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient) používá vlastní protokol ke komunikaci s SQL Server. Je odlehčená a funguje dobře, protože je optimalizovaná pro přístup k SQL Server přímo bez přidání vrstvy OLE DB nebo rozhraní ODBC (Open Database Connectivity). Následující obrázek kontrastuje .NET Framework Zprostředkovatel dat SQL Server s .NET Framework Zprostředkovatel dat pro OLE DB. Zprostředkovatel dat .NET Framework pro OLE DB komunikuje s OLE DB zdrojem dat prostřednictvím součásti OLE DB služby, která poskytuje sdružování připojení a transakční služby a poskytovatele OLE DB pro zdroj dat.  
  
> [!NOTE]
> .NET Framework Zprostředkovatel dat pro rozhraní ODBC má podobnou architekturu .NET Framework Zprostředkovatel dat pro OLE DB. například volá součást služby ODBC.  
  
 ![Poskytovatelé dat](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porovnání Zprostředkovatel dat .NET Framework pro SQL Server a .NET Framework Zprostředkovatel dat pro OLE DB  
  
 Zprostředkovatel dat .NET Framework pro třídy SQL Server jsou umístěny v <xref:System.Data.SqlClient> oboru názvů.  
  
 Zprostředkovatel dat .NET Framework pro SQL Server podporuje místní i distribuované transakce. U distribuovaných transakcí .NET Framework Zprostředkovatel dat pro SQL Server ve výchozím nastavení automaticky zařadí do transakce a získá podrobnosti transakcí ze služby komponent Windows nebo <xref:System.Transactions>. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.SqlClient` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET Framework Zprostředkovatel dat OLE DB  
 .NET Framework Zprostředkovatel dat pro OLE DB (OleDb) používá nativní OLE DB prostřednictvím zprostředkovatele komunikace s objekty COM k povolení přístupu k datům. Zprostředkovatel dat .NET Framework pro OLE DB podporuje místní i distribuované transakce. U distribuovaných transakcí .NET Framework Zprostředkovatel dat pro OLE DB ve výchozím nastavení automaticky zařadí do transakce a získá podrobnosti transakcí ze služby komponent Windows Component Services. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Následující tabulka uvádí poskytovatele, kteří byli otestováni pomocí ADO.NET.  
  
|Faktorů|Poskytovatel|  
|------------|--------------|  
|ZPROSTŘEDKOVATEL|Zprostředkovatel Microsoft OLE DB pro SQL Server|  
|MADAORA|Microsoft OLE DB Provider pro Oracle|  
|Microsoft.Jet.OLEDB.4.0|Poskytovatel OLE DB pro Microsoft Jet|  
  
> [!NOTE]
> Použití databáze Accessu jako zdroje dat pro vícevláknové aplikace, jako jsou například aplikace ASP.NET, se nedoporučuje. Pokud je nutné jako zdroj dat pro aplikaci ASP.NET použít jet, je třeba si uvědomit, že aplikace ASP.NET, které se připojují k databázi Access, můžou narazit na problémy s připojením.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB nepodporuje rozhraní OLE DB verze 2,5. Poskytovatelé OLE DB, kteří vyžadují podporu rozhraní OLE DB 2,5, nebudou správně fungovat s .NET Framework Zprostředkovatel dat pro OLE DB. To zahrnuje poskytovatele Microsoft OLE DB pro Exchange a poskytovatele Microsoft OLE DB pro publikování na internetu.  
  
 .NET Framework Zprostředkovatel dat pro OLE DB nepracuje s poskytovatelem OLE DB pro rozhraní ODBC (MSDASQL). Pro přístup ke zdroji dat ODBC pomocí ADO.NET použijte Zprostředkovatel dat .NET Framework pro ODBC.  
  
 Zprostředkovatel dat .NET Framework pro třídy OLE DB jsou umístěny v <xref:System.Data.OleDb> oboru názvů. Následující příklad kódu ukazuje, jak zahrnout `System.Data.OleDb` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET Framework Zprostředkovatel dat pro rozhraní ODBC  
 .NET Framework Zprostředkovatel dat pro rozhraní ODBC (ODBC) používá nativního správce ovladačů ODBC (DM) k povolení přístupu k datům. Zprostředkovatel dat ODBC podporuje místní i distribuované transakce. U distribuovaných transakcí poskytovatel dat ODBC ve výchozím nastavení automaticky zařadí do transakce a získá podrobnosti transakcí ze služby komponent Windows. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny ovladače rozhraní ODBC testované pomocí ADO.NET.  
  
|Faktorů|  
|------------|  
|SQL Server|  
|Microsoft ODBC pro Oracle|  
|Ovladač Microsoft Access (*. mdb)|  
  
 .NET Framework Zprostředkovatel dat pro třídy rozhraní ODBC jsou umístěny v <xref:System.Data.Odbc> oboru názvů.  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.Odbc` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
> Zprostředkovatel dat .NET Framework pro ODBC vyžaduje MDAC 2,6 nebo novější verzi a doporučuje se MDAC 2,8 SP1. MDAC 2,8 SP1 si můžete stáhnout z [centra pro vývojáře pro přístup k datům a úložiště](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET Framework pro Oracle  
 Zprostředkovatel dat .NET Framework pro Oracle (OracleClient) umožňuje přístup k datům do zdrojů dat Oracle prostřednictvím softwaru pro připojení klienta Oracle. Zprostředkovatel dat podporuje verzi klientského softwaru Oracle 8.1.7 nebo novější. Zprostředkovatel dat podporuje místní i distribuované transakce. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 .NET Framework Zprostředkovatel dat pro Oracle vyžaduje před připojením ke zdroji dat Oracle klientský software Oracle (verze 8.1.7 nebo novější) v systému.  
  
 .NET Framework Zprostředkovatel dat pro třídy Oracle jsou umístěny v <xref:System.Data.OracleClient> oboru názvů a jsou obsaženy `System.Data.OracleClient.dll` v sestavení. Při kompilaci aplikace, která `System.Data.dll` používá poskytovatele dat, je nutné, aby odkazovaly na a. `System.Data.OracleClient.dll`  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.OracleClient` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Volba .NET Framework Zprostředkovatel dat  
 V závislosti na návrhu a zdroji dat vaší aplikace může váš výběr .NET Frameworkho poskytovatele dat zlepšit výkon, schopnost a integritu vaší aplikace. Následující tabulka popisuje výhody a omezení pro každého poskytovatele .NET Framework dat.  
  
|Poskytovatel|Poznámky|  
|--------------|-----------|  
|.NET Framework Zprostředkovatel dat SQL Server|Doporučuje se pro aplikace střední vrstvy, které používají Microsoft SQL Server.<br /><br /> Doporučuje se pro vícevrstvé aplikace, které používají Microsoft Database Engine (MSDE) nebo SQL Server.<br /><br /> Doporučuje se použít poskytovatele OLE DB pro SQL Server (SQLOLEDB) s .NET Framework Zprostředkovatel dat pro OLE DB.|  
|.NET Framework Zprostředkovatel dat OLE DB|Pro SQL Server se místo tohoto poskytovatele doporučuje .NET Framework Zprostředkovatel dat pro SQL Server.<br /><br /> Doporučuje se pro vícevrstvé aplikace, které používají databáze Microsoft Access. Použití databáze Access pro aplikaci střední vrstvy se nedoporučuje.|  
|.NET Framework Zprostředkovatel dat pro rozhraní ODBC|Doporučuje se pro střední a vícevrstvé aplikace, které používají zdroje dat ODBC.|  
|Zprostředkovatel dat .NET Framework pro Oracle|Doporučuje se pro střední a vícevrstvé aplikace, které používají zdroje dat Oracle.|  
  
## <a name="entityclient-provider"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient se používá pro přístup k datům na základě model EDM (Entity Data Model) (EDM). Na rozdíl od jiných zprostředkovatelů dat .NET Framework nekomunikuje přímo se zdrojem dat. Místo toho používá Entity SQL ke komunikaci s podkladovým poskytovatelem dat. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
