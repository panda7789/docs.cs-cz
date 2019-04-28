---
title: 'Postupy: Přidání možností do dotazu v datové službě (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 2056b803b34faafdaebb85883de8b76ea2f9dcd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765541"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Postupy: Přidání možností do dotazu v datové službě (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje dotazování dat služby z klienta na základě rozhraní .NET Framework aplikace s použitím tříd generované klientské datové služby. Nejjednodušší k tomu je compose, který zahrnuje možnosti požadovaného dotazu výrazu dotazu Language Integrated Query (LINQ). Můžete také volat řadu metody LINQ dotazů k vytváření ekvivalentní dotazů. Nakonec můžete použít <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro přidání možností do dotazu. Ve všech těchto případech obsahuje identifikátor URI, který je generován klienta sady požadovaná entita se vybraný dotaz možnosti použít. Další informace najdete v tématu [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak sestavit výrazu dotazu LINQ, který vrátí pouze objednávky s cenou freight z více než 30 USD a že objednávky výsledky podle data příjemce v sestupném pořadí.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit dotaz LINQ pomocí metody dotazu LINQ, který je ekvivalentem předchozího dotazu.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro vytvoření <xref:System.Data.Services.Client.DataServiceQuery%601> , který je ekvivalentní předchozí příklady.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `$orderby` dotazu můžete filtrovat a řadit Freight vlastnost vrátí objekty objednávky.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [Postupy: Výsledky dotazu projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
