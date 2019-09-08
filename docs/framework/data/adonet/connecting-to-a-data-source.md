---
title: Připojení ke zdroji dat v ADO.NET
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 01e4048fb9c7b53b1b1907d1965f822b9a4644a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786760"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Připojení ke zdroji dat v ADO.NET
V ADO.NET použijete objekt **připojení** pro připojení ke konkrétnímu zdroji dat zadáním potřebných ověřovacích informací v připojovacím řetězci. Použitý objekt **připojení** závisí na typu zdroje dat.  
  
 Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, <xref:System.Data.Common.DbConnection> má objekt: .NET Framework Zprostředkovatel dat pro OLE DB <xref:System.Data.OleDb.OleDbConnection> obsahuje objekt, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje <xref:System.Data.SqlClient.SqlConnection> objekt,. Rozhraní .NET Framework Zprostředkovatel dat pro rozhraní ODBC <xref:System.Data.Odbc.OdbcConnection> zahrnuje objekt a .NET Framework Zprostředkovatel dat pro Oracle <xref:System.Data.OracleClient.OracleConnection> obsahuje objekt.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Navazování připojení](establishing-the-connection.md)  
 Popisuje způsob použití objektu **připojení** k navázání připojení ke zdroji dat.  
  
 [Události připojení](connection-events.md)  
 Popisuje, jak používat událost **InfoMessage** k načtení informativních zpráv ze zdroje dat.  
  
## <a name="see-also"></a>Viz také:

- [Připojovací řetězce](connection-strings.md)
- [Sdružování připojení](connection-pooling.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)
