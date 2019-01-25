---
title: 'Postupy: Použití víc tokenů zabezpečení stejného typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 40fc95c905f8923b8aaf2c97fb9dc2b937dfb06f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691344"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Postupy: Použití víc tokenů zabezpečení stejného typu
-   V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, klienta zprávy pouze omezením jeden token daného typu. Zprávy klienta teď může obsahovat více tokenů typu. Toto téma ukazuje, jak zahrnout více tokenů stejného typu zprávy klienta.  
  
-   Poznámka: službu nelze nakonfigurovat tímto způsobem: Služba může obsahovat pouze jeden podpůrný token.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Použití víc tokenů zabezpečení stejného typu  
  
1.  Vytvořte kolekci elementů prázdný vazby který se má naplnit.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Vytvoření <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekce.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  Tokeny SAML přidáte do kolekce.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Kolekce, kterou chcete přidat <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Přidání elementů vazby do kolekce elementů vazby.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Vrátí novou vlastní vazbu vytvořené z kolekce elementů vazby.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Příklad  
 Níže je celý metody popsané v předchozím postupu.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a>Viz také:
- [Architektura zabezpečení](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
