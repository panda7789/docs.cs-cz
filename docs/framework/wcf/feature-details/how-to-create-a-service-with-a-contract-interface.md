---
title: 'Postupy: Vytvoření služby pomocí rozhraní kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: cd0ae76040f235b4573a90764566205a2d5d81e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536721"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Postupy: Vytvoření služby pomocí rozhraní kontraktu
Pomocí rozhraní je upřednostňovaný způsob vytvoření kontraktu Windows Communication Foundation (WCF). Tento kontrakt určuje kolekci a struktura zpráv, které jsou nutné pro přístup k operace nabídky služeb. Toto rozhraní definuje vstupní a výstupní typy použitím <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní a <xref:System.ServiceModel.OperationContractAttribute> třídy pro metody, které chcete zveřejnit.  
  
 Další informace o kontraktech služeb najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Vytvoření pomocí rozhraní kontraktu WCF  
  
1.  Vytvoření nového rozhraní pomocí jazyka Visual Basic C#, nebo jakéhokoli jiného common language runtime jazyka.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.  
  
3.  Definujte metody v rozhraní.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou metodu, která musí být v rámci veřejného kontraktu WCF vystavené.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje rozhraní, které definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> Třída použitá použít model zprávy požadavku a odpovědi ve výchozím nastavení. Další informace o tomto vzoru zprávy naleznete v tématu [jak: Vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít další způsoby zpráva nastavením vlastností atributu. Další příklady najdete v tématu [jak: Vytvoření jednosměrného kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [jak: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
