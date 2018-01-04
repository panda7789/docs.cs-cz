---
title: "Postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6241df0fd5a0b6ee532691eee2279f618be25a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu
Toto téma ukazuje základní kroky pro vytvoření kontraktu dat pomocí třídu nebo strukturu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]měnící data a jak se používají, najdete v části [pomocí kontrakty dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Kurz, který vás provede kroky k vytvoření základního [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby a klienta, najdete v článku [kurzu Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md). Pracovní ukázkovou aplikaci, která se skládá z klienta a služby na úrovni basic, najdete v části [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>K vytvoření kontraktu základní data pro třídu nebo strukturu  
  
1.  Deklarovat, zda má tento typ kontraktu dat s použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut třídy. Upozorňujeme, že jsou všechny veřejné typy, včetně těch bez atributy, serializable. <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat, pokud <xref:System.Runtime.Serialization.DataContractAttribute> chybí atribut. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Definování členů (vlastnosti, pole nebo události), které jsou serializovány použitím <xref:System.Runtime.Serialization.DataMemberAttribute> atribut pro každého člena. Tito členové se nazývají datových členů. Všechny veřejné typy jsou ve výchozím nastavení, serializable. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut privátním polím, způsobuje data, která mají být zpřístupněny ostatním uživatelům. Ujistěte se, zda člen neobsahuje citlivá data.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje postup vytvoření kontraktu dat pro `Person` typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy třídy a její členy.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Kurz Začínáme](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)
