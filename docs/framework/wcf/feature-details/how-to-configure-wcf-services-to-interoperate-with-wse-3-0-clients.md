---
title: 'Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 0349c9ba76b3f240bf98daa0e095b415bc98a87c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045940"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0

Služby Windows Communication Foundation (WCF) jsou kompatibilní s rozšířeními webových služeb 3,0 pro klienty Microsoft .NET (WSE), když jsou služby WCF nakonfigurované na použití verze standardu WS-Addressing ze srpna 2004.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Umožnění spolupráce služby WCF s klienty WSE 3,0

1. Definujte vlastní vazbu pro službu WCF.

    Chcete-li určit, že verze specifikace WS-Addressing ve verzi ze srpna 2004 se používá pro kódování zprávy, musí být vytvořena vlastní vazba.

    1. Přidejte podřízené [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ >CustomBindingdovazeb>konfiguračníhosouboruslužby.\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

    2. Zadejte název vazby přidáním `name` [ \<vazby](../../../../docs/framework/misc/binding.md) [ \<> k CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a nastavením atributu.

    3. Zadejte režim ověřování a verzi specifikací WS-Security, které se používají k zabezpečení zpráv kompatibilních s WSE 3,0 přidáním podřízeného [ \<](../../../../docs/framework/misc/binding.md) [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do > vazby.

        Chcete-li nastavit režim ověřování, nastavte `authenticationMode` atribut [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Režim ověřování je zhruba stejný jako kontrolní výraz zabezpečení klíč v WSE 3,0. Následující tabulka mapuje režimy ověřování ve službě WCF na klíč kontrolní výrazy zabezpečení v WSE 3,0.

        |Režim ověřování WCF|Kontrolní výraz zabezpečení WSE 3,0 klíč|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*Jednou z hlavních rozdílů mezi `mutualCertificate10Security` kontrolními výrazy zabezpečení a `mutualCertificate11Security` klíč je verze specifikace WS-Security, kterou WSE používá k zabezpečení zpráv SOAP. V případě se používá WS-Security 1,0, zatímco pro `mutualCertificate11Security`je použito WS-Security 1,1. `mutualCertificate10Security` V případě WCF je verze specifikace WS-Security určena v `messageSecurityVersion` atributu [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).

        Chcete-li nastavit verzi specifikace WS-Security, která je použita k zabezpečení zpráv protokolu SOAP, nastavte `messageSecurityVersion` atribut [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Pro spolupráci s WSE 3,0 nastavte hodnotu `messageSecurityVersion` atributu na. <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>

    4. Určete, že služba WCF používá verzi ze srpna 2004 specifikace WS-Addressing přidáním [ \<> textMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) a nastavením `messageVersion` na hodnotu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.

        > [!NOTE]
        > Pokud používáte SOAP 1,2, nastavte `messageVersion` atribut na. <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>

2. Určete, že služba používá vlastní vazbu.

    1. `binding` Nastavte `customBinding` [atribut \<koncového bodu >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu na.

    2. `bindingConfiguration` Nastavte `name` [atribut \<koncového bodu >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu [ na\<](../../../../docs/framework/misc/binding.md) hodnotu zadanou v atributu > vazby pro vlastní vazbu.

## <a name="example"></a>Příklad

Následující příklad kódu určuje, že `Service.HelloWorldService` používá vlastní vazbu pro spolupráci s klienty WSE 3,0. Vlastní vazba určuje, že verze 2004 protokolu WS-Addressing a WS-Security 1,1 sady specifikací slouží ke kódování vyměňovaných zpráv. Zprávy jsou zabezpečeny pomocí <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> režimu ověřování.

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Postupy: Přizpůsobení systémem poskytované vazby](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
