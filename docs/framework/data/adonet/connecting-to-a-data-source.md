---
title: Připojení ke zdroji dat
deescription: Learn about Connection objects, used to connect to data sources in ADO.NET. The Connection object you choose depends on the type of data source.
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: a14fe179cf2fc8714a54e52252c53bd71346cad3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287074"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Připojení ke zdroji dat v ADO.NET

V ADO.NET použijete objekt **připojení** pro připojení ke konkrétnímu zdroji dat zadáním potřebných ověřovacích informací v připojovacím řetězci. Použitý objekt **připojení** závisí na typu zdroje dat.  
  
 Každý .NET Framework poskytovatel dat, který je součástí .NET Framework <xref:System.Data.Common.DbConnection> , má objekt: .NET Framework Zprostředkovatel dat pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbConnection> objekt, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje objekt, .NET Framework Zprostředkovatel dat <xref:System.Data.SqlClient.SqlConnection> pro rozhraní ODBC obsahuje objekt a .NET Framework Zprostředkovatel dat <xref:System.Data.Odbc.OdbcConnection> pro Oracle <xref:System.Data.OracleClient.OracleConnection> obsahuje objekt.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Navazování připojení](establishing-the-connection.md)\
 Popisuje způsob použití objektu **připojení** k navázání připojení ke zdroji dat.  
  
 [Události připojení](connection-events.md)\
 Popisuje, jak používat událost **InfoMessage** k načtení informativních zpráv ze zdroje dat.  
  
## <a name="see-also"></a>Viz také

- [Připojovací řetězce](connection-strings.md)
- [Sdružování připojení](connection-pooling.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)
