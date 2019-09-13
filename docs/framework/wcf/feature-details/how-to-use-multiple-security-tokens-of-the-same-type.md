---
title: 'Postupy: Použití víc tokenů zabezpečení stejného typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 84009eacca113fcd83a0e4908c7d6eb0c82db7d5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928764"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Postupy: Použití víc tokenů zabezpečení stejného typu

- V .NET Framework 3,0 zpráva klienta obsahovala pouze jeden token daného typu. Nyní mohou klientské zprávy obsahovat více tokenů typu. V tomto tématu se dozvíte, jak do zprávy klienta zahrnout více tokenů stejného typu.  
  
- Upozorňujeme, že nemůžete nakonfigurovat službu tímto způsobem: služba může obsahovat jenom jeden podpůrný token.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Použití více tokenů zabezpečení stejného typu  
  
1. Vytvořte prázdnou kolekci elementů vazby, která se má naplnit.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <xref:System.ServiceModel.Channels.SecurityBindingElement> Vytvořte voláním. <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> Vytvořte kolekci.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. Přidejte do kolekce tokeny SAML.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. Přidejte kolekci do <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. Přidejte prvky vazby do kolekce elementů vazby.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. Vrátí novou vlastní vazbu vytvořenou z kolekce elementů vazby.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Příklad  
 Následuje celá metoda, kterou popisuje předchozí postup.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
