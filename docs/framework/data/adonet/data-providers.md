---
title: Zprostředkovatelé dat .NET Framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: 2c986aab33f2c4dcefb5924ea61e8b9f6b3c50a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347813"
---
# <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET Framework
Zprostředkovatel dat .NET Framework slouží k připojení k databázi, provádění příkazů a načítání výsledků. Tyto výsledky jsou buď zpracovávány přímo, umístěny v <xref:System.Data.DataSet>, aby je bylo možné zpřístupnit uživateli podle potřeby, v kombinaci s daty z více zdrojů nebo vzdáleně vydanými mezi vrstvami. Poskytovatelé dat .NET Framework jsou odlehčení a vytvářejí minimální vrstvu mezi zdrojem dat a kódem a zvyšují výkon, aniž by došlo ke ztrátě funkčnosti.  
  
 V následující tabulce jsou uvedeni poskytovatelé dat, kteří jsou součástí .NET Framework.  
  
|Poskytovatel dat .NET Framework|Popis|  
|-------------------------------------------------------------------------------|-----------------|  
|.NET Framework Zprostředkovatel dat SQL Server|Poskytuje přístup k datům pro Microsoft SQL Server. Používá <xref:System.Data.SqlClient> obor názvů.|  
|.NET Framework Zprostředkovatel dat OLE DB|Pro zdroje dat, které jsou vystaveny pomocí OLE DB. Používá <xref:System.Data.OleDb> obor názvů.|  
|.NET Framework Zprostředkovatel dat pro rozhraní ODBC|Pro zdroje dat, které jsou vystaveny pomocí rozhraní ODBC. Používá <xref:System.Data.Odbc> obor názvů.|  
|Zprostředkovatel dat .NET Framework pro Oracle|Pro zdroje dat Oracle. Zprostředkovatel dat .NET Framework pro Oracle podporuje klientský software Oracle verze 8.1.7 a novější a používá obor názvů <xref:System.Data.OracleClient>.|  
|Zprostředkovatel EntityClient|Poskytuje přístup k datům pro aplikace model EDM (Entity Data Model) (EDM). Používá <xref:System.Data.EntityClient> obor názvů.|  
|.NET Framework Zprostředkovatel dat pro SQL Server Compact 4,0.|Poskytuje přístup k datům pro Microsoft SQL Server Compact 4,0. Používá obor názvů [System. data. SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) .|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Základní objekty zprostředkovatelů dat .NET Framework  
 Následující tabulka popisuje čtyři základní objekty, které tvoří poskytovatele dat .NET Framework.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Connection`|Naváže připojení ke konkrétnímu zdroji dat. Základní třída pro všechny objekty `Connection` je třída <xref:System.Data.Common.DbConnection>.|  
|`Command`|Spustí příkaz proti zdroji dat. Zpřístupňuje `Parameters` a může provést v rozsahu `Transaction` z `Connection`. Základní třída pro všechny objekty `Command` je třída <xref:System.Data.Common.DbCommand>.|  
|`DataReader`|Přečte datový proud dat jen pro čtení z datového zdroje, který je jen pro čtení. Základní třída pro všechny objekty `DataReader` je třída <xref:System.Data.Common.DbDataReader>.|  
|`DataAdapter`|Naplní `DataSet` a vyřeší aktualizace se zdrojem dat. Základní třída pro všechny objekty `DataAdapter` je třída <xref:System.Data.Common.DbDataAdapter>.|  
  
 Kromě základních tříd uvedených v tabulce výše v tomto dokumentu obsahuje poskytovatel .NET Framework dat také třídy uvedené v následující tabulce.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Transaction`|Zařadí příkazy v transakcích ve zdroji dat. Základní třída pro všechny objekty `Transaction` je třída <xref:System.Data.Common.DbTransaction>. ADO.NET také poskytuje podporu pro transakce pomocí tříd v oboru názvů <xref:System.Transactions>.|  
|`CommandBuilder`|Pomocný objekt, který automaticky generuje vlastnosti příkazu `DataAdapter` nebo odvozuje informace o parametrech z uložené procedury a naplní kolekci `Parameters` objektu `Command`. Základní třída pro všechny objekty `CommandBuilder` je třída <xref:System.Data.Common.DbCommandBuilder>.|  
|`ConnectionStringBuilder`|Pomocný objekt, který poskytuje jednoduchý způsob, jak vytvořit a spravovat obsah připojovacích řetězců používaných objekty `Connection`. Základní třída pro všechny objekty `ConnectionStringBuilder` je třída <xref:System.Data.Common.DbConnectionStringBuilder>.|  
|`Parameter`|Definuje vstupní, výstupní a návratové parametry hodnot pro příkazy a uložené procedury. Základní třída pro všechny objekty `Parameter` je třída <xref:System.Data.Common.DbParameter>.|  
|`Exception`|Vrátí se, když dojde k chybě ve zdroji dat. Aby došlo k chybě v klientovi, .NET Framework Zprostředkovatelé dat vyvolají výjimku .NET Framework. Základní třída pro všechny objekty `Exception` je třída <xref:System.Data.Common.DbException>.|  
|`Error`|Zpřístupňuje informace z upozornění nebo chyby vrácené zdrojem dat.|  
|`ClientPermission`|Zadáno pro .NET Framework atributů zabezpečení přístupu kódu poskytovatele dat. Základní třída pro všechny objekty `ClientPermission` je třída <xref:System.Data.Common.DBDataPermission>.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>.NET Framework Zprostředkovatel dat pro SQL Server (SqlClient)  
 .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient) používá vlastní protokol ke komunikaci s SQL Server. Je odlehčená a funguje dobře, protože je optimalizovaná pro přístup k SQL Server přímo bez přidání vrstvy OLE DB nebo rozhraní ODBC (Open Database Connectivity). Následující obrázek kontrastuje .NET Framework Zprostředkovatel dat SQL Server s .NET Framework Zprostředkovatel dat pro OLE DB. Zprostředkovatel dat .NET Framework pro OLE DB komunikuje s OLE DB zdrojem dat prostřednictvím součásti OLE DB služby, která poskytuje sdružování připojení a transakční služby a poskytovatele OLE DB pro zdroj dat.  
  
> [!NOTE]
> .NET Framework Zprostředkovatel dat pro rozhraní ODBC má podobnou architekturu .NET Framework Zprostředkovatel dat pro OLE DB. například volá součást služby ODBC.  
  
 ![Poskytovatelé dat](./media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porovnání Zprostředkovatel dat .NET Framework pro SQL Server a .NET Framework Zprostředkovatel dat pro OLE DB  
  
 Zprostředkovatel dat .NET Framework pro třídy SQL Server jsou umístěny v oboru názvů <xref:System.Data.SqlClient>.  
  
 Zprostředkovatel dat .NET Framework pro SQL Server podporuje místní i distribuované transakce. U distribuovaných transakcí .NET Framework SQL Server Zprostředkovatel dat ve výchozím nastavení automaticky zařadí do transakce a získá podrobnosti transakcí ze služby Windows Component Services nebo <xref:System.Transactions>. Další informace najdete v tématu [transakce a souběžnost](transactions-and-concurrency.md).  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.SqlClient` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>.NET Framework Zprostředkovatel dat OLE DB  
 .NET Framework Zprostředkovatel dat pro OLE DB (OleDb) používá nativní OLE DB prostřednictvím zprostředkovatele komunikace s objekty COM k povolení přístupu k datům. Zprostředkovatel dat .NET Framework pro OLE DB podporuje místní i distribuované transakce. U distribuovaných transakcí .NET Framework Zprostředkovatel dat pro OLE DB ve výchozím nastavení automaticky zařadí do transakce a získá podrobnosti transakcí ze služby komponent Windows Component Services. Další informace najdete v tématu [transakce a souběžnost](transactions-and-concurrency.md).  
  
 Následující tabulka uvádí poskytovatele, kteří byli otestováni pomocí ADO.NET.  
  
|kartu Ovladač|Zprostředkovatel|  
|------------|--------------|  
|Zprostředkovatel|Zprostředkovatel Microsoft OLE DB pro SQL Server|  
|MADAORA|Microsoft OLE DB Provider pro Oracle|  
|Microsoft.Jet.OLEDB.4.0|Poskytovatel OLE DB pro Microsoft Jet|  
  
> [!NOTE]
> Použití databáze Accessu jako zdroje dat pro vícevláknové aplikace, jako jsou například aplikace ASP.NET, se nedoporučuje. Pokud je nutné jako zdroj dat pro aplikaci ASP.NET použít jet, je třeba si uvědomit, že aplikace ASP.NET, které se připojují k databázi Access, můžou narazit na problémy s připojením.  
  
 Zprostředkovatel dat .NET Framework pro OLE DB nepodporuje rozhraní OLE DB verze 2,5. Poskytovatelé OLE DB, kteří vyžadují podporu rozhraní OLE DB 2,5, nebudou správně fungovat s .NET Framework Zprostředkovatel dat pro OLE DB. To zahrnuje poskytovatele Microsoft OLE DB pro Exchange a poskytovatele Microsoft OLE DB pro publikování na internetu.  
  
 .NET Framework Zprostředkovatel dat pro OLE DB nepracuje s poskytovatelem OLE DB pro rozhraní ODBC (MSDASQL). Pro přístup ke zdroji dat ODBC pomocí ADO.NET použijte Zprostředkovatel dat .NET Framework pro ODBC.  
  
 Zprostředkovatel dat .NET Framework pro třídy OLE DB jsou umístěny v oboru názvů <xref:System.Data.OleDb>. Následující příklad kódu ukazuje, jak zahrnout `System.Data.OleDb` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>.NET Framework Zprostředkovatel dat pro rozhraní ODBC  
 .NET Framework Zprostředkovatel dat pro rozhraní ODBC (ODBC) používá nativního správce ovladačů ODBC (DM) k povolení přístupu k datům. Zprostředkovatel dat ODBC podporuje místní i distribuované transakce. U distribuovaných transakcí poskytovatel dat ODBC ve výchozím nastavení automaticky zařadí do transakce a získá podrobnosti transakcí ze služby komponent Windows. Další informace najdete v tématu [transakce a souběžnost](transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny ovladače rozhraní ODBC testované pomocí ADO.NET.  
  
|kartu Ovladač|  
|------------|  
|Server SQL|  
|Microsoft ODBC pro Oracle|  
|Ovladač Microsoft Access (*. mdb)|  
  
 .NET Framework Zprostředkovatel dat pro třídy rozhraní ODBC jsou umístěny v oboru názvů <xref:System.Data.Odbc>.  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.Odbc` obor názvů do vašich aplikací.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
> Zprostředkovatel dat .NET Framework pro ODBC vyžaduje MDAC 2,6 nebo novější verzi a doporučuje se MDAC 2,8 SP1. Součásti MDAC 2,8 SP1 si můžete stáhnout z webu [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=5793).
  
## <a name="net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET Framework pro Oracle  
 Zprostředkovatel dat .NET Framework pro Oracle (OracleClient) umožňuje přístup k datům do zdrojů dat Oracle prostřednictvím softwaru pro připojení klienta Oracle. Zprostředkovatel dat podporuje verzi klientského softwaru Oracle 8.1.7 nebo novější. Zprostředkovatel dat podporuje místní i distribuované transakce. Další informace najdete v tématu [transakce a souběžnost](transactions-and-concurrency.md).  
  
 .NET Framework Zprostředkovatel dat pro Oracle vyžaduje před připojením ke zdroji dat Oracle klientský software Oracle (verze 8.1.7 nebo novější) v systému.  
  
 .NET Framework Zprostředkovatel dat pro třídy Oracle jsou umístěné v oboru názvů <xref:System.Data.OracleClient> a jsou obsaženy v sestavení `System.Data.OracleClient.dll`. Při kompilaci aplikace, která používá poskytovatele dat, je nutné na `System.Data.dll` a `System.Data.OracleClient.dll` odkazovat.  
  
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
  
|Zprostředkovatel|Poznámky|  
|--------------|-----------|  
|.NET Framework Zprostředkovatel dat SQL Server|Doporučuje se pro aplikace střední vrstvy, které používají Microsoft SQL Server.<br /><br /> Doporučuje se pro vícevrstvé aplikace, které používají Microsoft Database Engine (MSDE) nebo SQL Server.<br /><br /> Doporučuje se použít poskytovatele OLE DB pro SQL Server (SQLOLEDB) s .NET Framework Zprostředkovatel dat pro OLE DB.|  
|.NET Framework Zprostředkovatel dat OLE DB|Pro SQL Server se místo tohoto poskytovatele doporučuje .NET Framework Zprostředkovatel dat pro SQL Server.<br /><br /> Doporučuje se pro vícevrstvé aplikace, které používají databáze Microsoft Access. Použití databáze Access pro aplikaci střední vrstvy se nedoporučuje.|  
|.NET Framework Zprostředkovatel dat pro rozhraní ODBC|Doporučuje se pro střední a vícevrstvé aplikace, které používají zdroje dat ODBC.|  
|Zprostředkovatel dat .NET Framework pro Oracle|Doporučuje se pro střední a vícevrstvé aplikace, které používají zdroje dat Oracle.|  
  
## <a name="entityclient-provider"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient se používá pro přístup k datům na základě model EDM (Entity Data Model) (EDM). Na rozdíl od jiných zprostředkovatelů dat .NET Framework nekomunikuje přímo se zdrojem dat. Místo toho používá Entity SQL ke komunikaci s podkladovým poskytovatelem dat. Další informace najdete v tématu [zprostředkovatel EntityClient pro Entity Framework](./ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled ADO.NET](ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](retrieving-and-modifying-data.md)
