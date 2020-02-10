---
title: Připojení ke zdroji dat
ms.date: 03/30/2017
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
ms.openlocfilehash: 206a4f741b6bf711b51da794e23f779c2bea6fa0
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094446"
---
# <a name="connecting-to-a-data-source-in-adonet"></a>Připojení ke zdroji dat v ADO.NET

V ADO.NET použijete objekt **připojení** pro připojení ke konkrétnímu zdroji dat zadáním potřebných ověřovacích informací v připojovacím řetězci. Použitý objekt **připojení** závisí na typu zdroje dat.  
  
 Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, má <xref:System.Data.Common.DbConnection> objekt: .NET Framework Zprostředkovatel dat pro OLE DB obsahuje objekt <xref:System.Data.OleDb.OleDbConnection>, .NET Framework Zprostředkovatel dat pro SQL Server obsahuje objekt <xref:System.Data.SqlClient.SqlConnection>, .NET Framework Zprostředkovatel dat pro rozhraní ODBC zahrnuje <xref:System.Data.Odbc.OdbcConnection> objekt a .NET Framework Zprostředkovatel dat pro Oracle zahrnuje objekt <xref:System.Data.OracleClient.OracleConnection>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Navázání\ připojení](establishing-the-connection.md)
 Popisuje způsob použití objektu **připojení** k navázání připojení ke zdroji dat.  
  
 \ [události připojení](connection-events.md)
 Popisuje, jak používat událost **InfoMessage** k načtení informativních zpráv ze zdroje dat.  
  
## <a name="see-also"></a>Viz také

- [Připojovací řetězce](connection-strings.md)
- [Sdružování připojení](connection-pooling.md)
- [Příkazy a parametry](commands-and-parameters.md)
- [Adaptéry a čtečky dat](dataadapters-and-datareaders.md)
- [Transakce a souběžnost](transactions-and-concurrency.md)
- [Přehled ADO.NET](ado-net-overview.md)
