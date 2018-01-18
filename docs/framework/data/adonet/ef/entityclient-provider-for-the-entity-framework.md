---
title: "Zprostředkovatel EntityClient rozhraní Entity Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: eaccace7a333903e236107a72dbc17e19dc8d48a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Zprostředkovatel EntityClient rozhraní Entity Framework
Zprostředkovatel EntityClient je zprostředkovatele dat používaných aplikacemi Entity Framework pro přístup k datům, které jsou popsané v konceptuálním modelu. Informace o konceptuálních modelech najdete v tématu [modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). Zprostředkovatel EntityClient používá pro přístup ke zdroji dat jiných poskytovatelů dat rozhraní .NET Framework. Například EntityClient používá zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) při přístupu k databázi systému SQL Server. Informace o poskytovateli SqlClient najdete v tématu [SqlClient rozhraní Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). Zprostředkovatel EntityClient je implementována ve <xref:System.Data.EntityClient> oboru názvů.  
  
## <a name="managing-connections"></a>Správa připojení  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Sestavení nad specifické pro úložiště [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatelé dat tím, že poskytuje <xref:System.Data.EntityClient.EntityConnection> na základní zprostředkovatel dat a relační databáze. K vytvoření <xref:System.Data.EntityClient.EntityConnection> objektu, budete muset odkazovat na sadu metadata, která obsahuje nezbytné modely a mapování a také řetězec připojení a název zprostředkovatele dat specifických pro úložiště. Po <xref:System.Data.EntityClient.EntityConnection> je na místě, se dá dostat entity třídy vygenerované z konceptuálního modelu.  
  
 Můžete zadat připojovací řetězec v souboru app.config.  
  
 <xref:System.Data.EntityClient> Také zahrnuje <xref:System.Data.EntityClient.EntityConnectionStringBuilder> třídy. Tato třída umožňuje vývojářům prostřednictvím kódu programu syntakticky správný připojovací řetězce, vytvářet a analyzovat a znovu vytvořit existující připojovací řetězce, pomocí vlastnosti a metody třídy. Další informace najdete v tématu [postupy: sestavení řetězec připojení EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Vytváření dotazů  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Jazyk je nezávislé na úložiště dialekt SQL pracuje přímo s schémata koncepční entity, která podporuje model Entity Data Model koncepty například dědičnosti a vztahy. <xref:System.Data.EntityClient.EntityCommand> Třída se používá k provedení [!INCLUDE[esql](../../../../../includes/esql-md.md)] příkaz proti entity model. Když vytvoříte <xref:System.Data.EntityClient.EntityCommand> objekty, můžete zadat název uložené procedury nebo text dotazu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Spolupracuje s poskytovateli úložiště specifických dat přeložit Obecné [!INCLUDE[esql](../../../../../includes/esql-md.md)] do úložiště dotazů. Další informace o psaní [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy, najdete v části [jazyk SQL Entity](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 Následující příklad vytvoří <xref:System.Data.EntityClient.EntityCommand> objekt a přiřadí [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz na text, který se jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnost. To [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazu požadavky produktů seřazených podle ceníku z konceptuálního modelu. Následující kód nemá vůbec žádné informace o modelu úložiště.  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"``SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## <a name="executing-queries"></a>Provádění dotazů  
 Pokud je dotaz proveden, analyzovat a převést na strom kanonický příkazů. Všechny následné zpracování se provádí na strom příkazů. Strom příkazů je způsob komunikace mezi <xref:System.Data.EntityClient> a základní [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat, jako například <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Zpřístupní výsledky provádění <xref:System.Data.EntityClient.EntityCommand> proti konceptuálního modelu. K provedení příkazu, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Implementuje <xref:System.Data.IExtendedDataRecord> k popisu bohaté strukturovaná výsledky.  
  
## <a name="managing-transactions"></a>Správa transakcí  
 Rozhraní Entity Framework, existují dva způsoby, jak používat transakce: automatické a explicitní. Použít automatické transakce <xref:System.Transactions> použít obor názvů a explicitních transakcí <xref:System.Data.EntityClient.EntityTransaction> třídy.  
  
 Aktualizace dat, který je zveřejněný prostřednictvím konceptuálního modelu; v tématu [postupy: Správa transakce v rozhraní Entity Framework](http://msdn.microsoft.com/en-us/4a55eb7f-f826-4a48-9df1-aebe2352ebef).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Sestavení připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Postup: Provedení dotazu, který vrátí výsledky typu PrimitiveType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Postup: Provedení dotazu, který vrátí výsledky typu StructuralType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Postup: Provedení dotazu, který vrátí výsledky typu RefType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Postup: Provedení dotazu, který vrátí komplexní typy](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Postup: Provedení dotazu, který vrátí vnořené kolekce](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Postup: Spuštění polymorfního dotazu](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Postupy: Procházení relací pomocí navigačního operátoru](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Viz také  
 [Správa připojení a transakce](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Referenční dokumentace jazyka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
