---
title: "Postupy: Nastavení potvrzení podpisu"
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
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fced2ddd16ae244e2ea3d945082f48ffd23302e6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Postupy: Nastavení potvrzení podpisu
*Potvrzení podpisu* mechanismus pro zprávu iniciátor zajistit, že byla přijata odpověď byla vygenerována v reakci na původní zprávu o odesílatele. Potvrzení podpisu je definována ve specifikaci WS-zabezpečení 1.1. Pokud koncový bod podporuje WS-Security 1.0, nemůžete použít potvrzení podpisu.  
  
 Následující postupy, určete, jak povolit pomocí potvrzení podpisu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Můžete použít stejný postup s <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Postup staví na základní kroky, které jsou součástí [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>Chcete-li povolit potvrzení podpisu v kódu  
  
1.  Vytvořit instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy.  
  
2.  Vytvoření instance <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.  
  
3.  Nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> k `true`.  
  
4.  Přidáte element zabezpečení do kolekce vazby.  
  
5.  Vytvoření vlastní vazby, jak je uvedeno v [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>Chcete-li povolit potvrzení podpisu v konfiguraci  
  
1.  Přidat `<customBinding>` elementu, který chcete `<bindings>` oddíl konfiguračního souboru.  
  
2.  Přidat `<binding>` elementu a sadu název atributu na odpovídající hodnotu.  
  
3.  Přidáte odpovídající element kódování. Následující příklad přidá `<TextMessageEncoding>` elementu.  
  
4.  Přidat `<security>` podřízený element a sadu `requireSignatureConfirmation` atribut `true`.  
  
5.  Volitelné. Chcete-li povolit potvrzení podpisu během službou bootstrap nástroje, přidejte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element a sadu `equireSignatureConfirmation` atribut `true`.  
  
6.  Přidáte element odpovídající přenosu. Následující příklad přidá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastaví <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> vlastnost `true`. Všimněte si, že v tomto příkladu se nepoužívá `<secureConversationBootstrap>` element v předchozím příkladu. Tento příklad ukazuje potvrzení podpisu při použití tokenu systému Windows (protokol Kerberos). V takovém případě podpis klienta je vrácený v všechny odpovědi ze služby a je potvrzen klientem.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
