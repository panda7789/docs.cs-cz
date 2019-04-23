---
title: Zprostředkovatel EntityClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: b8de4e36351a93858104a99045c5aeecce9d2997
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169673"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Zprostředkovatel EntityClient pro Entity Framework
Zprostředkovatel EntityClient je poskytovatel dat používané aplikacemi Entity Framework pro přístup k datům je popsáno v konceptuálním modelu. Informace o konceptuálních modelů najdete v tématu [modelování a mapování](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md). Zprostředkovatel EntityClient používá pro přístup ke zdroji dat jiné zprostředkovatele dat .NET Framework. Například zprostředkovatel EntityClient používá zprostředkovatele dat .NET Framework pro SQL Server (SqlClient) při přístupu k databázi serveru SQL Server. Informace o poskytovateli SqlClient najdete v tématu [SqlClient pro Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md). Zprostředkovatel EntityClient je implementována v <xref:System.Data.EntityClient> oboru názvů.  
  
## <a name="managing-connections"></a>Správa připojení  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Postavená na konkrétní úložiště [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zprostředkovatelé dat tím, že poskytuje <xref:System.Data.EntityClient.EntityConnection> na základní poskytovatel dat a relační databáze. K vytvoření <xref:System.Data.EntityClient.EntityConnection> objektu, budete muset odkazovat na sadu metadata, která obsahuje nezbytné modely a mapování a také data specifická pro úložiště poskytovatele název a připojovací řetězec. Po <xref:System.Data.EntityClient.EntityConnection> je na místě a přístupné prostřednictvím prostor tříd vygenerovaných z konceptuálního modelu entity.  
  
 Můžete zadat připojovací řetězec v souboru app.config.  
  
 <xref:System.Data.EntityClient> Zahrnuje také <xref:System.Data.EntityClient.EntityConnectionStringBuilder> třídy. Tato třída umožňuje vývojářům pro programové vytváření syntakticky správný připojovací řetězce a analyzovat a znovu vytvořit existující připojovací řetězce, pomocí vlastností a metod této třídy. Další informace najdete v tématu [jak: Vytvoření připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md).  
  
## <a name="creating-queries"></a>Vytváření dotazů  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Jazyk je nezávislý na úložišti dialekt SQL, který pracuje přímo s konceptuálními schématy entity a podporuje koncepty modelu Entity Data Model, jako je dědičnost a vztahy. <xref:System.Data.EntityClient.EntityCommand> Třída se používá ke spuštění [!INCLUDE[esql](../../../../../includes/esql-md.md)] příkaz proti modelu entity. Při sestavování <xref:System.Data.EntityClient.EntityCommand> objekty, můžete zadat název uložené procedury nebo text dotazu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Spolupracuje s poskytovateli data specifická pro úložiště pro převod obecný [!INCLUDE[esql](../../../../../includes/esql-md.md)] do konkrétní úložiště dotazů. Další informace o psaní [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazy, naleznete v tématu [jazyk Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
 Následující příklad vytvoří <xref:System.Data.EntityClient.EntityCommand> objektu a přiřazuje [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazování text, který se jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnost. To [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz požaduje produktů seřazených podle ceníku v konceptuálním modelu. Následující kód všech je vůbec nezná model úložiště.  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>Provádění dotazů  
 Pokud je dotaz proveden, je analyzovat a převést na strom canonical příkazů. Všechny následné zpracování se provádí na strom příkazů. Stromu příkazů je způsob komunikace mezi <xref:System.Data.EntityClient> a základní [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat, jako například <xref:System.Data.SqlClient>.  
  
 <xref:System.Data.EntityClient.EntityDataReader> Zpřístupňuje výsledky spuštění <xref:System.Data.EntityClient.EntityCommand> proti konceptuálního modelu. K provedení příkazu, který vrací <xref:System.Data.EntityClient.EntityDataReader>, volání <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>. <xref:System.Data.EntityClient.EntityDataReader> Implementuje <xref:System.Data.IExtendedDataRecord> k popisu formátu RTF strukturované výsledky.  
  
## <a name="managing-transactions"></a>Správa transakcí  
 V rozhraní Entity Framework, existují dva způsoby, jak používat transakce: automatické a explicitní. Použít automatické transakce <xref:System.Transactions> obor názvů a explicitní transakce pomocí <xref:System.Data.EntityClient.EntityTransaction> třídy.  
  
 Pokud chcete aktualizovat data, která je k dispozici prostřednictvím konceptuálního modelu, naleznete v tématu [jak: Správa transakcí v rozhraní Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření připojovacího řetězce EntityConnection](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Postupy: Spustit dotaz, který vrátí výsledky typu RefType](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí komplexní typy](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Postupy: Provedení dotazu, který vrátí vnořené kolekce](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Postupy: Provést parametrizovaného dotazu Entity SQL pomocí EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Postupy: Spuštění parametrizované uložené procedury pomocí EntityCommand](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Postupy: Spuštění Polymorfního dotazu](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Postupy: Procházení vztahů pomocí navigačního operátoru](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Viz také:

- [Správa připojení a transakce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)
- [Referenční dokumentace jazyka](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
