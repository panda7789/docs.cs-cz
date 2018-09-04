---
title: Získání jedné hodnoty z databáze
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: 1a0d92c7acad58d3618c3f50b7463022352cf542
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560854"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Získání jedné hodnoty z databáze
Možná bude nutné k vrácení databáze informace, které jsou pouze jednu hodnotu, nikoli ve formě tabulky nebo datový proud. Například můžete chtít vrátit výsledek agregační funkce, jako je počet (\*), výraz SUM(Price) nebo AVG(Quantity). **Příkaz** objekt, který poskytuje schopnost vrátit jednu hodnotu pomocí **ExecuteScalar** metody. **ExecuteScalar** metoda vrátí hodnotu jako skalární hodnota, hodnota první sloupec prvního řádku sady výsledků dotazu.  
  
 Následující příklad kódu vloží novou hodnotu v databázi pomocí <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
