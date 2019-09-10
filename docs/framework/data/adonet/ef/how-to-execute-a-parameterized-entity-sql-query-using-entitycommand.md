---
title: 'Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: aa750ef088ee045c8d1045b2509d8fc4bde014ce
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854624"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand
Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotaz, který má parametry <xref:System.Data.EntityClient.EntityCommand> pomocí objektu.  
  
### <a name="to-run-the-code-in-this-example"></a>Spuštění kódu v tomto příkladu  
  
1. Přidejte do svého projektu [model AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) a nakonfigurujte projekt tak, aby používal Entity Framework. Další informace najdete v tématu [jak: Použijte průvodce](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))model EDM (Entity Data Model).  
  
2. Na kódové stránce vaší aplikace přidejte následující `using` příkazy (`Imports` v Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit řetězec dotazu se dvěma parametry. Potom vytvoří <xref:System.Data.EntityClient.EntityCommand>, přidá dva parametry <xref:System.Data.EntityClient.EntityParameter> do kolekce <xref:System.Data.EntityClient.EntityCommand>a provede iteraci kolekce `Contact` položek.  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Provedení parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))
- [Jazyk Entity SQL](./language-reference/entity-sql-language.md)
