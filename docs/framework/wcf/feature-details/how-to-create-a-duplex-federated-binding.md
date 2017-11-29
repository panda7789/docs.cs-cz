---
title: "Postupy: Vytvoření duplexní federované vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a682b84a90e64e0242a3490986cb526c7f028b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Postupy: Vytvoření duplexní federované vazby
<xref:System.ServiceModel.WSFederationHttpBinding>podporuje pouze kontrakty zpráv exchange datagram a požadavek nebo odpověď. Pokud chcete použít exchange kontrakt duplexní zprávy, musíte vytvořit vlastní vazby. Následující postupy ukazují, jak to udělat v konfiguraci, pomocí režimu zabezpečení zpráv pro přenosy protokolu HTTP a TCP a používá zabezpečení ve smíšeném režimu pro přenos TCP. Ukázkový kód zobrazuje všechny 3 vazby je na konci tohoto tématu.  
  
 Můžete také vytvořit vazby v kódu. Popis zásobníku elementů vazby k vytvoření najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>K vytvoření duplexní federované vlastní vazby s protokolem HTTP  
  
1.  V [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) vytvořit uzel konfiguračního souboru [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.  
  
2.  Uvnitř [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element s `name` atribut nastaven na `FederationDuplexHttpMessageSecurityBinding`.  
  
3.  Uvnitř [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, vytvoření [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atribut nastaven na `SecureConversation`.  
  
4.  Uvnitř [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvoření [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atribut nastaven na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.  
  
5.  Následující [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvořte prázdnou [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.  
  
6.  Následující [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu, vytvořte prázdnou [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.  
  
7.  Následující [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu, vytvořte prázdnou [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>K vytvoření duplexní federované vlastní vazby s režimem zabezpečení zpráv TCP  
  
1.  V [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) vytvořit uzel konfiguračního souboru [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.   
  
2.  Uvnitř [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element s `name` atribut nastaven na `FederationDuplexTcpMessageSecurityBinding`.  
  
3.  Uvnitř [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, vytvoření [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atribut nastaven na `SecureConversation`.  
  
4.  Uvnitř [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvoření [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atribut nastaven na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.  
  
5.  Následující [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvořte prázdnou [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Chcete-li vytvořit duplexní režim federovaný vlastní vazby s TCP zabezpečení smíšený režim  
  
1.  V [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) vytvořit uzel konfiguračního souboru [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.   
  
2.  Uvnitř [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element s `name` atribut nastaven na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3.  Uvnitř [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, vytvoření [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atribut nastaven na `SecureConversation`.  
  
4.  Uvnitř [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvoření [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atribut nastaven na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.  
  
5.  Následující [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvořte prázdnou [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.  
  
6.  Následující [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu, vytvořte prázdnou [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.  
  
## <a name="code-sample"></a>Ukázka kódu  
  
#### <a name="sample-with-3-bindings"></a>Ukázka s 3 vazby  
  
1.  Vložte následující kód do konfiguračního souboru.  
  
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
