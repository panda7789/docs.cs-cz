---
title: 'Postupy: určení počtu entity vrácené dotazem (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: 183fed2d267fc16767c902cdd69513aa9986ff78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364996"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>Postupy: určení počtu entity vrácené dotazem (služby WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete určit počet entit, které jsou v zadaný identifikátor URI dotazu na sadu entit. Tento počet může být zahrnuta, společně s výsledek dotazu nebo jako celočíselnou hodnotu. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se provede dotaz po volání <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metoda. <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> Vlastnost vrací počet entit v `Customers` sady entit.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>Příklad  
 Tento příklad volá <xref:System.Linq.Enumerable.Count%2A> metoda vrátí pouze celočíselnou hodnotu to znamená počet entit v `Customers` sady entit.  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
