---
title: Připojení ke zdroji dat v technologii ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 27653c3e1f14e08fc8b5e1225a441072778a0cc8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757109"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Připojení ke zdroji dat v technologii ADO.NET
V technologii ADO.NET použijete **připojení** objekt, který chcete připojit ke zdroji dat konkrétní zadáním informace nezbytné ověřování v připojovacím řetězci. **Připojení** objekt použijete, závisí na typu zdroje dat.  
  
 Má každý zprostředkovatel dat .NET Framework je součástí rozhraní .NET Framework <xref:System.Data.Common.DbConnection> objektu: zahrnuje zprostředkovatel dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbConnection> objektu, zahrnuje zprostředkovatel dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlConnection> objekt,. Zprostředkovatel dat NET Framework pro ODBC zahrnuje <xref:System.Data.Odbc.OdbcConnection> objekt a zprostředkovatel dat .NET Framework pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleConnection> objektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Navazování připojení](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 Popisuje způsob použití **připojení** objekt, který chcete vytvořit připojení ke zdroji dat.  
  
 [Události připojení](../../../../docs/framework/data/adonet/connection-events.md)  
 Popisuje, jak používat **InfoMessage** na načíst informační zprávy ze zdroje dat události.  
  
## <a name="see-also"></a>Viz také  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Sdružování připojení](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Adaptéry a čtečky dat](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Transakce a souběžnost](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
