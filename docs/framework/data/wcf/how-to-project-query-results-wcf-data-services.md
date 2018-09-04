---
title: 'Postupy: výsledky dotazů (WCF Data Services) na projekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: c1eb2618e14f0e02aa5e1a2e91aa93fe0831c7c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508741"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Postupy: výsledky dotazů (WCF Data Services) na projekt
Projekce poskytuje mechanismus ke snížení množství dat vrácených dotazem tak, že určíte, které jsou vráceny pouze určité vlastnosti entity v odpovědi. Projekce můžete provádět na výsledcích [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] dotazování s použitím `$select` možnosti dotazu nebo s použitím [vyberte](~/docs/csharp/language-reference/keywords/select-clause.md) – klauzule ([vyberte](~/docs/visual-basic/language-reference/queries/select-clause.md) v jazyce Visual Basic) v dotazu LINQ. Další informace najdete v tématu [dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dotaz LINQ této projektů zákazníků entity do nové CustomerAddress typ, který obsahuje pouze vlastnosti specifické pro adresu a vlastnost identity. To `CustomerAddress` třída je definována na straně klienta a má atribut tak, aby Klientská knihovna dokáže rozpoznat jako typ entity.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje LINQ dotaz na tento zákazníkům entity vrácené projekty do nové CustomerAddressNonEntity typ, který obsahuje pouze adresy specifické vlastnosti a žádná vlastnost identity. To `CustomerAddressNonEntity` třída je definována na straně klienta a nemá atribut jako typ entity.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definici `CustomerAddress` a `CustomerAddressNonEntity` typy, které se používají v předchozích příkladech.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
