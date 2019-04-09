---
title: 'Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: 252d04ce96e222526bfd3d3e0b798f1c5edd2c8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079705"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>Postupy: Spuštění parametrizovaného dotazu Entity SQL pomocí EntityCommand
Toto téma ukazuje, jak spustit [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotazu, který obsahuje parametry s využitím <xref:System.Data.EntityClient.EntityCommand> objektu.  
  
### <a name="to-run-the-code-in-this-example"></a>Chcete-li spustit kód v tomto příkladu  
  
1.  Přidat [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do vašeho projektu a konfigurace projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [jak: Použijte Průvodce datovým modelem Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2.  V kódové stránce pro vaši aplikaci, přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit řetězec dotazu se dvěma parametry. Potom vytvoří <xref:System.Data.EntityClient.EntityCommand>, přidá dva parametry do <xref:System.Data.EntityClient.EntityParameter> kolekce, která <xref:System.Data.EntityClient.EntityCommand>a Iteruje přes kolekci `Contact` položky.  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Spuštění parametrizovaného dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))
- [Jazyk Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
