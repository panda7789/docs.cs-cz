---
title: 'Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1ad69393-3915-4e7f-9b91-b6fc59c6f5ba
ms.openlocfilehash: 2cd757107d9f62ce749d98db1d4968c02a09c5d2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988752"
---
# <a name="how-to-create-a-windows-communication-foundation-contract-with-a-class"></a>Postupy: Vytvoření kontraktu Windows Communication Foundation s třídou
Upřednostňovaným způsobem vytvoření kontraktu Windows Communication Foundation (WCF) je použití rozhraní. Další informace najdete v tématu [jak: Definujte kontrakt](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)služby. Alternativa, která je zde uvedená, je vytvořit třídu a potom použít <xref:System.ServiceModel.ServiceContractAttribute> atribut přímo pro třídu <xref:System.ServiceModel.OperationContractAttribute> a atribut pro každou metodu ve třídě, která je součástí kontraktu.  
  
> [!WARNING]
> `[ServiceContract]`a `[ServiceContractAttribute]` udělejte stejné věci. Totéž platí pro `[OperationContract]` a `[OperationContractAttribute]`. V každém případě je původní zkratka pro druhý.  
  
 Další informace o kontraktech služeb najdete v tématu [Navrhování kontraktů služeb](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
### <a name="creating-a-windows-communication-foundation-contract-with-a-class"></a>Vytvoření kontraktu Windows Communication Foundation s třídou  
  
1. Vytvořte novou třídu pomocí Visual Basic, C#nebo jakéhokoli jiného jazyka Common Language Runtime.  
  
2. <xref:System.ServiceModel.ServiceContractAttribute> Použijte třídu pro třídu.  
  
3. Vytvořte metody ve třídě.  
  
4. <xref:System.ServiceModel.OperationContractAttribute> Použijte třídu pro každou metodu, která musí být vystavena jako součást veřejné smlouvy WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje třídu, která definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithclass/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithclass/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> použitou třídu, používají ve výchozím nastavení vzor zprávy požadavek-odpověď. Další informace o tomto vzoru zprávy naleznete v tématu [How to: Vytvoření kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)požadavku a odpovědi. Můžete také vytvořit a použít jiné vzorce zprávy nastavením vlastností atributu. Další příklady naleznete v tématu [How to: Vytvoření jednosměrného kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md) a [postupy: Vytvoří oboustranný kontrakt](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
