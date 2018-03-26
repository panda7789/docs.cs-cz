---
title: Získání jednu hodnotu z databáze
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 41c3547d203a9958d3ad84303469c1e9591e6bd3
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="obtaining-a-single-value-from-a-database"></a>Získání jednu hodnotu z databáze
Může být nutné na návratový databáze informace, které je jednoduše jednu hodnotu, nikoli ve formě tabulky nebo datového proudu. Například můžete chtít vrátit výsledek agregační funkce jako je například počet (\*), výraz SUM(Price) nebo AVG(Quantity). **Příkaz** objekt poskytuje možnost vrácení jedné hodnoty pomocí **ExecuteScalar** metoda. **ExecuteScalar** metoda vrátí jako skalární hodnotu, hodnotu první sloupec prvního řádku sady výsledků dotazu.  
  
 Následující příklad kódu vloží novou hodnotu v databázi pomocí <xref:System.Data.SqlClient.SqlCommand>. <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> Metoda se používá k vrácení hodnota sloupce identity vloženého záznamu.  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Příkazy a parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Spuštění příkazu](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
