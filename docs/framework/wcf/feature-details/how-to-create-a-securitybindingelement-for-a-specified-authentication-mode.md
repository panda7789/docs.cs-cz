---
title: "Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování"
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
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 29cbe3c10ac68d508dc22781e46a6041f2d7eab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje několik režimy, které služby a klienti ověřování jednu na druhou. Můžete vytvořit bezpečnostní prvky vazeb pro tyto režimy ověřování pomocí statické metody na <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy nebo prostřednictvím konfigurace, jak je znázorněno v následujícím příkladu.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]režimy 18 ověřování, najdete v části [režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje metody pro vytvoření vazby v různých režimech ověřování.  
  
> [!NOTE]
>  Jednou instance <xref:System.ServiceModel.Channels.SecurityBindingElement> je vytvořen objekt, jsou neměnné, například počet vlastností <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> a <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Volání metody `set` na tyto vlastnosti nejsou změněny.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Režimy ověřování SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
