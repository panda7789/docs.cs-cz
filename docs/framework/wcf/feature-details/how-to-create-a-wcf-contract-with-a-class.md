---
title: "Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf32559f9b5a1040390562cc8492646288494638
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou
Upřednostňovaný způsob vytváření [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kontrakt je pomocí rozhraní. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Alternativní, popsané tady, je vytvoření třídy a následně použít <xref:System.ServiceModel.ServiceContractAttribute> atribut třídy přímo a <xref:System.ServiceModel.OperationContractAttribute> atribut každá z metod ve třídě, které jsou součástí smlouvy.  
  
> [!WARNING]
>  `[ServiceContract]`a `[ServiceContractAttribute]` stejnou věc udělat. Samé ho true pro `[OperationContract]` a `[OperationContractAttribute]`. V každém případě je sdružená vlastnost pro tento první.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontrakty najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Vytvoření kontraktu Windows Communication Foundation s třídou  
  
1.  Vytvoření nové třídy pomocí [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# nebo jakéhokoli jiného common language runtime jazyka.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třída pro třídu.  
  
3.  Vytvoření metody ve třídě.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každou metodu, který musí být zveřejněný v rámci veřejnosti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> třída použije ve výchozím nastavení používá vzor zprávu požadavku a odpovědi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tento vzor zpráv najdete v části [postupy: vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít dalších zpráv vzorech nastavením vlastnosti atributu. Další příklady najdete v tématu [postupy: vytvoření kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
