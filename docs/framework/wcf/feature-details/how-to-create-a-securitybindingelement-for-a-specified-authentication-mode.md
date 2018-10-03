---
title: 'Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
author: BrucePerlerMS
ms.openlocfilehash: 6204a2832bbdc0c6631903687fcd8a1c45b35d03
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036960"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování
Windows Communication Foundation (WCF) poskytuje několik režimů, které služby a klienti ověřování mezi sebou. Můžete vytvořit bezpečnostní prvky vazeb pro tyto režimy ověřování pomocí statické metody na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy nebo prostřednictvím konfigurace, jak je znázorněno v následujícím příkladu.  
  
 Další informace o režimech ověřování 18 najdete v tématu [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje metody pro vytváření vazeb v různých režimech ověřování.  
  
> [!NOTE]
>  Jednou instancí <xref:System.ServiceModel.Channels.SecurityBindingElement> je vytvořen objekt, jsou neměnné, jako například počet vlastností <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> a <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Volání `set` k takovým vlastnostem není je změnit.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
