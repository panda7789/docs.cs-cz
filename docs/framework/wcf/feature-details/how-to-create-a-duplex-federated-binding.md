---
title: 'Postupy: Vytvoření duplexní federované vazby'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141716"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Postupy: Vytvoření duplexní federované vazby

<xref:System.ServiceModel.WSFederationHttpBinding> podporuje jenom kontrakty datagramu a žádosti nebo odpovědi na zprávy o výměně. Pokud chcete použít oboustrannou smlouvu výměny zpráv, musíte vytvořit vlastní vazbu. Následující postupy ukazují, jak to provést v konfiguraci, použití zabezpečení režimu zprávy pro přenosy HTTP a TCP a použití smíšeného režimu zabezpečení pro přenos TCP. Vzorový kód zobrazující všechny 3 vazby jsou na konci tohoto tématu.

Vazbu můžete vytvořit také v kódu. Popis prvků vazby, které se mají vytvořit, naleznete v tématu [How to: Create a Custom Binding using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Vytvoření duplexní federované vlastní vazby pomocí protokolu HTTP

1. V uzlu [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru vytvořte prvek [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Uvnitř [\<elementu > CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vytvořte [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) element s atributem `name` nastaveným na `FederationDuplexHttpMessageSecurityBinding`.

3. Uvnitř [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<element zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) s atributem `authenticationMode` nastaveným na `SecureConversation`.

4. Uvnitř prvku [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prvek [\<secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) s atributem `authenticationMode` nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.

5. Po elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prázdný prvek [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) .

6. Po [\<elementu > compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vytvořte prázdný prvek [\<oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) .

7. Po [\<prvku > oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vytvořte prázdný [\<](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Vytvoření duplexní federované vlastní vazby pomocí režimu zabezpečení zprávy TCP

1. V uzlu [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru vytvořte prvek [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Uvnitř [\<elementu > CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vytvořte [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) element s atributem `name` nastaveným na `FederationDuplexTcpMessageSecurityBinding`.

3. Uvnitř [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<element zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) s atributem `authenticationMode` nastaveným na `SecureConversation`.

4. Uvnitř prvku [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prvek [\<secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) s atributem `authenticationMode` nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.

5. Po elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prázdný prvek [\<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Vytvoření duplexní federované vlastní vazby se smíšeným režimem zabezpečení TCP

1. V uzlu [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru vytvořte prvek [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Uvnitř [\<elementu > CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vytvořte [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) element s atributem `name` nastaveným na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.

3. Uvnitř [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<element zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) s atributem `authenticationMode` nastaveným na `SecureConversation`.

4. Uvnitř prvku [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prvek [\<secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) s atributem `authenticationMode` nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.

5. Po elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prázdný prvek [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) .

6. Po [\<elementu > sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vytvořte prázdný prvek [\<tcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .

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
