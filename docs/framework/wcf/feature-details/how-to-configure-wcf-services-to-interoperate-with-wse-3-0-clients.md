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
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="e7b1b-102">Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="e7b1b-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="e7b1b-103">Služby Windows Communication Foundation (WCF) jsou kompatibilní s rozšířeními webových služeb 3,0 pro klienty Microsoft .NET (WSE), když jsou služby WCF nakonfigurované na použití verze standardu WS-Addressing ze srpna 2004.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="e7b1b-104">Umožnění spolupráce služby WCF s klienty WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="e7b1b-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="e7b1b-105">Definujte vlastní vazbu pro službu WCF.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="e7b1b-106">Chcete-li určit, že verze specifikace WS-Addressing ve verzi ze srpna 2004 se používá pro kódování zprávy, musí být vytvořena vlastní vazba.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="e7b1b-107">Přidejte podřízené [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ >CustomBindingdovazeb>konfiguračníhosouboruslužby.\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e7b1b-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="e7b1b-108">Zadejte název vazby přidáním `name` [ \<vazby](../../../../docs/framework/misc/binding.md) [ \<> k CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) a nastavením atributu.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="e7b1b-109">Zadejte režim ověřování a verzi specifikací WS-Security, které se používají k zabezpečení zpráv kompatibilních s WSE 3,0 přidáním podřízeného [ \<](../../../../docs/framework/misc/binding.md) [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) do > vazby.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>

        <span data-ttu-id="e7b1b-110">Chcete-li nastavit režim ověřování, nastavte `authenticationMode` atribut [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e7b1b-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="e7b1b-111">Režim ověřování je zhruba stejný jako kontrolní výraz zabezpečení klíč v WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="e7b1b-112">Následující tabulka mapuje režimy ověřování ve službě WCF na klíč kontrolní výrazy zabezpečení v WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="e7b1b-113">Režim ověřování WCF</span><span class="sxs-lookup"><span data-stu-id="e7b1b-113">WCF Authentication Mode</span></span>|<span data-ttu-id="e7b1b-114">Kontrolní výraz zabezpečení WSE 3,0 klíč</span><span class="sxs-lookup"><span data-stu-id="e7b1b-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="e7b1b-115">\*Jednou z hlavních rozdílů mezi `mutualCertificate10Security` kontrolními výrazy zabezpečení a `mutualCertificate11Security` klíč je verze specifikace WS-Security, kterou WSE používá k zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="e7b1b-116">V případě se používá WS-Security 1,0, zatímco pro `mutualCertificate11Security`je použito WS-Security 1,1. `mutualCertificate10Security`</span><span class="sxs-lookup"><span data-stu-id="e7b1b-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="e7b1b-117">V případě WCF je verze specifikace WS-Security určena v `messageSecurityVersion` atributu [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e7b1b-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="e7b1b-118">Chcete-li nastavit verzi specifikace WS-Security, která je použita k zabezpečení zpráv protokolu SOAP, nastavte `messageSecurityVersion` atribut [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="e7b1b-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="e7b1b-119">Pro spolupráci s WSE 3,0 nastavte hodnotu `messageSecurityVersion` atributu na. <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A></span><span class="sxs-lookup"><span data-stu-id="e7b1b-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="e7b1b-120">Určete, že služba WCF používá verzi ze srpna 2004 specifikace WS-Addressing přidáním [ \<> textMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) a nastavením `messageVersion` na hodnotu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="e7b1b-121">Pokud používáte SOAP 1,2, nastavte `messageVersion` atribut na. <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A></span><span class="sxs-lookup"><span data-stu-id="e7b1b-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="e7b1b-122">Určete, že služba používá vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="e7b1b-123">`binding` Nastavte `customBinding` [atribut \<koncového bodu >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu na.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="e7b1b-124">`bindingConfiguration` Nastavte `name` [atribut \<koncového bodu >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) elementu [ na\<](../../../../docs/framework/misc/binding.md) hodnotu zadanou v atributu > vazby pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="e7b1b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7b1b-125">Example</span></span>

<span data-ttu-id="e7b1b-126">Následující příklad kódu určuje, že `Service.HelloWorldService` používá vlastní vazbu pro spolupráci s klienty WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="e7b1b-127">Vlastní vazba určuje, že verze 2004 protokolu WS-Addressing a WS-Security 1,1 sady specifikací slouží ke kódování vyměňovaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="e7b1b-128">Zprávy jsou zabezpečeny pomocí <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> režimu ověřování.</span><span class="sxs-lookup"><span data-stu-id="e7b1b-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e7b1b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7b1b-129">See also</span></span>

- [<span data-ttu-id="e7b1b-130">Postupy: Přizpůsobení systémem poskytované vazby</span><span class="sxs-lookup"><span data-stu-id="e7b1b-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
