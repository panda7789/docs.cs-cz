---
title: Spuštění příkazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: ed5ae1cbab40b57676219ffbe7d1d5696ac3bec4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209430"
---
# <a name="executing-a-command"></a>Spuštění příkazu
Každý poskytovatel dat rozhraní .NET Framework součástí rozhraní .NET Framework má svůj vlastní objekt příkazu, která dědí z <xref:System.Data.Common.DbCommand>. Obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlCommand> objektu zprostředkovatele dat .NET Framework pro ODBC zahrnuje <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu. Každá z těchto metod zpřístupňuje objekty pro spouštění příkazů na základě typu příkazu a požadovaného vrácené hodnoty, jak je popsáno v následující tabulce.  
  
|Příkaz|Návratová hodnota|  
|-------------|------------------|  
|`ExecuteReader`|Vrátí hodnotu `DataReader` objektu.|  
|`ExecuteScalar`|Vrátí jednu skalární hodnotu.|  
|`ExecuteNonQuery`|Provede příkaz, který nevrací žádné řádky.|  
|`ExecuteXMLReader`|Vrátí <xref:System.Xml.XmlReader>. K dispozici pro `SqlCommand` pouze objekt.|  
  
 Také podporuje každý příkaz silného typu objektu <xref:System.Data.CommandType> výčet, který určuje, jak interpretovat řetězec příkazu, jak je popsáno v následující tabulce.  
  
|CommandType|Popis|  
|-----------------|-----------------|  
|`Text`|Příkaz SQL definovat příkazy, které mají být provedeny ve zdroji dat.|  
|`StoredProcedure`|Název uložené procedury. Můžete použít `Parameters` vlastnost příkazu pro přístup k vstupní a výstupní parametry a návratové hodnoty, bez ohledu na to, které `Execute` metoda je volána. Při použití `ExecuteReader`, návratové hodnoty a výstupní parametry nebude dostupný dokud `DataReader` je zavřený.|  
|`TableDirect`|Název tabulky.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlCommand> objekt pro provedení uložené procedury nastavením jeho vlastností. A <xref:System.Data.SqlClient.SqlParameter> objektu se používá k určení vstupní parametr uložené procedury. Spuštění příkazu pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody a její výstup <xref:System.Data.SqlClient.SqlDataReader> se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Řešení potíží s příkazy  
 Zprostředkovatel dat .NET Framework pro SQL Server přidá čítačů výkonu rozpoznávat přerušované problémy související s spuštění příkazu se nezdařilo. Další informace najdete v části [čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Práce s čtečky dat](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
