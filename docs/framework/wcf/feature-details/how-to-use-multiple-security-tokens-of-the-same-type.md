---
title: "Postupy: použití více tokeny zabezpečení stejného typu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f30fa563445a5399a4cb11064d85b2ad2cefcee
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Postupy: použití více tokeny zabezpečení stejného typu
-   V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, klienta zprávy pouze obsahují jeden token daného typu. Nyní zprávy klienta může obsahovat více tokeny typu. Toto téma ukazuje, jak chcete zahrnout do zpráv klienta více tokeny stejného typu.  
  
-   Všimněte si, že nemůžete nakonfigurovat službu tímto způsobem: služby může obsahovat jenom jeden token podpory.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Použití více tokeny zabezpečení stejného typu  
  
1.  Vytvořte kolekci elementů vazby prázdný vyplnit.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> voláním <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Vytvoření <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekce.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  Tokeny SAML přidáte do kolekce.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Přidání do kolekce <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Prvky vazeb přidáte do kolekce elementů vazby.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Vrátí novou vlastní vazby vytvořené z kolekce elementů vazby.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Příklad  
 Níže je celý metody popsané předchozím postupu.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a>Viz také  
 [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
