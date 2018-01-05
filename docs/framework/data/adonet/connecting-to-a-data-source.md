---
title: "Připojení ke zdroji dat v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 01a7342d6e081bec88aeef2c55461be2d936e4a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
