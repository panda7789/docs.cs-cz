---
title: 'Postupy: Provedení dotazu, který vrátí výsledky typu RefType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: c9f3b7e19770c89bbb200913bf7fcf44f901ea99
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854573"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a>Postupy: Provedení dotazu, který vrátí výsledky typu RefType
Toto téma ukazuje, jak spustit příkaz pro koncepční model pomocí <xref:System.Data.EntityClient.EntityCommand> objektu a jak <xref:System.Data.Metadata.Edm.RefType> načíst výsledky pomocí <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Spuštění kódu v tomto příkladu  
  
1. Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
2. Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Příklad  
 Tento příklad spustí dotaz, který vrátí <xref:System.Data.Metadata.Edm.RefType> výsledky. Pokud předáte následující dotaz jako argument `ExecuteRefTypeQuery` funkci, vrátí funkce odkaz na entitu:  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 Pokud předáte parametrizovaný dotaz, podobně jako následující, přidejte <xref:System.Data.EntityClient.EntityParameter> objekty <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> do vlastnosti <xref:System.Data.EntityClient.EntityCommand> objektu.  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](./language-reference/entity-sql-reference.md)
- [Zprostředkovatel EntityClient pro Entity Framework](entityclient-provider-for-the-entity-framework.md)
