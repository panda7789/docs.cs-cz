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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1df18730d3a4428f245fe4222dafec0eaf6c08a5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
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
