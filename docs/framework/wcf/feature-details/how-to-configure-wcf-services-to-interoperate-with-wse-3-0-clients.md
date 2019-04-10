---
title: 'Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 8f4407f66095f97a213d6cd987b4bd9a3ed340fa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303892"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0
Služby Windows Communication Foundation (WCF) jsou přenosový kompatibilní s 3.0 rozšíření webové služby pro klienty Microsoft .NET (Najít), když služby WCF, které jsou nakonfigurovány pro použití verzi specifikace WS-Addressing ze srpna 2004.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Povolení služby WCF pro spolupráci s klienty WSE 3.0  
  
1. Definujte vlastní vazbu pro službu WCF.  
  
     Chcete-li určit, že je pro kódování zpráv používá verzi ze srpna 2004 specifikace WS-Addressing, musí být vytvořený vlastní vazby.  
  
    1.  Přidat podřízený prvek [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) k [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru služby.  
  
    2.  Zadejte název pro vazbu, tak, že přidáte [ \<vazby >](../../../../docs/framework/misc/binding.md) k [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a nastavení `name` atribut.  
  
    3.  Zadejte režim ověřování a verzi specifikace WS-Security, které se používají k zabezpečení zprávy, které jsou kompatibilní s WSE 3.0, tak, že přidáte podřízený [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) k [ \<vazby >](../../../../docs/framework/misc/binding.md).  
  
         Chcete-li nastavit režim ověřování, nastavte `authenicationMode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Režim ověřování je zhruba ekvivalentní kontrolní výraz na klíč zabezpečení ve službě WSE 3.0. Následující tabulka mapuje na klíč zabezpečení kontrolní výrazy ve WSE 3.0 režimy ověřování ve službě WCF.  
  
        |Režim ověřování WCF|Kontrolní výraz WSE 3.0 na klíč zabezpečení|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* Jeden z hlavních rozdílů mezi `mutualCertificate10Security` a `mutualCertificate11Security` kontrolní výrazy na klíč zabezpečení je verze příslušné specifikaci WS-Security WSE používá k zabezpečení zprávy protokolu SOAP. Pro `mutualCertificate10Security`, se používá WS-Security 1.0, zatímco WS-Security 1.1 se používá pro `mutualCertificate11Security`. Pro službu WCF, je podle verze specifikaci WS-Security `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Chcete-li nastavit verzi specifikace WS-Security, který se používá k zabezpečení zprávy protokolu SOAP, nastavte `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Pro spolupráci s WSE 3.0, nastavte hodnotu `messageSecurityVersion` atribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Určit, že WCF používá verzi specifikace WS-Addressing ze srpna 2004 tak, že přidáte [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) a nastavit `messageVersion` na jeho hodnotu a <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  Při použití protokolu SOAP 1.2, nastavte `messageVersion` atribut <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2. Zadejte, že služba používá vlastní vazby.  
  
    1.  Nastavte `binding` atribut [ \<koncový bod >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu `customBinding`.  
  
    2.  Nastavte `bindingConfiguration` atribut [ \<koncový bod >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) prvku na hodnotu zadanou v `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) pro vlastní Vytvoření vazby.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje, že `Service.HelloWorldService` používá vlastní vazby pro spolupráci s klienty WSE 3.0. Vlastní vazby Určuje, že verzi elementu WS-Addressing ze srpna 2004 a sadu specifikace WS-Security 1.1 se používají k výměně zpráv kódování. Zprávy jsou zabezpečené pomocí <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> režim ověřování.  
  
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

- [Postupy: Přizpůsobení vazeb poskytovaných systémem](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
