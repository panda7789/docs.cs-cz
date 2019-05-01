---
title: 'Postupy: Nastavení potvrzení podpisu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 56e8720a6130d2908fbfb83bd243a54fae9a2406
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972923"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Postupy: Nastavení potvrzení podpisu
*Potvrzení podpisu* sítí je mechanismus pro iniciátor zprávy k zajištění, že byla přijata odpověď byla vygenerována v reakci na původní zprávu o odesílatele. Potvrzení podpisu je definováno ve specifikaci WS-Security 1.1. Pokud koncový bod podporuje WS-Security 1.0, nemůžete použít potvrzení podpisu.  
  
 Následující postupy, určete, jak povolit potvrzení podpisu pomocí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Můžete použít stejný postup se <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Postup staví na základních kroků v [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-code"></a>Chcete-li povolit potvrzení podpisu v kódu  
  
1. Vytvořit instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy.  
  
2. Vytvoření instance <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.  
  
3. Nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> k `true`.  
  
4. Přidáte element zabezpečení do kolekce vazby.  
  
5. Vytvoření vlastní vazby, jak je uvedeno v [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a>Chcete-li povolit potvrzení podpisu v konfiguraci  
  
1. Přidat `<customBinding>` elementu `<bindings>` oddílu konfiguračního souboru.  
  
2. Přidat `<binding>` elementu a nastavte název atributu na odpovídající hodnotu.  
  
3. Přidáte odpovídající element kódování. Následující příklad přidá `<TextMessageEncoding>` elementu.  
  
4. Přidat `<security>` podřízený element a nastavte `requireSignatureConfirmation` atribut `true`.  
  
5. Volitelné. Chcete-li povolit potvrzení podpisu během spuštění, přidejte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element a nastavte `equireSignatureConfirmation` atribut `true`.  
  
6. Přidáte element přenosu odpovídající. Následující příklad přidá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):  
  
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
 Následující kód vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastaví <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> vlastnost `true`. Všimněte si, že v tomto příkladu nepoužívá `<secureConversationBootstrap>` element je znázorněno v předchozím příkladu. Tento příklad ukazuje potvrzení podpisu při použití token Windows (protokol Kerberos). V tomto případě podpis klienta se vrátí ve všech odpovědí od služby a potvrdí klientem.  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
