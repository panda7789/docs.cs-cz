---
title: Získání jedné hodnoty z databáze
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: e362a71f902739663961099cf2f43dff90b4743c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711457"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Získání jedné hodnoty z databáze
Možná bude nutné k vrácení databáze informace, které jsou pouze jednu hodnotu, nikoli ve formě tabulky nebo datový proud. Například můžete chtít vrátit výsledek agregační funkce, jako je počet (\*), výraz SUM(Price) nebo AVG(Quantity). **Příkaz** objekt, který poskytuje schopnost vrátit jednu hodnotu pomocí **ExecuteScalar** metody. **ExecuteScalar** metoda vrátí hodnotu jako skalární hodnota, hodnota první sloupec prvního řádku sady výsledků dotazu.  
  
 Následující příklad kódu vloží novou hodnotu v databázi pomocí <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
