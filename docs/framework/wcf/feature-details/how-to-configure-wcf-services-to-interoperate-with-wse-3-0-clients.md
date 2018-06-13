---
title: 'Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 174ecd279f9380136532ce0d5105b7a71b6d88da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495106"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="b0d77-102">Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="b0d77-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>
<span data-ttu-id="b0d77-103">Služby Windows Communication Foundation (WCF) jsou úroveň kompatibilní s 3.0 vylepšení webové služby pro klienty rozhraní Microsoft .NET (WSE) při služby WCF, které jsou nakonfigurovány pro použití srpen 2004 verzi specifikace WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="b0d77-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="b0d77-104">Chcete-li povolit služby WCF pro spolupráci s klienty WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="b0d77-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>  
  
1.  <span data-ttu-id="b0d77-105">Definování vlastních vazeb pro služby WCF.</span><span class="sxs-lookup"><span data-stu-id="b0d77-105">Define a custom binding for the WCF service.</span></span>  
  
     <span data-ttu-id="b0d77-106">Chcete-li určit, že srpen 2004 verzi specifikace WS-Addressing se používá pro kódování zpráv, je třeba vytvořit vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="b0d77-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>  
  
    1.  <span data-ttu-id="b0d77-107">Přidat podřízenou [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) k [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru služby.</span><span class="sxs-lookup"><span data-stu-id="b0d77-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>  
  
    2.  <span data-ttu-id="b0d77-108">Zadejte název pro vazbu, přidáním [ \<vazby >](../../../../docs/framework/misc/binding.md) k [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a nastavení `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="b0d77-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>  
  
    3.  <span data-ttu-id="b0d77-109">Zadejte režim ověřování a verzi specifikace WS-zabezpečení, které se používají k zabezpečení zpráv, které jsou kompatibilní s WSE 3.0 přidáním podřízenou [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) k [ \<vazby >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="b0d77-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
         <span data-ttu-id="b0d77-110">Režim ověřování, nastavit `authenicationMode` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b0d77-110">To set the authentication mode, set the `authenicationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="b0d77-111">Režim ověřování je přibližně ekvivalentem připraveného security assertion ve WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="b0d77-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="b0d77-112">Následující tabulka mapuje režimy ověřování ve WCF připraveného zabezpečení kontrolní výrazy ve WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="b0d77-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>  
  
        |<span data-ttu-id="b0d77-113">Režim ověřování WCF</span><span class="sxs-lookup"><span data-stu-id="b0d77-113">WCF Authentication Mode</span></span>|<span data-ttu-id="b0d77-114">Kontrolní výraz připraveného zabezpečení WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="b0d77-114">WSE 3.0 turnkey security assertion</span></span>|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         <span data-ttu-id="b0d77-115">\* Jeden z hlavních rozdílů mezi `mutualCertificate10Security` a `mutualCertificate11Security` kontrolní výrazy připraveného zabezpečení je verzi specifikace WS-zabezpečení, která WSE používá k zabezpečení protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="b0d77-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="b0d77-116">Pro `mutualCertificate10Security`, WS-Security 1.0 se používá, zatímco 1.1 WS-zabezpečení se používá pro `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="b0d77-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="b0d77-117">Pro WCF, verzi specifikace WS-Security je uveden v `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b0d77-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="b0d77-118">Verze specifikaci WS-zabezpečení, která se používá k zabezpečení protokolu SOAP zprávy, nastavit `messageSecurityVersion` atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="b0d77-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="b0d77-119">Chcete-li zajistit vzájemnou funkční spolupráci s WSE 3.0, nastavte hodnotu `messageSecurityVersion` atribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0d77-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>  
  
    4.  <span data-ttu-id="b0d77-120">Určení, že je verze srpen 2004 specifikace WS-Addressing používat technologie WCF přidáním [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) a nastavte `messageVersion` jeho hodnotou, čímž <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0d77-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b0d77-121">Při použití protokolu SOAP 1.2, nastavte `messageVersion` atribut <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0d77-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>  
  
2.  <span data-ttu-id="b0d77-122">Zadejte, že služba používá vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="b0d77-122">Specify that the service uses the custom binding.</span></span>  
  
    1.  <span data-ttu-id="b0d77-123">Nastavit `binding` atribut [ \<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element `customBinding`.</span><span class="sxs-lookup"><span data-stu-id="b0d77-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>  
  
    2.  <span data-ttu-id="b0d77-124">Nastavit `bindingConfiguration` atribut [ \<endpoint >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element z hodnoty zadané v `name` atribut [ \<vazby >](../../../../docs/framework/misc/binding.md) pro vlastní vazba.</span><span class="sxs-lookup"><span data-stu-id="b0d77-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0d77-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0d77-125">Example</span></span>  
 <span data-ttu-id="b0d77-126">Následující příklad kódu určuje, že `Service.HelloWorldService` používá vlastní vazby pro spolupráci s klienty WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="b0d77-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="b0d77-127">Vlastní vazby určí, že verze srpen 2004 adresování WS a sadu specifikace WS-zabezpečení 1.1 ke kódování výměně zpráv.</span><span class="sxs-lookup"><span data-stu-id="b0d77-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="b0d77-128">Zprávy jsou zabezpečené, pomocí <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="b0d77-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0d77-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0d77-129">See Also</span></span>  
 [<span data-ttu-id="b0d77-130">Postupy: Přizpůsobení vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b0d77-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
