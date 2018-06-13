---
title: 'Postupy: Vytvoření služby pomocí rozhraní kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 796870b80ed72db2353e79db3e4e3fc164c22875
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489791"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Postupy: Vytvoření služby pomocí rozhraní kontraktu
Pomocí rozhraní je upřednostňovaný způsob vytvoření kontraktu Windows Communication Foundation (WCF). Tento kontrakt určuje kolekci a struktura zpráv, které jsou nutné pro přístup k činnosti nabídky služeb. Toto rozhraní definuje vstupní a výstupní typy použitím <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní a <xref:System.ServiceModel.OperationContractAttribute> třídy metody, které chcete vystavit.  
  
 Další informace o kontraktů služby najdete v tématu [navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Vytvoření kontraktu WCF pomocí rozhraní  
  
1.  Vytvořte nové rozhraní pomocí jazyka Visual Basic, C# nebo jakéhokoli jiného common language runtime jazyka.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní.  
  
3.  Definujte metody v rozhraní.  
  
4.  Použít <xref:System.ServiceModel.OperationContractAttribute> třída pro každou metodu, který musí být zveřejněný v rámci veřejného kontraktu WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje rozhraní, které definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> třída použije ve výchozím nastavení používá vzor zprávu požadavku a odpovědi. Další informace o tomto vzoru zpráva najdete v tématu [postupy: vytvoření kontraktu požadavku a odpovědi](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít dalších zpráv vzorech nastavením vlastnosti atributu. Další příklady najdete v tématu [postupy: vytvoření kontraktu One-Way](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>
