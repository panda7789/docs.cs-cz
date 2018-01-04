---
title: "Postupy: Přidání možnosti dotazu do služby dotaz na Data (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55ed062ce2b4464618dfdb8184be65847195280d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Postupy: Přidání možnosti dotazu do služby dotaz na Data (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Umožňuje dotazovat datové služby z klienta na základě rozhraní .NET Framework aplikace pomocí generovaného klienta datových služba tříd. Nejjednodušší k tomu je tvoří výrazu dotazu jazyka integrovaného dotazu (LINQ), který zahrnuje možnosti požadovaný dotaz. Můžete také zavolat řadu metody LINQ dotazů k vytváření ekvivalentní dotazů. Nakonec můžete použít <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro přidání do dotazu možnosti dotazu. V každém z těchto případech se identifikátor URI, který je generovaný klienta má požadovaná entita s možnostmi vybraný dotaz, použít. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit výraz dotazu LINQ, který vrací pouze s více než 30 $ nákladní náklady a že objednávky výsledky podle data expedice v sestupném pořadí.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k vytváření LINQ dotazů pomocí metody dotazů LINQ, který je ekvivalentem předchozího dotazu.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro vytvoření <xref:System.Data.Services.Client.DataServiceQuery%601> tedy ekvivalent v předchozích příkladech.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `$orderby` možnost dotazu filtru a pořadí vrácených vlastnost nákladní objednávky objekty.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [Postupy: Výsledky dotazů na projekt](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
