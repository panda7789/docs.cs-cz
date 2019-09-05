---
title: Zprostředkovatel EntityClient pro Entity Framework
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 70cc5a9aaa22cc563c910f9d250ad4565e34a135
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251605"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Zprostředkovatel EntityClient pro Entity Framework
Zprostředkovatel EntityClient je poskytovatel dat, který používá aplikace Entity Framework pro přístup k datům, která jsou popsaná v koncepčním modelu. Informace o koncepčních modelech najdete v tématu [modelování a mapování](modeling-and-mapping.md). Zprostředkovatel EntityClient pro přístup ke zdroji dat používá jiné poskytovatele dat .NET Framework. Pro přístup k databázi SQL Server například EntityClient používá .NET Framework Zprostředkovatel dat pro SQL Server (SqlClient). Informace o poskytovateli SqlClient najdete v tématu [SqlClient pro Entity Framework](sqlclient-for-the-entity-framework.md). Zprostředkovatel EntityClient je implementován v <xref:System.Data.EntityClient> oboru názvů.  
  
## <a name="managing-connections"></a>Správa připojení  
 Sestavuje na poskytovatele dat ADO.NET specifických <xref:System.Data.EntityClient.EntityConnection> pro úložiště tím, že poskytuje základnímu poskytovateli dat a relační databázi. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Chcete-li <xref:System.Data.EntityClient.EntityConnection> vytvořit objekt, musíte odkazovat na sadu metadat, která obsahuje nezbytné modely a mapování, a také na název zprostředkovatele dat a připojovací řetězec specifický pro úložiště. Po umístění <xref:System.Data.EntityClient.EntityConnection> je možné k entitám přicházet prostřednictvím tříd vygenerovaných z koncepčního modelu.  
  
 Můžete zadat připojovací řetězec v souboru App. config.  
  
 <xref:System.Data.EntityClient> Zahrnuje<xref:System.Data.EntityClient.EntityConnectionStringBuilder> také třídu. Tato třída umožňuje vývojářům programově vytvářet syntakticky správné připojovací řetězce a analyzovat a znovu sestavovat existující připojovací řetězce pomocí vlastností a metod třídy. Další informace najdete v tématu [jak: Sestavte připojovací řetězec](how-to-build-an-entityconnection-connection-string.md)EntityConnection.  
  
## <a name="creating-queries"></a>Vytváření dotazů  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] Jazyk je dialekt SQL nezávislý na úložišti, který pracuje přímo s koncepčními schématy entit a podporuje model EDM (Entity Data Model) konceptů, jako jsou dědičnost a vztahy. Třída se používá ke [!INCLUDE[esql](../../../../../includes/esql-md.md)] spuštění příkazu proti modelu entity. <xref:System.Data.EntityClient.EntityCommand> Při vytváření <xref:System.Data.EntityClient.EntityCommand> objektů můžete zadat název uložené procedury nebo text dotazu. Spolupracuje s poskytovateli dat specifických pro úložiště k překladu [!INCLUDE[esql](../../../../../includes/esql-md.md)] obecných na dotazy specifických pro úložiště. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Další informace o zápisu [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazů naleznete v tématu [Entity SQL Language](./language-reference/entity-sql-language.md).  
  
 Následující příklad vytvoří <xref:System.Data.EntityClient.EntityCommand> objekt a [!INCLUDE[esql](../../../../../includes/esql-md.md)] přiřadí text dotazu k jeho <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> vlastnosti. Tento [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz vyžádá produkty seřazené podle ceny za seznam koncepčního modelu. Následující kód nemá žádné znalosti modelu úložiště vůbec.  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>Provádění dotazů  
 Při spuštění dotazu se analyzuje a převede na kanonický strom příkazů. Veškeré následné zpracování se provádí ve stromu příkazů. Strom příkazů je způsob komunikace mezi serverem <xref:System.Data.EntityClient> a podkladovým poskytovatelem .NET Framework dat, <xref:System.Data.SqlClient>jako je například.  
  
 Zpřístupňuje výsledky provádění s <xref:System.Data.EntityClient.EntityCommand> koncepčním modelem. <xref:System.Data.EntityClient.EntityDataReader> Chcete-li spustit příkaz, který <xref:System.Data.EntityClient.EntityDataReader>vrátí, <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>zavolejte. <xref:System.Data.EntityClient.EntityDataReader> Implementuje<xref:System.Data.IExtendedDataRecord> k popisu bohatě strukturovaných výsledků.  
  
## <a name="managing-transactions"></a>Správa transakcí  
 V Entity Framework Existují dva způsoby, jak použít transakce: automaticky a Explicit. Automatické transakce používají <xref:System.Transactions> obor názvů a explicitní transakce <xref:System.Data.EntityClient.EntityTransaction> používají třídu.  
  
 Chcete-li aktualizovat data, která jsou zveřejněna prostřednictvím koncepčního [modelu, přečtěte si téma How to: Spravujte transakce v Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření připojovacího řetězce EntityConnection](how-to-build-an-entityconnection-connection-string.md)  
  
 [Postupy: Spustí dotaz, který vrátí výsledky PrimitiveType.](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí výsledky StructuralType](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [Postupy: Provedení dotazu, který vrátí výsledky RefType](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [Postupy: Spustí dotaz, který vrátí komplexní typy.](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [Postupy: Spustit dotaz, který vrátí vnořené kolekce](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [Postupy: Provedení parametrizovaného Entity SQLového dotazu pomocí EntityCommand](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [Postupy: Provedení parametrizované uložené procedury pomocí EntityCommand](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [Postupy: Spustit polymorfní dotaz](how-to-execute-a-polymorphic-query.md)  
  
 [Postupy: Navigace v relacích pomocí operátoru navigace](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>Viz také:

- [Správa připojení a transakcí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](index.md)
- [Referenční dokumentace jazyka](./language-reference/index.md)
