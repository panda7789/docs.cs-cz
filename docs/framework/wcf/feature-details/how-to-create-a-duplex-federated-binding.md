---
title: 'Postupy: Vytvoření duplexní federované vazby'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598967"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Postupy: Vytvoření duplexní federované vazby

<xref:System.ServiceModel.WSFederationHttpBinding>podporuje pouze kontrakty pro výměnu zpráv datagram a Request/Reply. Pokud chcete použít oboustrannou smlouvu výměny zpráv, musíte vytvořit vlastní vazbu. Následující postupy ukazují, jak to provést v konfiguraci, použití zabezpečení režimu zprávy pro přenosy HTTP a TCP a použití smíšeného režimu zabezpečení pro přenos TCP. Vzorový kód zobrazující všechny 3 vazby jsou na konci tohoto tématu.

Vazbu můžete vytvořit také v kódu. Popis prvků vazby, které se mají vytvořit, naleznete v tématu [How to: Create a Custom Binding using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Vytvoření duplexní federované vlastní vazby pomocí protokolu HTTP

1. V [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) uzlu konfiguračního souboru vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.

2. Uvnitř [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element s `name` atributem nastaveným na `FederationDuplexHttpMessageSecurityBinding` .

3. Uvnitř [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atributem nastaveným na `SecureConversation` .

4. Uvnitř [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atributem nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated` .

5. Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte prázdný [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.

6. Po [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) elementu vytvořte prázdný [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.

7. Po [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) elementu vytvořte prázdný [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Vytvoření duplexní federované vlastní vazby pomocí režimu zabezpečení zprávy TCP

1. V [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) uzlu konfiguračního souboru vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.

2. Uvnitř [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element s `name` atributem nastaveným na `FederationDuplexTcpMessageSecurityBinding` .

3. Uvnitř [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atributem nastaveným na `SecureConversation` .

4. Uvnitř [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atributem nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated` .

5. Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte prázdný [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Vytvoření duplexní federované vlastní vazby se smíšeným režimem zabezpečení TCP

1. V [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) uzlu konfiguračního souboru vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.

2. Uvnitř [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element s `name` atributem nastaveným na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .

3. Uvnitř [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atributem nastaveným na `SecureConversation` .

4. Uvnitř [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atributem nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated` .

5. Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte prázdný [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.

6. Po [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu vytvořte prázdný [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.

## <a name="code-sample"></a>Ukázka kódu

### <a name="sample-with-3-bindings"></a>Ukázka se 3 vazbami

1. Do konfiguračního souboru vložte následující kód.

## <a name="example"></a>Příklad

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
