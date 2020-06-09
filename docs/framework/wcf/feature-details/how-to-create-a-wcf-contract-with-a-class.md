---
title: 'Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 0be2400ef3da5f0bbc218032ecd69af23f82cabd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597134"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou
Upřednostňovaným způsobem vytvoření kontraktu Windows Communication Foundation (WCF) je použití rozhraní. Další informace najdete v tématu [Postup: Definování kontraktu služby](../how-to-define-a-wcf-service-contract.md). Alternativa, která je zde uvedená, je vytvořit třídu a potom použít <xref:System.ServiceModel.ServiceContractAttribute> atribut přímo pro třídu a <xref:System.ServiceModel.OperationContractAttribute> atribut pro každou metodu ve třídě, která je součástí kontraktu.  
  
> [!WARNING]
> `[ServiceContract]`a `[ServiceContractAttribute]` udělejte stejné věci. Totéž platí pro `[OperationContract]` a `[OperationContractAttribute]` . V každém případě je původní zkratka pro druhý.  
  
 Další informace o kontraktech služeb najdete v tématu [Navrhování kontraktů služeb](../designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Vytvoření kontraktu Windows Communication Foundation s třídou  
  
1. Vytvořte novou třídu pomocí Visual Basic, jazyka C# nebo jakéhokoli jiného jazyka Common Language Runtime.  
  
2. Použijte <xref:System.ServiceModel.ServiceContractAttribute> třídu pro třídu.  
  
3. Vytvořte metody ve třídě.  
  
4. Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každou metodu, která musí být vystavena jako součást veřejné smlouvy WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> použitou třídu, používají ve výchozím nastavení vzor zprávy požadavek-odpověď. Další informace o tomto vzoru zprávy najdete v tématu [Postupy: Vytvoření kontraktu požadavku a odpovědi](how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít jiné vzorce zprávy nastavením vlastností atributu. Další příklady naleznete v tématu [Postupy: vytvoření jednosměrného kontraktu](how-to-create-a-one-way-contract.md) a [Postup: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
