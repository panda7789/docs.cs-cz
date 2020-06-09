---
title: 'Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 9aebe6d8cc82c454161daead49b55f02a1cca4a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598941"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování
Windows Communication Foundation (WCF) poskytuje několik režimů, podle kterých se klienti a služby ověřují mezi sebou. Prvky vazby zabezpečení pro tyto režimy ověřování lze vytvořit pomocí statických metod pro <xref:System.ServiceModel.Channels.SecurityBindingElement> třídu nebo prostřednictvím konfigurace, jak je znázorněno v následujícím příkladu.  
  
 Další informace o režimech 18 ověřování najdete v tématu [režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje metody pro vytváření vazeb pro různé režimy ověřování.  
  
> [!NOTE]
> Po vytvoření instance objektu je <xref:System.ServiceModel.Channels.SecurityBindingElement> počet vlastností neměnný, například <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> a <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> . Volání `set` těchto vlastností je nemění.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Režimy ověřování SecurityBindingElement](securitybindingelement-authentication-modes.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
