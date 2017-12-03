---
title: "Postupy: Vytvoření služby pomocí rozhraní kontraktu"
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
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cf3938f96674b07a7938861e217a93babd83101
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Postupy: Vytvoření služby pomocí rozhraní kontraktu
Upřednostňovaný způsob, jak vytvořit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kontrakt je pomocí rozhraní. Tento kontrakt určuje kolekci a struktura zpráv, které jsou nutné pro přístup k činnosti nabídky služeb. Toto rozhraní definuje vstupní a výstupní typy použitím <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní a <xref:System.ServiceModel.OperationContractAttribute> třídy metody, které chcete vystavit.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontrakty najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Vytvoření kontraktu WCF pomocí rozhraní  
  
1.  Vytvoření nové rozhraní pomocí [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], C# nebo jakéhokoli jiného common language runtime jazyka.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.  
  
3.  Definujte metody v rozhraní.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každou metodu, který musí být zveřejněný v rámci veřejnosti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje rozhraní, které definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> třída použije ve výchozím nastavení používá vzor zprávu požadavku a odpovědi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tento vzor zpráv najdete v části [postupy: vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít dalších zpráv vzorech nastavením vlastnosti atributu. Další příklady najdete v tématu [postupy: vytvoření kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
