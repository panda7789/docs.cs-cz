---
title: Spuštění příkazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: f749ea37e1655f006e4de26e7cb279b778fe4faf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795105"
---
# <a name="executing-a-command"></a>Spuštění příkazu
Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, má svůj vlastní objekt příkazu, <xref:System.Data.Common.DbCommand>který dědí z. Zprostředkovatel dat .NET Framework pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbCommand> objekt, .NET Framework Zprostředkovatel dat pro SQL Server <xref:System.Data.SqlClient.SqlCommand> obsahuje objekt, .NET Framework Zprostředkovatel dat pro rozhraní ODBC zahrnuje <xref:System.Data.Odbc.OdbcCommand> objekt a .NET Framework Zprostředkovatel dat pro Oracle obsahuje <xref:System.Data.OracleClient.OracleCommand> objekt. Každý z těchto objektů zveřejňuje metody pro spouštění příkazů na základě typu příkazu a požadované návratové hodnoty, jak je popsáno v následující tabulce.  
  
|Příkaz|Návratová hodnota|  
|-------------|------------------|  
|`ExecuteReader`|Vrátí hodnotu `DataReader` objektu.|  
|`ExecuteScalar`|Vrátí jednu skalární hodnotu.|  
|`ExecuteNonQuery`|Provede příkaz, který nevrací žádné řádky.|  
|`ExecuteXMLReader`|<xref:System.Xml.XmlReader>Vrátí. K dispozici `SqlCommand` pouze pro objekt.|  
  
 Každý objekt příkazu silného typu také podporuje <xref:System.Data.CommandType> výčet, který určuje, jak je řetězec příkazu interpretován, jak je popsáno v následující tabulce.  
  
|CommandType|Popis|  
|-----------------|-----------------|  
|`Text`|Příkaz SQL definující příkazy, které mají být provedeny ve zdroji dat.|  
|`StoredProcedure`|Název uložené procedury. Můžete použít `Parameters` vlastnost příkazu pro přístup k vstupnímu a výstupnímu parametru a návratovým hodnotám bez ohledu na to `Execute` , která metoda je volána. Při použití `ExecuteReader`, návratové hodnoty a výstupní parametry nebudou přístupné, `DataReader` dokud není zavřeno.|  
|`TableDirect`|Název tabulky.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlCommand> objekt pro provedení uložené procedury nastavením vlastností. <xref:System.Data.SqlClient.SqlParameter> Objekt se používá k určení vstupního parametru pro uloženou proceduru. Příkaz se provede pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody a výstup <xref:System.Data.SqlClient.SqlDataReader> z konzoly se zobrazí v okně konzoly.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a>Příkazy pro řešení potíží  
 .NET Framework Zprostředkovatel dat pro SQL Server přidá čítače výkonu, které vám umožní detekovat občasné problémy související s neúspěšnými prováděními příkazů. Další informace najdete v tématu [čítače výkonu](performance-counters.md).  
  
## <a name="see-also"></a>Viz také:

- [Příkazy a parametry](commands-and-parameters.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Přehled ADO.NET](ado-net-overview.md)
