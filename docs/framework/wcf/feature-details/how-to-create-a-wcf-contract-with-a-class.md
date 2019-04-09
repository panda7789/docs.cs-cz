---
title: 'Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: a514134ed0af3b691a2e66720f81594a51747b6f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089520"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou
Pomocí rozhraní je upřednostňovaným způsobem vytvoření kontraktu Windows Communication Foundation (WCF). Další informace najdete v tématu [jak: Definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md). Alternativní, osnovy tady, je vytvořit třídu a následně použít <xref:System.ServiceModel.ServiceContractAttribute> atribut třídy přímo a <xref:System.ServiceModel.OperationContractAttribute> atribut pro každou z metod ve třídě, které jsou součástí kontraktu.  
  
> [!WARNING]
>  `[ServiceContract]` a `[ServiceContractAttribute]` stejnou věc udělat. Totéž platí pro `[OperationContract]` a `[OperationContractAttribute]`. V obou případech je zkratka pro ten.  
  
 Další informace o kontraktech služeb najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Vytvoření kontraktu Windows Communication Foundation s třídou  
  
1.  Vytvořte novou třídu pomocí jazyka Visual Basic C#, nebo jakéhokoli jiného common language runtime jazyka.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy do třídy.  
  
3.  Vytvoření metod ve třídě.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou metodu, která musí být v rámci veřejného kontraktu WCF vystavené.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> Třída použitá použít model zprávy požadavku a odpovědi ve výchozím nastavení. Další informace o tomto vzoru zprávy naleznete v tématu [jak: Vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít další způsoby zpráva nastavením vlastností atributu. Další příklady najdete v tématu [jak: Vytvoření jednosměrného kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [jak: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
