---
title: 'Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 296f500532040aaebf0f6d7d37a7a9aae99a3451
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491808"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou
Pomocí rozhraní je upřednostňovaný způsob vytvoření kontraktu Windows Communication Foundation (WCF). Další informace najdete v tématu [postupy: definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Alternativní, popsané tady, je vytvoření třídy a následně použít <xref:System.ServiceModel.ServiceContractAttribute> atribut třídy přímo a <xref:System.ServiceModel.OperationContractAttribute> atribut každá z metod ve třídě, které jsou součástí smlouvy.  
  
> [!WARNING]
>  `[ServiceContract]` a `[ServiceContractAttribute]` stejnou věc udělat. Samé ho true pro `[OperationContract]` a `[OperationContractAttribute]`. V každém případě je sdružená vlastnost pro tento první.  
  
 Další informace o kontraktů služby najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Vytvoření kontraktu Windows Communication Foundation s třídou  
  
1.  Vytvořte novou třídu pomocí jazyka Visual Basic, C# nebo jakéhokoli jiného common language runtime jazyka.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třída pro třídu.  
  
3.  Vytvoření metody ve třídě.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každou metodu, který musí být zveřejněný v rámci veřejného kontraktu WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> třída použije ve výchozím nastavení používá vzor zprávu požadavku a odpovědi. Další informace o tomto vzoru zpráva najdete v tématu [postupy: vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít dalších zpráv vzorech nastavením vlastnosti atributu. Další příklady najdete v tématu [postupy: vytvoření kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
