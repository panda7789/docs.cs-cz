---
title: 'Postupy: Provedení dotazu, který vrátí výsledky typu PrimitiveType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: a00448f1c521d468db4cdaa957f92772194c8b43
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854880"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a>Postupy: Provedení dotazu, který vrátí výsledky typu PrimitiveType
Toto téma ukazuje <xref:System.Data.EntityClient.EntityCommand>, jak spustit příkaz pro koncepční model pomocí a jak <xref:System.Data.Metadata.Edm.PrimitiveType> načíst výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Spuštění kódu v tomto příkladu  
  
1. Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
2. Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Příklad  
 Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.PrimitiveType> výsledek. Pokud předáte následující dotaz jako argument `ExecutePrimitiveTypeQuery` funkci, funkce zobrazí průměrnou Ceník všech: `Products`  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 Pokud předáte parametrizovaný dotaz, podobně jako následující, <xref:System.Data.EntityClient.EntityParameter> objekty <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> na vlastnost <xref:System.Data.EntityClient.EntityCommand> objektu.  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](./language-reference/entity-sql-reference.md)
- [Zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md)
