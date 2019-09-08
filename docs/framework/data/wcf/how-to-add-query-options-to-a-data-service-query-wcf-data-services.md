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
ms.openlocfilehash: f7b0557938d1419b79c3191cf8f9110cab2f5ce6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790782"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Postupy: Přidání možností dotazu do dotazu datové služby (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje zadávat dotazy na datovou službu z .NET Framework klientské aplikace založené na vygenerovaných třídách klientské datové služby. Nejjednodušší je vytvořit výraz dotazu LINQ (Language Integrated Query), který obsahuje požadované možnosti dotazu. Můžete také volat řadu metod dotazů LINQ pro vytvoření ekvivalentního dotazu. Nakonec můžete použít <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro přidání možností dotazu do dotazu. V každém z těchto případů identifikátor URI generovaný klientem zahrnuje požadovanou sadu entit s použitými možnostmi zvolených dotazů. Další informace najdete v tématu [dotazování datové služby](querying-the-data-service-wcf-data-services.md).  
  
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
 Následující příklad ukazuje, jak použít <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu k vytvoření typu <xref:System.Data.Services.Client.DataServiceQuery%601> , který je ekvivalentní předchozím příkladům.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít `$orderby` možnost dotazu pro filtrování i řazení vrácených objednávek do objektů pomocí vlastnosti dopravného.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
- [Postupy: Výsledky dotazu projektu](how-to-project-query-results-wcf-data-services.md)
