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
ms.openlocfilehash: 29105b7f3177403aacf5f8e628f2dceda4e26354
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54747866"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu
Toto téma popisuje základní kroky k vytvoření kontraktu dat pomocí třídy nebo struktury. Další informace o kontraktech dat a způsob jejich použití naleznete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Kurz vás provede kroky k vytvoření základní služby Windows Communication Foundation (WCF) a klienta, najdete v tématu [kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md). Ukázkové aplikace práci, která se skládá klienta a služby na úrovni basic, naleznete v tématu [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Vytvoření základního kontraktu dat pro třídu nebo strukturu  
  
1.  Deklarujte, že má typ kontraktu dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut třídy. Všimněte si, že všechny veřejné typy, včetně těch bez atributy, jsou serializovatelné. <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat, pokud <xref:System.Runtime.Serialization.DataContractAttribute> atribut chybí. Další informace najdete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Definování členů (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro každého člena. Tyto členy, se nazývají datové členy. Standardně jsou všechny veřejné typy serializovatelné. Další informace najdete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut k privátním položkám, způsobí data, která mají být vystaveny ostatním uživatelům. Ujistěte se, že člen neobsahuje citlivá data.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob vytvoření kontraktu dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy třídy a jejích členů.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
