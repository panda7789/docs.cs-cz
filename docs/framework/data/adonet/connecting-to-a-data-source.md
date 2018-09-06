---
title: Připojení ke zdroji dat v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: f5788b9b0b19f32d03c917575db7b3f40324c0a2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44031723"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Připojení ke zdroji dat v ADO.NET
V ADO.NET pomocí **připojení** objektu, který chcete připojit ke konkrétnímu zdroji dat zadáním potřebné ověřovací údaje v připojovacím řetězci. **Připojení** objektu použijete, závisí na typu zdroje dat.  
  
 Má každý zprostředkovatele dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbConnection> objektu: obsahuje zprostředkovatele dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbConnection> objektu zprostředkovatele dat .NET Framework pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlConnection> objektu,. Zahrnuje NET Framework Data Provider pro rozhraní ODBC <xref:System.Data.Odbc.OdbcConnection> objektu a zprostředkovatele dat .NET Framework pro Oracle se zahrnuje <xref:System.Data.OracleClient.OracleConnection> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Navazování připojení](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Popisuje způsob použití **připojení** k navázání připojení ke zdroji dat objektu.  
  
 [Události připojení](../../../../docs/framework/data/adonet/connection-events.md)  
 Popisuje způsob použití **InfoMessage** na načtení informační zprávy ze zdroje dat události.  
  
## <a name="see-also"></a>Viz také  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
