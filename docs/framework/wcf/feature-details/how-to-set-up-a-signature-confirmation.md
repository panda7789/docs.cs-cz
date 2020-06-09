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
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586909"
---
# <a name="how-to-set-up-a-signature-confirmation"></a>Postupy: Nastavení potvrzení podpisu

*Potvrzení podpisu* je mechanismus pro iniciátora zprávy, který zajistí, že přijatá odpověď byla vygenerována v reakci na původní zprávu odesílatele. Potvrzení podpisu je definováno ve specifikaci WS-Security 1,1. Pokud koncový bod podporuje WS-Security 1,0, nemůžete použít potvrzení podpisu.

Následující postupy určují, jak povolit potvrzení podpisu pomocí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . Stejný postup můžete použít s <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Procedura je založena na základních krocích, které byly nalezeny v tématu [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-code"></a>Povolení potvrzení podpisu v kódu

1. Vytvořit instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy.

2. Vytvořte instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.

3. Nastavte na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> `true` .

4. Přidejte prvek zabezpečení do kolekce vazeb.

5. Vytvořte vlastní vazbu, jak je uvedeno v tématu [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

### <a name="to-enable-signature-confirmation-in-configuration"></a>Povolení potvrzení podpisu v konfiguraci

1. Přidejte `<customBinding>` element do `<bindings>` oddílu konfiguračního souboru.

2. Přidejte `<binding>` element a nastavte atribut Name na odpovídající hodnotu.

3. Přidejte příslušný element kódování. Následující příklad přidá `<TextMessageEncoding>` prvek.

4. Přidejte `<security>` podřízený element a nastavte `requireSignatureConfirmation` atribut na `true` .

5. Nepovinný parametr. Chcete-li povolit potvrzení podpisu při spuštění, přidejte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element a nastavte `requireSignatureConfirmation` atribut na `true` .

6. Přidejte příslušný transportní element. Následující příklad přidá [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :

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

Následující kód vytvoří instanci třídy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastaví <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> vlastnost na hodnotu `true` . Všimněte si, že tento příklad nepoužívá `<secureConversationBootstrap>` prvek zobrazený v předchozím příkladu. Tento příklad ukazuje potvrzení podpisu při použití tokenu Windows (protokolu Kerberos). V takovém případě se podpis klienta vrátí ve všech odpovědích služby a klient ho potvrdí.

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
