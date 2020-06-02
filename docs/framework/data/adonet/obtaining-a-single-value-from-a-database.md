---
title: Získání jedné hodnoty z databáze
description: Naučte se vracet jednu hodnotu v ADO.NET. Tento ukázkový kód vrátí hodnotu sloupce identity vloženého záznamu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: a6f268f72f8b8a09ae48ba3cad6254323cb95a20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286699"
---
# <a name="obtaining-a-single-value-from-a-database"></a>Získání jedné hodnoty z databáze
Možná budete muset vrátit databázové informace, které jsou jednoduše jedinou hodnotou, nikoli ve formě tabulky nebo datového proudu. Například můžete chtít vrátit výsledek agregační funkce, jako například COUNT ( \* ), Sum (price) nebo AVG (množství). Objekt **Command** poskytuje schopnost vracet jednotlivé hodnoty pomocí metody **ExecuteScalar** . Metoda **ExecuteScalar** vrací jako skalární hodnotu hodnotu prvního sloupce prvního řádku sady výsledků dotazu.  
  
 Následující příklad kódu vloží novou hodnotu do databáze pomocí <xref:System.Data.SqlClient.SqlCommand> . <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>Metoda se používá k vrácení hodnoty sloupce identity pro vložený záznam.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Příkazy a parametry](commands-and-parameters.md)
- [Spuštění příkazu](executing-a-command.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Přehled ADO.NET](ado-net-overview.md)
