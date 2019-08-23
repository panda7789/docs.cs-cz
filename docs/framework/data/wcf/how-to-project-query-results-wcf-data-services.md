---
title: 'Postupy: Výsledky dotazu projektu (WCF Data Services)'
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
ms.openlocfilehash: b53da9c1ecfcc5061fe551c4e180774319beaf5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952227"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Postupy: Výsledky dotazu projektu (WCF Data Services)
Projekce poskytuje mechanismus pro snížení množství dat vrácených dotazem tím, že zadáte, že v odpovědi se vrátí jenom některé vlastnosti entity. Můžete provést [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] projekce pro výsledky dotazu buď `$select` pomocí možnosti dotazu, nebo pomocí klauzule [Select](../../../csharp/language-reference/keywords/select-clause.md) ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) v dotazu LINQ. Další informace najdete v tématu [dotazování datové služby](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá ukázková datová služba Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dotaz LINQ, který prokáže, že Projects zavede entity do nového typu CustomerAddress, který obsahuje pouze vlastnosti specifické pro adresu a vlastnost identity. Tato `CustomerAddress` třída je definována v klientovi a má atribut, aby ji Klientská knihovna mohla rozpoznat jako typ entity.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dotaz LINQ, který projekty vrátily entity zákazníkům do nového typu CustomerAddressNonEntity, který obsahuje pouze vlastnosti specifické pro adresu a žádnou vlastnost identity. Tato `CustomerAddressNonEntity` třída je definována v klientovi a není považována za typ entity.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definice `CustomerAddress` typů a `CustomerAddressNonEntity` , které jsou použity v předchozích příkladech.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
