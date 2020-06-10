---
title: 'Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 600b9c28d92f9e2b6e4d586b052cc5762d591521
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599058"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="2074e-102">Postupy: Konfigurace služeb WCF pro spolupráci s klienty WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="2074e-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="2074e-103">Služby Windows Communication Foundation (WCF) jsou kompatibilní s rozšířeními webových služeb 3,0 pro klienty Microsoft .NET (WSE), když jsou služby WCF nakonfigurované na použití verze standardu WS-Addressing ze srpna 2004.</span><span class="sxs-lookup"><span data-stu-id="2074e-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="2074e-104">Umožnění spolupráce služby WCF s klienty WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="2074e-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="2074e-105">Definujte vlastní vazbu pro službu WCF.</span><span class="sxs-lookup"><span data-stu-id="2074e-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="2074e-106">Chcete-li určit, že verze specifikace WS-Addressing ve verzi ze srpna 2004 se používá pro kódování zprávy, musí být vytvořena vlastní vazba.</span><span class="sxs-lookup"><span data-stu-id="2074e-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="2074e-107">Přidejte podřízenou položku [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) ke [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) konfiguračnímu souboru služby.</span><span class="sxs-lookup"><span data-stu-id="2074e-107">Add a child [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="2074e-108">Zadejte název vazby přidáním [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) do [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) a nastavením `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="2074e-108">Specify a name for the binding, by adding a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) to the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="2074e-109">Určete režim ověřování a verzi specifikací WS-Security, která se používá k zabezpečení zpráv kompatibilních s WSE 3,0 přidáním podřízeného prvku [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) do [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="2074e-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md).</span></span>

        <span data-ttu-id="2074e-110">Chcete-li nastavit režim ověřování, nastavte `authenticationMode` atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2074e-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="2074e-111">Režim ověřování je zhruba stejný jako kontrolní výraz zabezpečení klíč v WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="2074e-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="2074e-112">Následující tabulka mapuje režimy ověřování ve službě WCF na klíč kontrolní výrazy zabezpečení v WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="2074e-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="2074e-113">Režim ověřování WCF</span><span class="sxs-lookup"><span data-stu-id="2074e-113">WCF Authentication Mode</span></span>|<span data-ttu-id="2074e-114">Kontrolní výraz zabezpečení WSE 3,0 klíč</span><span class="sxs-lookup"><span data-stu-id="2074e-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="2074e-115">\*Jednou z hlavních rozdílů mezi `mutualCertificate10Security` `mutualCertificate11Security` kontrolními výrazy zabezpečení a klíč je verze specifikace WS-Security, kterou WSE používá k zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="2074e-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="2074e-116">V případě se `mutualCertificate10Security` používá WS-security 1,0, zatímco pro je použito WS-security 1,1 `mutualCertificate11Security` .</span><span class="sxs-lookup"><span data-stu-id="2074e-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="2074e-117">V případě WCF je verze specifikace WS-Security určena v `messageSecurityVersion` atributu [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2074e-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="2074e-118">Chcete-li nastavit verzi specifikace WS-Security, která je použita k zabezpečení zpráv protokolu SOAP, nastavte `messageSecurityVersion` atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2074e-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="2074e-119">Pro spolupráci s WSE 3,0 nastavte hodnotu `messageSecurityVersion` atributu na <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> .</span><span class="sxs-lookup"><span data-stu-id="2074e-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="2074e-120">Určete, že služba WCF používá verzi ze srpna 2004 specifikace WS-Addressing přidáním [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) a nastavenou na `messageVersion` hodnotu <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="2074e-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="2074e-121">Pokud používáte SOAP 1,2, nastavte `messageVersion` atribut na <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A> .</span><span class="sxs-lookup"><span data-stu-id="2074e-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="2074e-122">Určete, že služba používá vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2074e-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="2074e-123">Nastavte `binding` atribut [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu na `customBinding` .</span><span class="sxs-lookup"><span data-stu-id="2074e-123">Set the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="2074e-124">Nastavte `bindingConfiguration` atribut [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) elementu na hodnotu zadanou v `name` atributu [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="2074e-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="2074e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2074e-125">Example</span></span>

<span data-ttu-id="2074e-126">Následující příklad kódu určuje, že `Service.HelloWorldService` používá vlastní vazbu pro spolupráci s klienty WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="2074e-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="2074e-127">Vlastní vazba určuje, že verze 2004 protokolu WS-Addressing a WS-Security 1,1 sady specifikací slouží ke kódování vyměňovaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="2074e-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="2074e-128">Zprávy jsou zabezpečeny pomocí <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> režimu ověřování.</span><span class="sxs-lookup"><span data-stu-id="2074e-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2074e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2074e-129">See also</span></span>

- [<span data-ttu-id="2074e-130">Postupy: Přizpůsobení vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2074e-130">How to: Customize a System-Provided Binding</span></span>](../extending/how-to-customize-a-system-provided-binding.md)
