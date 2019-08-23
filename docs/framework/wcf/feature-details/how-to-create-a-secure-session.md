---
title: 'Postupy: Vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: bdb0f89b950d086e04cbb9d6da161bd315fc64b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934382"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="714cf-102">Postupy: Vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="714cf-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="714cf-103">S výjimkou [ \<> vazby](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , jsou vazby poskytnuté systémem v Windows Communication Foundation (WCF) automaticky používat zabezpečené relace, pokud je zapnuté zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="714cf-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="714cf-104">Ve výchozím nastavení zabezpečené relace neobsahují webový server, který se recykluje.</span><span class="sxs-lookup"><span data-stu-id="714cf-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="714cf-105">Po navázání zabezpečené relace klient a služba uloží klíč, který je přidružený k zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="714cf-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="714cf-106">Při výměně zpráv je vyměněn pouze identifikátor pro klíč uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="714cf-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="714cf-107">Pokud dojde k recyklení webového serveru, mezipaměť je také recyklována, což znamená, že webový server nemůže načíst klíč uložený v mezipaměti pro identifikátor.</span><span class="sxs-lookup"><span data-stu-id="714cf-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="714cf-108">Pokud k tomu dojde, je vrácena výjimka klientovi.</span><span class="sxs-lookup"><span data-stu-id="714cf-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="714cf-109">Zabezpečené relace, které používají token kontextového kontextu zabezpečení (SCT), mohou zachovány recyklaci webového serveru.</span><span class="sxs-lookup"><span data-stu-id="714cf-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="714cf-110">Další informace o používání stavového SCTu v zabezpečené relaci najdete v tématu [How to: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="714cf-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="714cf-111">Určení, že služba používá zabezpečené relace pomocí jedné z vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="714cf-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="714cf-112">Nakonfigurujte službu tak, aby používala vazbu poskytovanou systémem, která podporuje zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="714cf-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="714cf-113">S výjimkou [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, pokud jsou zadané systémové vazby nakonfigurovány na používání zabezpečení zpráv, WCF automaticky používá zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="714cf-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="714cf-114">V následující tabulce jsou uvedené systémové vazby, které podporují zabezpečení zpráv a zda jsou zabezpečení zpráv výchozím mechanismem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="714cf-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="714cf-115">Vazba poskytnutá systémem</span><span class="sxs-lookup"><span data-stu-id="714cf-115">System-provided binding</span></span>|<span data-ttu-id="714cf-116">Element konfigurace</span><span class="sxs-lookup"><span data-stu-id="714cf-116">Configuration element</span></span>|<span data-ttu-id="714cf-117">Zabezpečení zprávy je ve výchozím nastavení zapnuté.</span><span class="sxs-lookup"><span data-stu-id="714cf-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="714cf-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="714cf-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="714cf-119">Ne</span><span class="sxs-lookup"><span data-stu-id="714cf-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="714cf-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="714cf-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="714cf-121">Ano</span><span class="sxs-lookup"><span data-stu-id="714cf-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="714cf-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="714cf-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="714cf-123">Ano</span><span class="sxs-lookup"><span data-stu-id="714cf-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="714cf-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="714cf-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="714cf-125">Ano</span><span class="sxs-lookup"><span data-stu-id="714cf-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="714cf-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="714cf-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="714cf-127">Ne</span><span class="sxs-lookup"><span data-stu-id="714cf-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="714cf-128">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="714cf-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="714cf-129">Ne</span><span class="sxs-lookup"><span data-stu-id="714cf-129">No</span></span>|  
  
     <span data-ttu-id="714cf-130">Následující příklad kódu používá konfiguraci k určení vazby s názvem `wsHttpBinding_Calculator` , která [ \<používá WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpečení zpráv a zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="714cf-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="714cf-131">Následující příklad kódu určuje, že `secureCalculator` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)se k zabezpečení služby používá WSHttpBinding >, zabezpečení zpráv a zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="714cf-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="714cf-132">Zabezpečené relace je možné vypnout pro `establishSecurityContext` [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nastavením atributu na. `false`</span><span class="sxs-lookup"><span data-stu-id="714cf-132">Secure sessions can be turned off for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="714cf-133">U ostatních vazeb poskytovaných systémem můžete zabezpečené relace vypnout jenom vytvořením vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="714cf-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="714cf-134">Určení, že služba používá zabezpečené relace pomocí vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="714cf-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="714cf-135">Vytvořte vlastní vazbu, která určuje, zda jsou zprávy protokolu SOAP chráněny zabezpečenou relací.</span><span class="sxs-lookup"><span data-stu-id="714cf-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="714cf-136">Další informace o vytvoření vlastní vazby naleznete v tématu [How to: Přizpůsobení vazby](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)poskytnuté systémem.</span><span class="sxs-lookup"><span data-stu-id="714cf-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="714cf-137">Následující příklad kódu používá konfiguraci k určení vlastní vazby pro zprávy pomocí zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="714cf-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="714cf-138">Následující příklad kódu vytvoří vlastní vazbu, která pro spuštění zabezpečené <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> relace používá režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="714cf-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="714cf-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="714cf-139">See also</span></span>

- [<span data-ttu-id="714cf-140">Přehled vazeb WCF</span><span class="sxs-lookup"><span data-stu-id="714cf-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
