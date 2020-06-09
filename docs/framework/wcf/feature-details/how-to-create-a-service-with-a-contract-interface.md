---
title: 'Postupy: Vytvoření služby pomocí rozhraní kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: c7d4bce174790b97db6b95aa5d15af455f261f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597160"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a>Postupy: Vytvoření služby pomocí rozhraní kontraktu
Upřednostňovaný způsob, jak vytvořit kontrakt Windows Communication Foundation (WCF), je pomocí rozhraní. Tato smlouva určuje kolekci a strukturu zpráv potřebných pro přístup k operacím, které služba nabízí. Toto rozhraní definuje vstupní a výstupní typy tím, že použije <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní a <xref:System.ServiceModel.OperationContractAttribute> třídu na metody, které chcete zveřejnit.  
  
 Další informace o kontraktech služeb najdete v tématu [Navrhování kontraktů služeb](../designing-service-contracts.md).  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a>Vytvoření kontraktu WCF s rozhraním  
  
1. Vytvořte nové rozhraní pomocí Visual Basic, C# nebo jakéhokoli jiného jazyka modulu CLR (Common Language Runtime).  
  
2. Použijte <xref:System.ServiceModel.ServiceContractAttribute> třídu na rozhraní.  
  
3. Definujte metody v rozhraní.  
  
4. Použijte <xref:System.ServiceModel.OperationContractAttribute> třídu pro každou metodu, která musí být vystavena jako součást veřejné smlouvy WCF.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje rozhraní, které definuje kontrakt služby.  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 Metody, které mají <xref:System.ServiceModel.OperationContractAttribute> použitou třídu, používají ve výchozím nastavení vzor zprávy požadavek-odpověď. Další informace o tomto vzoru zprávy najdete v tématu [Postupy: Vytvoření kontraktu požadavku a odpovědi](how-to-create-a-request-reply-contract.md). Můžete také vytvořit a použít jiné vzorce zprávy nastavením vlastností atributu. Další příklady naleznete v tématu [Postupy: vytvoření jednosměrného kontraktu](how-to-create-a-one-way-contract.md) a [Postup: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
