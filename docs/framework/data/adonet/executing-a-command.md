---
title: "Spouštění příkazu"
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 43fb2d8e42aeae5340874ab082f33257b197eac3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="executing-a-command"></a>Spouštění příkazu
Zprostředkovatel dat .NET Framework, jednotlivých součástí rozhraní .NET Framework má svou vlastní objekt příkazu, který dědí z <xref:System.Data.Common.DbCommand>. Zahrnuje zprostředkovatel dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro ODBC <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu. Každá z těchto metod zpřístupňuje objekty pro provádění příkazů na základě typu příkazu a potřeby návratovou hodnotu, jak je popsáno v následující tabulce.  
  
|Příkaz|Návratová hodnota|  
|-------------|------------------|  
|`ExecuteReader`|Vrátí hodnotu `DataReader` objektu.|  
|`ExecuteScalar`|Vrátí jednu skalární hodnotu.|  
|`ExecuteNonQuery`|Spustí příkaz, který nevrací žádné řádky.|  
|`ExecuteXMLReader`|Vrátí <xref:System.Xml.XmlReader>. K dispozici pro `SqlCommand` pouze objekt.|  
  
 Každý objekt silného typu příkazu podporuje také <xref:System.Data.CommandType> výčet, který určuje, jak se interpretují příkazového řetězce, jak je popsáno v následující tabulce.  
  
|Typ příkazu CommandType|Popis|  
|-----------------|-----------------|  
|`Text`|Příkaz SQL definování příkazy ve zdroji dat spouštění.|  
|`StoredProcedure`|Název uložené procedury. Můžete použít `Parameters` vlastnost příkaz, který má přístup k vstupní a výstupní parametry a návratové hodnoty, bez ohledu na to, které `Execute` metoda je volána. Při použití `ExecuteReader`, návratové hodnoty a výstupní parametry nebudou přístupné, dokud `DataReader` je uzavřený.|  
|`TableDirect`|Název tabulky.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlCommand> objekt ke spuštění uložené procedury nastavením jeho vlastnosti. A <xref:System.Data.SqlClient.SqlParameter> objekt se používá k určení vstupní parametr uložené procedury. Provedení příkazu pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metoda a výstup <xref:System.Data.SqlClient.SqlDataReader> se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Řešení potíží s příkazy  
 Zprostředkovatel dat .NET Framework pro SQL Server přidá čítačů výkonu vám umožní zjistit přerušované problémy související s jednotlivými spuštěními příkazu se nezdařilo. Další informace najdete v části [čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Práce s DataReaders](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
