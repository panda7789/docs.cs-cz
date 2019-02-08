---
title: Zprostředkovatelé dat .NET framework
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
ms.openlocfilehash: c4b656d1ee7edcdc7e0e5cd41f7d57266ad5ad26
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828355"
---
# <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET framework
A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatel dat slouží k připojení k databázi, provádění příkazů a načíst výsledky. Tyto výsledky se buď zpracovávají přímo, umístí do <xref:System.Data.DataSet> aby bylo možné vystavit uživateli podle potřeby, kombinované s daty z více zdrojů nebo vzdálený mezi vrstvami. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatelé dat jsou zjednodušené, vytvoření minimální vrstvy mezi zdrojem dat a kódu, aniž byste museli obětovat funkčnost zvýšit výkon.  
  
 V následující tabulce jsou uvedeny zprostředkovatele dat, které jsou součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat|Popis|  
|-------------------------------------------------------------------------------|-----------------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro SQL Server|Poskytuje přístup k datům pro Microsoft SQL Server. Používá <xref:System.Data.SqlClient> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro OLE DB|Pro zdroje dat vystavena s použitím technologie OLE DB. Používá <xref:System.Data.OleDb> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro ODBC|Pro zdroje dat vystavena s použitím ODBC. Používá <xref:System.Data.Odbc> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro Oracle|Pro Oracle datového zdroje. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle podporuje software klienta Oracle version 8.1.7 a novější a používá <xref:System.Data.OracleClient> oboru názvů.|  
|Zprostředkovatel EntityClient|Poskytuje přístup k datům pro Entity Data Model (EDM) aplikace. Používá <xref:System.Data.EntityClient> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro SQL Server Compact 4.0.|Poskytuje přístup k datům pro Microsoft SQL Server Compact 4.0. Používá [System.Data.SqlServerCe](https://docs.microsoft.com/previous-versions/sql/compact/sql-server-compact-4.0/ec4st0e3(v=vs.100)) oboru názvů.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Základní objekty zprostředkovatele dat .NET Framework  
 Následující tabulka uvádí čtyři základní objekty, které tvoří [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Connection`|Naváže připojení ke konkrétnímu zdroji dat. Základní třída pro všechny `Connection` objekty je <xref:System.Data.Common.DbConnection> třídy.|  
|`Command`|Provede příkaz proti datovému zdroji. Zpřístupňuje `Parameters` a můžete spustit v oboru `Transaction` z `Connection`. Základní třída pro všechny `Command` objekty je <xref:System.Data.Common.DbCommand> třídy.|  
|`DataReader`|Ze zdroje dat čte pouze vpřed, jen pro čtení datový proud s daty. Základní třída pro všechny `DataReader` objekty je <xref:System.Data.Common.DbDataReader> třídy.|  
|`DataAdapter`|Naplní `DataSet` a překládá se aktualizace se zdrojem dat. Základní třída pro všechny `DataAdapter` objekty je <xref:System.Data.Common.DbDataAdapter> třídy.|  
  
 Kromě základních tříd uvedených v tabulce výše v tomto dokumentu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatel dat také obsahuje tříd uvedených v následující tabulce.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Transaction`|Příkazy v transakcích ve zdroji dat využívá. Základní třída pro všechny `Transaction` objekty je <xref:System.Data.Common.DbTransaction> třídy. ADO.NET také poskytuje podporu pro transakce pomocí třídy v <xref:System.Transactions> oboru názvů.|  
|`CommandBuilder`|Pomocný objekt, který automaticky generuje příkaz Vlastnosti `DataAdapter` nebo informace o parametrech z uložené procedury je odvozen a naplní `Parameters` kolekce `Command` objektu. Základní třída pro všechny `CommandBuilder` objekty je <xref:System.Data.Common.DbCommandBuilder> třídy.|  
|`ConnectionStringBuilder`|Pomocný objekt, který poskytuje jednoduchý způsob, jak vytvářet a spravovat obsah připojovací řetězec používaný `Connection` objekty. Základní třída pro všechny `ConnectionStringBuilder` objekty je <xref:System.Data.Common.DbConnectionStringBuilder> třídy.|  
|`Parameter`|Definuje vstupní, výstupní a návratovou hodnotu parametrů pro příkazy a uložené procedury. Základní třída pro všechny `Parameter` objekty je <xref:System.Data.Common.DbParameter> třídy.|  
|`Exception`|Vrátí, když dojde k chybě ve zdroji dat. Pro klienta, došlo k chybě [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] throw zprostředkovatelé dat [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] výjimky. Základní třída pro všechny `Exception` objekty je <xref:System.Data.Common.DbException> třídy.|  
|`Error`|Poskytuje informace z upozornění a chyby vrácené zdroje dat.|  
|`ClientPermission`|K dispozici pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] atributy zabezpečení přístupu kódu dat zprostředkovatele. Základní třída pro všechny `ClientPermission` objekty je <xref:System.Data.Common.DBDataPermission> třídy.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>Zprostředkovatel dat .NET framework pro SQL Server (SqlClient)  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (SqlClient) používá vlastní protokol pro komunikaci se serverem SQL. Je nenáročná a provádí dobrých výsledků, protože je optimalizována pro přístup k systému SQL Server přímo bez přidání vrstvu pro OLE DB nebo připojení ODBC (Open Database). Na následujícím obrázku uvádí vedle sebe [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Komunikuje se ke zdroji dat OLE DB prostřednictvím obě služby technologie OLE DB komponenty, které poskytuje sdružování připojení a transakce služeb a zprostředkovateli OLE DB pro zdroj dat poskytovatele dat pro OLE DB.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro ODBC má podobnou architekturu pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatel dat pro OLE DB; například zavolá komponentu služby ODBC.  
  
 ![Zprostředkovatelé dat](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porovnání zprostředkovatele dat .NET Framework pro SQL Server a zprostředkovatele dat .NET Framework pro OLE DB  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server třídy se nacházejí v <xref:System.Data.SqlClient> oboru názvů.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server podporuje místní a distribuované transakce. Pro distribuované transakce [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti o transakci ze Windows součásti služby nebo <xref:System.Transactions>. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.SqlClient` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>Zprostředkovatel dat .NET framework pro OLE DB  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB (OleDb) využívá nativní OLE DB pomocí zprostředkovatele komunikace s objekty COM k zajištění přístupu k datům. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB podporuje místní a distribuované transakce. Pro distribuované transakce [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti o transakci ze Windows součásti služby. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny zprostředkovatelů, které byly testovány pomocí [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Ovladač|Poskytovatel|  
|------------|--------------|  
|SQLOLEDB|Zprostředkovatel Microsoft OLE DB pro SQL Server|  
|MSDAORA|Zprostředkovatel Microsoft OLE DB pro Oracle|  
|Microsoft.Jet.OLEDB.4.0|Zprostředkovatel OLE DB pro Microsoft Jet|  
  
> [!NOTE]
>  Pomocí databáze aplikace Access (Jet) jako zdroj dat pro vícevláknové aplikace, jako například [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikací, se nedoporučuje. Pokud musíte použít Jet jako zdroj dat pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, pamatujte, že [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikací, připojení k databázi aplikace Access můžou mít problémy s připojením.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB nepodporuje rozhraní OLE DB verze 2.5. Zprostředkovatelé technologie OLE DB, které vyžadují podporu pro OLE DB 2.5 rozhraní se nebude fungovat správně s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB. To zahrnuje zprostředkovatel Microsoft OLE DB pro Exchange a zprostředkovatele Microsoft OLE DB pro publikování na Internetu.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB nefunguje pro zprostředkovatele OLE DB pro rozhraní ODBC (MSDASQL). Pro přístup k pomocí zdroje dat ODBC [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], použijte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat OLE DB tříd jsou umístěny v <xref:System.Data.OleDb> oboru názvů. Následující příklad kódu ukazuje, jak zahrnout `System.Data.OleDb` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET framework pro ODBC  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro ODBC (Odbc) využívá nativní správce ovladačů ODBC (DM) k zajištění přístupu k datům. Zprostředkovatel dat rozhraní ODBC podporuje místní a distribuované transakce. Pro distribuované transakce poskytovatel dat rozhraní ODBC, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti o transakci ze Windows součásti služby. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny testovat pomocí ovladače ODBC [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Ovladač|  
|------------|  
|SQL Server|  
|Ovladač Microsoft ODBC pro Oracle|  
|Ovladače Microsoft Access (*.mdb)|  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro ODBC – třídy se nacházejí v <xref:System.Data.Odbc> oboru názvů.  
  
 Následující příklad kódu ukazuje, jak zahrnout `System.Data.Odbc` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro ODBC vyžaduje součásti MDAC 2.6 nebo novější, a je doporučena MDAC 2.8 SP1. MDAC 2.8 SP1 si můžete stáhnout [středisko pro vývojáře úložiště a přístup k datům](https://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET framework pro Oracle  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Umožňuje přístup k datům pro Oracle zdrojům dat prostřednictvím připojení klientský software Oracle Data Provider pro Oracle (OracleClient). Zprostředkovatel dat podporuje verzi klientského softwaru Oracle 8.1.7 nebo vyšší verze. Zprostředkovatel dat podporuje místní a distribuované transakce. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Před připojením ke zdroji dat Oracle Data Provider pro Oracle vyžaduje klientský software Oracle (verze 8.1.7 nebo vyšší verze) v systému.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro Oracle třídy se nacházejí v <xref:System.Data.OracleClient> obor názvů a jsou obsaženy v `System.Data.OracleClient.dll` sestavení. Je třeba odkazovat i `System.Data.dll` a `System.Data.OracleClient.dll` Pokud kompilujete aplikace, která používá poskytovatele dat.  
  
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
 V závislosti na zdroji návrhu a data pro vaši aplikaci podle vaší volby [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat může zlepšit výkon, možnosti a integrita vaší aplikace. Následující tabulka popisuje výhody a omezení jednotlivých [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb.  
  
|Poskytovatel|Poznámky|  
|--------------|-----------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro SQL Server|Doporučuje se pro aplikace střední vrstvy, které používají Microsoft SQL Server.<br /><br /> Doporučuje se pro jednovrstvou aplikace, které používají Microsoft Database Engine (MSDE) nebo SQL Server.<br /><br /> Doporučuje namísto použití zprostředkovatele OLE DB pro SQL Server (SQLOLEDB) s používat [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro OLE DB|Pro SQL Server [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server se doporučuje namísto tohoto zprostředkovatele.<br /><br /> Doporučuje se pro jednovrstvou aplikace, které používají databáze aplikace Microsoft Access. Použití databáze aplikace Access pro aplikace střední vrstvy se nedoporučuje.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro ODBC|Doporučuje se pro střední a jedné vrstvy aplikace, které používají zdroje dat ODBC.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro Oracle|Doporučuje se pro střední a jedné vrstvy aplikace, které používají Oracle datového zdroje.|  
  
## <a name="entityclient-provider"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient se používá pro přístup k datům na základě na Entity Data Model (EDM). Na rozdíl od jiných rozhraní .NET Framework data zprostředkovatele nelze pracovat přímo se zdrojem dat. Místo toho používá Entity SQL ke komunikaci se příslušný prostředkovatel data. Další informace najdete v tématu [zprostředkovatel EntityClient a Entity SQL](https://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
## <a name="see-also"></a>Viz také:
- [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
