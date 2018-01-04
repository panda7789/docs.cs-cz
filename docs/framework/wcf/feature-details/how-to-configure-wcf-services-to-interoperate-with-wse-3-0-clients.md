---
title: "Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c93b91123c7622bea125bfa702c53a697b1ac84c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Služba je úroveň kompatibilní s 3.0 vylepšení webové služby pro klienty Microsoft .NET (WSE) při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby jsou nakonfigurovány pro použití srpen 2004 verze specifikace WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Chcete-li povolit služby WCF pro spolupráci s klienty WSE 3.0  
  
1.  Definovat vlastní vazby pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
     Chcete-li určit, že srpen 2004 verzi specifikace WS-Addressing se používá pro kódování zpráv, je třeba vytvořit vlastní vazby.  
  
    1.  Přidat podřízenou [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) k [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru služby.  
  
    2.  Zadejte název pro vazbu, přidáním [ \<vazby >](../../../../docs/framework/misc/binding.md) k [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a nastavení `name` atribut.  
  
    3.  Zadejte režim ověřování a verzi specifikace WS-zabezpečení, které se používají k zabezpečení zpráv, které jsou kompatibilní s WSE 3.0 přidáním podřízenou [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) k [ \<vazby >](../../../../docs/framework/misc/binding.md).  
  
         Režim ověřování, nastavit `authenicationMode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Režim ověřování je přibližně ekvivalentem připraveného security assertion ve WSE 3.0. Následující tabulka mapuje režimy ověřování ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do připraveného zabezpečení kontrolní výrazy ve WSE 3.0.  
  
        |Režim ověřování WCF|Kontrolní výraz připraveného zabezpečení WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \*Jeden z hlavních rozdílů mezi `mutualCertificate10Security` a `mutualCertificate11Security` kontrolní výrazy připraveného zabezpečení je verzi specifikace WS-zabezpečení, která WSE používá k zabezpečení protokolu SOAP zprávy. Pro `mutualCertificate10Security`, WS-Security 1.0 se používá, zatímco 1.1 WS-zabezpečení se používá pro `mutualCertificate11Security`. Pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], verzi specifikace WS-Security je uveden v `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Verze specifikaci WS-zabezpečení, která se používá k zabezpečení protokolu SOAP zprávy, nastavit `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Chcete-li zajistit vzájemnou funkční spolupráci s WSE 3.0, nastavte hodnotu `messageSecurityVersion` atribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Zadejte, že je používán. srpna 2004 verzi specifikace WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přidáním [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) a nastavte `messageVersion` jeho hodnotou, čímž <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
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
