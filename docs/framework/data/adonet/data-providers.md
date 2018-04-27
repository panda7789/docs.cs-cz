---
title: Zprostředkovatelé dat .NET framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 03a9fc62-2d24-491a-9fe6-d6bdb6dcb131
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 69acb7b2fe4eafcce75a7b76305fab37dbb7d2f6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="net-framework-data-providers"></a>Zprostředkovatelé dat .NET framework
A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatel dat slouží k připojení k databázi, provádění příkazů a načíst výsledky. Výsledků buď zpracování přímo, uložena v umístění <xref:System.Data.DataSet> Chcete-li zpřístupnit pro uživatele podle potřeby, kombinované s daty z více zdrojů nebo používat vzdáleně mezi vrstvami. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatelé dat jsou lightweight, vytváření minimální vrstva mezi zdroji dat a kód, zvýšení výkonu bez omezení funkčnosti.  
  
 Následující tabulka uvádí zprostředkovatele dat, které jsou součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat|Popis|  
|-------------------------------------------------------------------------------|-----------------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server|Poskytuje přístup k datům pro Microsoft SQL Server. Používá <xref:System.Data.SqlClient> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro OLE DB|Pro zdroje dat vystavené pomocí technologie OLE DB. Používá <xref:System.Data.OleDb> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro rozhraní ODBC|Pro zdroje dat vystavené pomocí rozhraní ODBC. Používá <xref:System.Data.Odbc> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro Oracle|Zdroje dat Oracle. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro databázi Oracle podporuje Oracle verze klientského softwaru 8.1.7 a novější a používá <xref:System.Data.OracleClient> oboru názvů.|  
|Zprostředkovatel EntityClient|Poskytuje přístup k datům Entity Data Model (EDM) aplikace. Používá <xref:System.Data.EntityClient> oboru názvů.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server Compact 4.0.|Poskytuje přístup k datům pro Microsoft SQL Server Compact 4.0. Používá [System.Data.SqlServerCe](http://msdn.microsoft.com/library/system.data.sqlserverce.aspx) oboru názvů.|  
  
## <a name="core-objects-of-net-framework-data-providers"></a>Základní objekty zprostředkovatelé dat .NET Framework  
 Následující tabulka uvádí čtyři základní objekty, které tvoří [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Connection`|Vytvoří připojení ke zdroji dat konkrétní. Základní třída pro všechny `Connection` je objekty <xref:System.Data.Common.DbConnection> třídy.|  
|`Command`|Spustí příkaz zdroj dat a. Zpřístupní `Parameters` a můžete provést v rámci oboru `Transaction` z `Connection`. Základní třída pro všechny `Command` je objekty <xref:System.Data.Common.DbCommand> třídy.|  
|`DataReader`|Přečte datový proud dopředné, jen pro čtení z datového zdroje. Základní třída pro všechny `DataReader` je objekty <xref:System.Data.Common.DbDataReader> třídy.|  
|`DataAdapter`|Naplní `DataSet` a přeloží aktualizace se zdrojem dat. Základní třída pro všechny `DataAdapter` je objekty <xref:System.Data.Common.DbDataAdapter> třídy.|  
  
 Kromě základní třídy uvedené v tabulce výše v tomto dokumentu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat také obsahuje tříd uvedených v následující tabulce.  
  
|Objekt|Popis|  
|------------|-----------------|  
|`Transaction`|Příkazy v transakce ve zdroji dat využívá. Základní třída pro všechny `Transaction` je objekty <xref:System.Data.Common.DbTransaction> třídy. ADO.NET taky poskytuje podporu pro transakce pomocí třídy v <xref:System.Transactions> oboru názvů.|  
|`CommandBuilder`|Pomocný objekt, který automaticky vygeneruje příkaz Vlastnosti `DataAdapter` nebo odvozuje informace o parametrech z uložené procedury a naplní `Parameters` kolekce `Command` objektu. Základní třída pro všechny `CommandBuilder` je objekty <xref:System.Data.Common.DbCommandBuilder> třídy.|  
|`ConnectionStringBuilder`|Pomocný objekt, který poskytuje jednoduchý způsob, jak vytvořit a spravovat obsah připojovacích řetězců používaných `Connection` objekty. Základní třída pro všechny `ConnectionStringBuilder` je objekty <xref:System.Data.Common.DbConnectionStringBuilder> třídy.|  
|`Parameter`|Definuje vstupní, výstupní a parametry návratovou hodnotu pro příkazy a uložené procedury. Základní třída pro všechny `Parameter` je objekty <xref:System.Data.Common.DbParameter> třídy.|  
|`Exception`|Vrátit, pokud je ve zdroji dat došlo k chybě. Pro k chybě na straně klienta [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] throw zprostředkovatelé dat [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] výjimka. Základní třída pro všechny `Exception` je objekty <xref:System.Data.Common.DbException> třídy.|  
|`Error`|Zveřejňuje informace o upozornění nebo chyby vrácené zdroj dat.|  
|`ClientPermission`|Zadaná pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] atributy zabezpečení přístupu kódu dat zprostředkovatele. Základní třída pro všechny `ClientPermission` je objekty <xref:System.Data.Common.DBDataPermission> třídy.|  
  
## <a name="net-framework-data-provider-for-sql-server-sqlclient"></a>Zprostředkovatel dat .NET framework pro SQL Server (SqlClient)  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server (SqlClient) používá vlastní protokol pro komunikaci se serverem SQL. Je jednoduché a provede dobře, protože je optimalizována pro přístup k systému SQL Server přímo bez přidáním úrovně technologie OLE DB nebo připojení ODBC (Open Database). Následující obrázku uvádí vedle sebe [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Komunikuje se zdroji dat OLE DB pomocí obou OLE DB služby komponentu, která poskytuje sdružování připojení a transakce služeb a zprostředkovateli OLE DB pro zdroj dat zprostředkovatele dat pro OLE DB.  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro ODBC má podobnou architekturu k [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB; například volání do komponentu služby ODBC.  
  
 ![Zprostředkovatelé dat](../../../../docs/framework/data/adonet/media/netdataproviders-bpuedev11.gif "NETDataProviders_bpuedev11")  
Porovnání zprostředkovatele dat .NET Framework pro SQL Server a zprostředkovatele dat .NET Framework pro OLE DB  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro třídy SQL serveru se nacházejí v <xref:System.Data.SqlClient> oboru názvů.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server podporuje místní a distribuované transakce. Pro distribuované transakce [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti transakce ze služeb součásti systému Windows nebo <xref:System.Transactions>. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 Následující příklad kódu ukazuje, jak se zahrnuje `System.Data.SqlClient` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.SqlClient  
```  
  
```csharp  
using System.Data.SqlClient;  
```  
  
## <a name="net-framework-data-provider-for-ole-db"></a>Zprostředkovatel dat .NET framework pro OLE DB  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB (OleDb) použije nativní OLE DB pomocí zprostředkovatele komunikace s objekty COM povolit přístup k datům. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB podporuje místní a distribuované transakce. Pro distribuované transakce [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB, ve výchozím nastavení, automaticky využívá v transakci a získá podrobnosti transakce ze služeb součásti systému Windows. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny zprostředkovatele, které byly testovány s [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Ovladače|Zprostředkovatel|  
|------------|--------------|  
|ZPROSTŘEDKOVATEL SQLOLEDB|Zprostředkovatel Microsoft OLE DB pro SQL Server|  
|MSDAORA|Zprostředkovatel Microsoft OLE DB pro Oracle|  
|Microsoft.Jet.OLEDB.4.0|Zprostředkovatel OLE DB pro Microsoft Jet|  
  
> [!NOTE]
>  Používání databáze Access (Jet) jako zdroj dat pro vícevláknové aplikace, jako například [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, se nedoporučuje. Pokud musíte použít Jet jako zdroj dat pro [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace, pamatujte si, že [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] připojení k databázi aplikace Access aplikace se můžete setkat potíže s připojením.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB nepodporuje verze 2.5 rozhraní OLE DB. OLE DB – zprostředkovatelé vyžadující podporu pro OLE DB 2.5 rozhraní bude fungovat správně s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB. To zahrnuje zprostředkovatel Microsoft OLE DB pro Exchange a zprostředkovatele Microsoft OLE DB pro publikování na Internetu.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro OLE DB pomocí zprostředkovatele OLE DB pro ODBC (MSDASQL) nefunguje. Pro přístup rozhraní ODBC zdroje dat pomocí [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], použijte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro ODBC.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro OLE DB třídy se nacházejí v <xref:System.Data.OleDb> oboru názvů. Následující příklad kódu ukazuje, jak se zahrnuje `System.Data.OleDb` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.OleDb  
```  
  
```csharp  
using System.Data.OleDb;  
```  
  
## <a name="net-framework-data-provider-for-odbc"></a>Zprostředkovatel dat .NET framework pro rozhraní ODBC  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro rozhraní ODBC (Odbc) použije nativní správce ovladačů ODBC (DM) povolit přístup k datům. Zprostředkovatel dat rozhraní ODBC podporuje místní a distribuované transakce. Zprostředkovatel dat rozhraní ODBC, ve výchozím nastavení, pro distribuované transakce, automaticky využívá v transakci a získá podrobnosti transakce ze služeb součásti systému Windows. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 V následující tabulce jsou uvedeny ovladače ODBC testovány s [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
|Ovladače|  
|------------|  
|SQL Server|  
|Microsoft ODBC pro Oracle|  
|Ovladače Microsoft Access (*.mdb)|  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro ODBC – třídy se nacházejí v <xref:System.Data.Odbc> oboru názvů.  
  
 Následující příklad kódu ukazuje, jak se zahrnuje `System.Data.Odbc` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data.Odbc  
```  
  
```csharp  
using System.Data.Odbc;  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro ODBC vyžaduje MDAC 2.6 nebo novější, a doporučuje se MDAC 2.8 SP1. Rozhraní MDAC 2.8 SP1 si můžete stáhnout [přístup k datům a středisku pro vývojáře úložiště](http://go.microsoft.com/fwlink/?linkid=4173).  
  
## <a name="net-framework-data-provider-for-oracle"></a>Zprostředkovatel dat .NET framework pro Oracle  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro databázi Oracle (OracleClient) umožňuje přístup k datům pro zdroje dat Oracle prostřednictvím softwaru připojení klienta Oracle. Zprostředkovatel dat podporuje verzi softwaru klienta Oracle 8.1.7 nebo novější. Zprostředkovatel dat podporuje místní a distribuované transakce. Další informace najdete v tématu [transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md).  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro databázi Oracle před připojením ke zdroji dat Oracle vyžaduje klientský software Oracle (verze 8.1.7 nebo novější verze) v systému.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro Oracle třídy se nacházejí v <xref:System.Data.OracleClient> obor názvů a jsou součástí `System.Data.OracleClient.dll` sestavení. Obě musíte odkázat `System.Data.dll` a `System.Data.OracleClient.dll` při sestavování aplikaci, která používá zprostředkovatele dat.  
  
 Následující příklad kódu ukazuje, jak se zahrnuje `System.Data.OracleClient` oboru názvů ve svých aplikacích.  
  
```vb  
Imports System.Data  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data;  
using System.Data.OracleClient;  
```  
  
## <a name="choosing-a-net-framework-data-provider"></a>Výběr zprostředkovatele dat .NET Framework  
 V závislosti na zdroji návrhu a dat pro vaši aplikaci vaši volbu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat může zvýšit výkon, funkce a integrity vaší aplikace. Následující tabulka popisuje výhody a omezení každé [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele.  
  
|Zprostředkovatel|Poznámky|  
|--------------|-----------|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server|Doporučuje pro aplikace střední vrstvy, které používají Microsoft SQL Server.<br /><br /> Doporučuje pro Jednoúrovňové aplikace, které používají Microsoft Database Engine (MSDE) nebo SQL Server.<br /><br /> Doporučuje namísto použití zprostředkovatele OLE DB pro SQL Server (SQLOLEDB) s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro OLE DB.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatel dat pro OLE DB|Pro systém SQL Server [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro SQL Server se doporučuje namísto tohoto zprostředkovatele.<br /><br /> Doporučuje Jednoúrovňové aplikace, které používají databáze aplikace Microsoft Access. Použití databáze aplikace Access pro aplikaci střední vrstvy se nedoporučuje.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] "Zprostředkovatel dat pro rozhraní ODBC|Doporučuje pro střední a Jednoúrovňové aplikace, které používají zdroje dat ODBC.|  
|[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] "Zprostředkovatele dat pro databázi Oracle|Doporučuje pro střední a Jednoúrovňové aplikace, které používají zdroje dat Oracle.|  
  
## <a name="entityclient-provider"></a>Zprostředkovatel EntityClient  
 Zprostředkovatel EntityClient se používá pro přístup k datům na základě na Entity Data Model (EDM). Na rozdíl od jiných rozhraní .NET Framework dat zprostředkovatele není komunikovat přímo se zdrojem dat. Místo toho ke komunikaci s základní poskytovatel dat používá Entity SQL. Další informace najdete v tématu [EntityClient a Entity SQL](http://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
## <a name="see-also"></a>Viz také  
 [Přehled ADO.NET](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
