---
title: Oracle a ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c615c985f885734800b471ee31451cfb8a4c8500
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-and-adonet"></a>Oracle a ADO.NET
> [!NOTE]
>  Typy v <xref:System.Data.OracleClient> jsou zastaralé. Typy zůstanou podporované v aktuální verzi of.NET Framework, ale bude v budoucí verzi odebrána. Společnost Microsoft doporučuje používat zprostředkovatele Oracle třetí strany.  
  
 Tato část popisuje funkce a chování, které jsou specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro databázi Oracle poskytuje přístup k databázi Oracle pomocí Oracle volání rozhraní (OCI) podle softwarem klienta Oracle. Funkce zprostředkovatele dat je navržený jako podobná [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat pro [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], technologie OLE DB a rozhraní ODBC.  
  
 Použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle, aplikace musí odkazovat <xref:System.Data.OracleClient> oboru názvů následujícím způsobem:  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 Můžete také musí obsahovat odkaz na knihovnu DLL při kompilaci kódu. Například pokud jsou kompilace programu v C#, by měla obsahovat příkazového řádku:  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Požadavky na systém](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 Popisuje požadavky pro použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle a popisuje řadu problémů znát při používání.  
  
 [Oracle BFILEs](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 Popisuje <xref:System.Data.OracleClient.OracleBFile> třídy, která se používá pro práci s datovým typem Oracle BFILE.  
  
 [Objekty LOBs Oracle](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 Popisuje <xref:System.Data.OracleClient.OracleLob> třídy, která se používá pro práci s datovými typy obchodní Oracle.  
  
 [Kurzory REF Oracle](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 Popisuje podporu pro datový typ KURZORU REF Oracle.  
  
 [OracleTypes](../../../../docs/framework/data/adonet/oracletypes.md)  
 Popisuje struktury můžete použít pro práci s datovými typy Oracle, včetně <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString>.  
  
 [Pořadí Oracle](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 Popisuje podporu pro načítání hodnoty klíče generované serverem Oracle pořadí.  
  
 [Mapování datového typu Oracle](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 Uvádí typy dat Oracle a jejich mapování <xref:System.Data.OracleClient.OracleDataReader>.  
  
 [Oracle distribuovaných transakcí](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky využívá v existující distribuované transakce, pokud zjistí, že je aktivní transakce.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Popisuje postupy pro zabezpečené kódování při použití [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [Datové sady, DataTables a DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 Popisuje, jak vytvořit a použít `DataSets`, typu `DataSets`, `DataTables`, a `DataViews`.  
  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Popisuje, jak pracovat s daty v ADO.NET.  
  
 [SQL Server a ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 Popisuje, jak pracovat s funkcí, které jsou specifické pro [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Popisuje obecné třídy, které vám umožní psaní kódu nezávislé na zprostředkovatele [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
