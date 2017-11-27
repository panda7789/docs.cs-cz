---
title: "Postupy: projektu výsledků dotazu (služby WCF Data Services)"
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
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b3e6b05952dfc87a911b1a80582cd27b327d6a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Postupy: projektu výsledků dotazu (služby WCF Data Services)
Projekce poskytuje mechanismus ke snížení objemu dat vrácených dotazem zadáním jenom některé vlastnosti entity jsou vráceny v odpovědi. Projekce můžete provádět na výsledcích [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] buď pomocí dotazu `$select` dotaz možnost nebo pomocí [vyberte](~/docs/csharp/language-reference/keywords/select-clause.md) klauzule ([vyberte](~/docs/visual-basic/language-reference/queries/select-clause.md) v jazyce Visual Basic) v dotazu LINQ. Další informace najdete v tématu [dotaz na službu Data](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 V příkladu v tomto tématu používá Northwind ukázková data služby a automaticky generovaný klienta dat služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dotaz LINQ této projekty zákazníkům entity do nový typ CustomerAddress, který obsahuje pouze vlastnosti specifické pro adresu plus vlastnost identity. To `CustomerAddress` třída definována na straně klienta a je nastavený atribut tak, aby klientské knihovny může rozpoznat jako typ entity.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje LINQ dotaz vrácené entity zákazníkům této projekty do nový typ CustomerAddressNonEntity, která obsahuje jenom adresy specifické vlastnosti a žádná vlastnost identity. To `CustomerAddressNonEntity` třída definována na straně klienta a není označené jako typ entity.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje definice `CustomerAddress``CustomerAddressNonEntity` typy, které se používají v předchozích příkladech.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customeraddress.vb#customeraddressdefinition)]
