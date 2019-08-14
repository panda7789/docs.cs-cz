---
title: 'Postupy: Vytvoření duplexní federované vazby'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972062"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Postupy: Vytvoření duplexní federované vazby

<xref:System.ServiceModel.WSFederationHttpBinding>podporuje pouze kontrakty pro výměnu zpráv datagram a Request/Reply. Pokud chcete použít oboustrannou smlouvu výměny zpráv, musíte vytvořit vlastní vazbu. Následující postupy ukazují, jak to provést v konfiguraci, použití zabezpečení režimu zprávy pro přenosy HTTP a TCP a použití smíšeného režimu zabezpečení pro přenos TCP. Vzorový kód zobrazující všechny 3 vazby jsou na konci tohoto tématu.

Vazbu můžete vytvořit také v kódu. Popis prvků vazby, které se mají vytvořit, najdete v tématu [How to: Vytvořte vlastní vazbu pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Vytvoření duplexní federované vlastní vazby pomocí protokolu HTTP

1. V uzlu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vazby > konfiguračního souboru vytvořte prvek > CustomBinding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. `name` `FederationDuplexHttpMessageSecurityBinding` [ Uvnitř\<prvkuCustomBinding > vytvořte vazbu >](../../../../docs/framework/misc/binding.md) elementu s atributem nastaveným na. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. Uvnitř elementu > `authenticationMode` `SecureConversation`vazbyvytvořteprvek [zabezpečení > s atributem nastaveným na. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)

4. `IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Uvnitř\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpečenívytvořteprvek>secureConversationBootstrapsatributem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) nastaveným na nebo.

5. Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) [> zabezpečenívytvořteprázdný>elementcompositeDuplex.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

6. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) [ PocompositeDuplex>elementuvytvořteprázdný>elementoneWay.\<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)

7. Po elementu [> oneWayvytvořteprázdnýelement>HttpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Vytvoření duplexní federované vlastní vazby pomocí režimu zabezpečení zprávy TCP

1. V uzlu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vazby > konfiguračního souboru vytvořte prvek > CustomBinding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. `name` `FederationDuplexTcpMessageSecurityBinding` [ Uvnitř\<prvkuCustomBinding > vytvořte vazbu >](../../../../docs/framework/misc/binding.md) elementu s atributem nastaveným na. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. Uvnitř elementu > `authenticationMode` `SecureConversation`vazbyvytvořteprvek [zabezpečení > s atributem nastaveným na. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)

4. `IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Uvnitř\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpečenívytvořteprvek>secureConversationBootstrapsatributem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) nastaveným na nebo.

5. Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) [> zabezpečenívytvořteprázdný>elementtcpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Vytvoření duplexní federované vlastní vazby se smíšeným režimem zabezpečení TCP

1. V uzlu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vazby > konfiguračního souboru vytvořte prvek > CustomBinding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ Uvnitř\<prvkuCustomBinding > vytvořte vazbu >](../../../../docs/framework/misc/binding.md) elementu s atributem nastaveným na. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

3. Uvnitř elementu > `authenticationMode` `SecureConversation`vazbyvytvořteprvek [zabezpečení > s atributem nastaveným na. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)

4. `IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Uvnitř\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpečenívytvořteprvek>secureConversationBootstrapsatributem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) nastaveným na nebo.

5. Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) [> zabezpečenívytvořteprázdný>elementsslStreamSecurity.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)

6. Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) sslStreamSecurity > Vytvořte prázdný tcpTransport prvek >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

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
