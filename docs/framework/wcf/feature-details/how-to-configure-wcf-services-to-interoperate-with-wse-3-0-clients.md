---
title: 'Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 174ecd279f9380136532ce0d5105b7a71b6d88da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0
Služby Windows Communication Foundation (WCF) jsou úroveň kompatibilní s 3.0 vylepšení webové služby pro klienty rozhraní Microsoft .NET (WSE) při služby WCF, které jsou nakonfigurovány pro použití srpen 2004 verzi specifikace WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Chcete-li povolit služby WCF pro spolupráci s klienty WSE 3.0  
  
1.  Definování vlastních vazeb pro služby WCF.  
  
     Chcete-li určit, že srpen 2004 verzi specifikace WS-Addressing se používá pro kódování zpráv, je třeba vytvořit vlastní vazby.  
  
    1.  Přidat podřízenou [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) k [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru služby.  
  
    2.  Zadejte název pro vazbu, přidáním [ \<vazby >](../../../../docs/framework/misc/binding.md) k [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a nastavení `name` atribut.  
  
    3.  Zadejte režim ověřování a verzi specifikace WS-zabezpečení, které se používají k zabezpečení zpráv, které jsou kompatibilní s WSE 3.0 přidáním podřízenou [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) k [ \<vazby >](../../../../docs/framework/misc/binding.md).  
  
         Režim ověřování, nastavit `authenicationMode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Režim ověřování je přibližně ekvivalentem připraveného security assertion ve WSE 3.0. Následující tabulka mapuje režimy ověřování ve WCF připraveného zabezpečení kontrolní výrazy ve WSE 3.0.  
  
        |Režim ověřování WCF|Kontrolní výraz připraveného zabezpečení WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \* Jeden z hlavních rozdílů mezi `mutualCertificate10Security` a `mutualCertificate11Security` kontrolní výrazy připraveného zabezpečení je verzi specifikace WS-zabezpečení, která WSE používá k zabezpečení protokolu SOAP zprávy. Pro `mutualCertificate10Security`, WS-Security 1.0 se používá, zatímco 1.1 WS-zabezpečení se používá pro `mutualCertificate11Security`. Pro WCF, verzi specifikace WS-Security je uveden v `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Verze specifikaci WS-zabezpečení, která se používá k zabezpečení protokolu SOAP zprávy, nastavit `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Chcete-li zajistit vzájemnou funkční spolupráci s WSE 3.0, nastavte hodnotu `messageSecurityVersion` atribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Určení, že je verze srpen 2004 specifikace WS-Addressing používat technologie WCF přidáním [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) a nastavte `messageVersion` jeho hodnotou, čímž <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  Při použití protokolu SOAP 1.2, nastavte `messageVersion` atribut <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Zadejte, že služba používá vlastní vazby.  
  
    1.  Nastavit `binding` atribut [ \<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element `customBinding`.  
  
    2.  Nastavit `bindingConfiguration` atribut [ \<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element z hodnoty zadané v `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) pro vlastní vazba.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje, že `Service.HelloWorldService` používá vlastní vazby pro spolupráci s klienty WSE 3.0. Vlastní vazby určí, že verze srpen 2004 adresování WS a sadu specifikace WS-zabezpečení 1.1 ke kódování výměně zpráv. Zprávy jsou zabezpečené, pomocí <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> režim ověřování.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přizpůsobení vazeb poskytovaných systémem](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
