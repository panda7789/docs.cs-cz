---
title: Získání jedné hodnoty z databáze
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: fb43d21546a0e98e87aab23db9213309b62320b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794747"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Získání jedné hodnoty z databáze
Možná budete muset vrátit databázové informace, které jsou jednoduše jedinou hodnotou, nikoli ve formě tabulky nebo datového proudu. Například můžete chtít vrátit výsledek agregační funkce, jako například Count (\*), Sum (price) nebo AVG (množství). Objekt **Command** poskytuje schopnost vracet jednotlivé hodnoty pomocí metody **ExecuteScalar** . Metoda **ExecuteScalar** vrací jako skalární hodnotu hodnotu prvního sloupce prvního řádku sady výsledků dotazu.  
  
 Následující příklad kódu vloží novou hodnotu do databáze pomocí <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Příkazy a parametry](commands-and-parameters.md)
- [Spuštění příkazu](executing-a-command.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Přehled ADO.NET](ado-net-overview.md)
