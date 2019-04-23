---
title: Oracle a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ce92705d22edfc832e894dd2feaafcd11088bf26
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120663"
---
# <a name="oracle-and-adonet"></a>Oracle a ADO.NET
> [!NOTE]
>  Typy v <xref:System.Data.OracleClient> jsou zastaralé. Typy dál podporovat v aktuální verzi of.NET rozhraní Framework, ale bude v budoucí verzi odebrána. Společnost Microsoft doporučuje používat Zprostředkovatel Oracle třetích stran.  
  
 Tato část popisuje funkce a chování, které jsou specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje přístup k databázi Oracle pomocí Oracle volání rozhraní (OCI) podle software klienta Oracle Data Provider pro Oracle. Funkce poskytovatele dat byla navržena jako podobný [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro SQL Server, technologie OLE DB a ODBC.  
  
 Použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle, aplikace musí odkazovat <xref:System.Data.OracleClient> oboru názvů následujícím způsobem:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Také musíte zahrnout odkaz na knihovnu DLL při kompilaci kódu. Například při kompilaci programu v jazyce C#, by měl obsahovat příkazového řádku:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Požadavky na systém](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Popisuje požadavky pro použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle a popisuje celou řadu problémů mějte na paměti při jeho použití.  
  
 [Soubory Oracle BFILE](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Popisuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle BFILE.  
  
 [Soubory Oracle LOB](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Popisuje <xref:System.Data.OracleClient.OracleLob> třídu, která se používá pro práci s datovými typy Oracle LOB.  
  
 [Soubory Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Popisuje podporu pro datový typ Oracle REF CURSOR.  
  
 [Typy Oracle](../../../../docs/framework/data/adonet/oracletypes.md)  
 Popisuje, můžete použít pro práci s typy dat Oracle, včetně struktur <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString>.  
  
 [Sekvence Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Popisuje podporu pro načtení hodnoty klíče generovaný serverem sekvence Oracle.  
  
 [Mapování datových typů Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Distribuované transakce Oracle](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Popisuje zabezpečené kódování postupy při používání [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Datové sady, datové tabulky a datová zobrazení](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Popisuje, jak vytvořit a používat `DataSets`, zadaný `DataSets`, `DataTables`, a `DataViews`.  
  
 [Načítání a úpravy dat v ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Popisuje, jak pracovat s daty v ADO.NET.  
  
 [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Popisuje, jak využívat funkce, které jsou specifické pro systém SQL Server.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Popisuje obecné třídy, které umožňuje psát kód nezávislý na zprostředkovatele [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
