---
title: 'Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968452"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu
V tomto tématu se dozvíte o základních krocích k vytvoření kontraktu dat pomocí třídy nebo struktury. Další informace o kontraktech dat a způsobu jejich použití najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Kurz, který vás provede kroky pro vytvoření služby a klienta základní Windows Communication Foundation (WCF), najdete v [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md). Pracovní ukázkovou aplikaci, která se skládá ze základní služby a klienta, najdete v tématu [Základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Vytvoření základního kontraktu dat pro třídu nebo strukturu  
  
1. Deklaruje, že typ obsahuje kontrakt dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu na třídu. Všimněte si, že všechny veřejné typy, včetně těch, které jsou bez atributů, jsou serializovatelný. Odvodí kontrakt dat, <xref:System.Runtime.Serialization.DataContractAttribute> Pokud chybí atribut. <xref:System.Runtime.Serialization.DataContractSerializer> Další informace naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Definujte členy (vlastnosti, pole nebo události), které jsou serializovány <xref:System.Runtime.Serialization.DataMemberAttribute> použitím atributu pro každý člen. Tito členové se nazývají datové členy. Ve výchozím nastavení jsou všechny veřejné typy serializovatelný. Další informace naleznete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    > Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na soukromá pole, což způsobí, že budou data zveřejněna ostatním. Ujistěte se, že člen neobsahuje citlivá data.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit kontrakt dat pro `Person` typ <xref:System.Runtime.Serialization.DataContractAttribute> použitím atributů a <xref:System.Runtime.Serialization.DataMemberAttribute> pro třídu a její členy.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
