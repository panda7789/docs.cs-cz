---
title: 'Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu'
description: Podle tohoto příkladu se dozvíte, jak vytvořit kontrakt dat pomocí třídy nebo struktury v technologii WCF pomocí atributu DataContractAttribute.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: a45fde58795947c3e46fa45750ae1a3faddd8849
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247166"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu
V tomto tématu se dozvíte o základních krocích k vytvoření kontraktu dat pomocí třídy nebo struktury. Další informace o kontraktech dat a způsobu jejich použití najdete v tématu [Použití kontraktů dat](using-data-contracts.md).  
  
 Kurz, který vás provede kroky pro vytvoření služby a klienta základní Windows Communication Foundation (WCF), najdete v [kurzu Začínáme](../getting-started-tutorial.md). Pracovní ukázkovou aplikaci, která se skládá ze základní služby a klienta, najdete v tématu [Základní kontrakt dat](../samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Vytvoření základního kontraktu dat pro třídu nebo strukturu  
  
1. Deklaruje, že typ obsahuje kontrakt dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu na třídu. Všimněte si, že všechny veřejné typy, včetně těch, které jsou bez atributů, jsou serializovatelný. <xref:System.Runtime.Serialization.DataContractSerializer>Odvodí kontrakt dat, pokud chybí <xref:System.Runtime.Serialization.DataContractAttribute> atribut. Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).  
  
2. Definujte členy (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atributu pro každý člen. Tito členové se nazývají datové členy. Ve výchozím nastavení jsou všechny veřejné typy serializovatelný. Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).  
  
    > [!NOTE]
    > Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut na soukromá pole, což způsobí, že budou data zveřejněna ostatním. Ujistěte se, že člen neobsahuje citlivá data.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit kontrakt dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributů a pro třídu a její členy.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Použití kontraktů dat](using-data-contracts.md)
- [Kurz Začínáme](../getting-started-tutorial.md)
- [Začínáme](../samples/getting-started-sample.md)
