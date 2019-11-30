---
title: 'Postupy: Přidání možností dotazu do dotazu datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 7b5a9c15f2d46c89abf8fb5bc0f4be99e501a267
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569185"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Postupy: Přidání možností dotazu do dotazu datové služby (WCF Data Services)
WCF Data Services umožňuje dotazovat se na datovou službu z klientské aplikace založené na .NET Framework pomocí vygenerovaných tříd klientské datové služby. Nejjednodušší je vytvořit výraz dotazu LINQ (Language Integrated Query), který obsahuje požadované možnosti dotazu. Můžete také volat řadu metod dotazů LINQ pro vytvoření ekvivalentního dotazu. Nakonec můžete pomocí metody <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> přidat do dotazu možnosti dotazu. V každém z těchto případů identifikátor URI generovaný klientem zahrnuje požadovanou sadu entit s použitými možnostmi zvolených dotazů. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit výraz dotazu LINQ, který vrátí pouze objednávky s náklady na dopravné více než $30 a který seřadí výsledky podle data expedice v sestupném pořadí.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit dotaz LINQ pomocí metod dotazů LINQ, který je ekvivalentní předchozímu dotazu.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít metodu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> k vytvoření <xref:System.Data.Services.Client.DataServiceQuery%601>, který je ekvivalentní předchozím příkladům.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít možnost dotazu `$orderby` pro filtrování i řazení vrácených objednávek do objektů podle vlastnosti dopravného.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Postupy: Výsledky dotazů na projekt](how-to-project-query-results-wcf-data-services.md)
