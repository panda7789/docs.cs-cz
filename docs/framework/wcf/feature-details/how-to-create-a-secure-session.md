---
title: 'Postupy: Vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593409"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="64bfb-102">Postupy: Vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="64bfb-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="64bfb-103">S výjimkou [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) vazby poskytují systémy vazby v Windows Communication Foundation (WCF) automaticky zabezpečené relace, pokud je zapnuté zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="64bfb-103">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="64bfb-104">Ve výchozím nastavení zabezpečené relace neobsahují webový server, který se recykluje.</span><span class="sxs-lookup"><span data-stu-id="64bfb-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="64bfb-105">Po navázání zabezpečené relace klient a služba uloží klíč, který je přidružený k zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="64bfb-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="64bfb-106">Při výměně zpráv je vyměněn pouze identifikátor pro klíč uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="64bfb-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="64bfb-107">Pokud dojde k recyklení webového serveru, mezipaměť je také recyklována, což znamená, že webový server nemůže načíst klíč uložený v mezipaměti pro identifikátor.</span><span class="sxs-lookup"><span data-stu-id="64bfb-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="64bfb-108">Pokud k tomu dojde, je vrácena výjimka klientovi.</span><span class="sxs-lookup"><span data-stu-id="64bfb-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="64bfb-109">Zabezpečené relace, které používají token kontextového kontextu zabezpečení (SCT), mohou zachovány recyklaci webového serveru.</span><span class="sxs-lookup"><span data-stu-id="64bfb-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="64bfb-110">Další informace o používání stavového SCTu v zabezpečené relaci naleznete v tématu [How to: Create a Security Context token for the Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="64bfb-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="64bfb-111">Určení, že služba používá zabezpečené relace pomocí jedné z vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="64bfb-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="64bfb-112">Nakonfigurujte službu tak, aby používala vazbu poskytovanou systémem, která podporuje zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="64bfb-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="64bfb-113">S výjimkou [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) vazby platí, že pokud jsou zadané systémové vazby nakonfigurovány na používání zabezpečení zpráv, WCF automaticky používá zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="64bfb-113">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="64bfb-114">V následující tabulce jsou uvedené systémové vazby, které podporují zabezpečení zpráv a zda jsou zabezpečení zpráv výchozím mechanismem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="64bfb-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="64bfb-115">Vazba poskytnutá systémem</span><span class="sxs-lookup"><span data-stu-id="64bfb-115">System-provided binding</span></span>|<span data-ttu-id="64bfb-116">Element konfigurace</span><span class="sxs-lookup"><span data-stu-id="64bfb-116">Configuration element</span></span>|<span data-ttu-id="64bfb-117">Zabezpečení zprávy je ve výchozím nastavení zapnuté.</span><span class="sxs-lookup"><span data-stu-id="64bfb-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="64bfb-118">No</span><span class="sxs-lookup"><span data-stu-id="64bfb-118">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="64bfb-119">Ano</span><span class="sxs-lookup"><span data-stu-id="64bfb-119">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="64bfb-120">Ano</span><span class="sxs-lookup"><span data-stu-id="64bfb-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="64bfb-121">Ano</span><span class="sxs-lookup"><span data-stu-id="64bfb-121">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="64bfb-122">Ne</span><span class="sxs-lookup"><span data-stu-id="64bfb-122">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="64bfb-123">Ne</span><span class="sxs-lookup"><span data-stu-id="64bfb-123">No</span></span>|  
  
     <span data-ttu-id="64bfb-124">Následující příklad kódu používá konfiguraci k určení vazby s názvem, `wsHttpBinding_Calculator` která používá [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) zabezpečení, zabezpečení zprávy a zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="64bfb-124">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="64bfb-125">Následující příklad kódu určuje, zda se [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) k zabezpečení služby používá zabezpečení, zabezpečení zpráv a zabezpečené relace `secureCalculator` .</span><span class="sxs-lookup"><span data-stu-id="64bfb-125">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="64bfb-126">Zabezpečené relace lze pro rozhraní vypnout [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) nastavením `establishSecurityContext` atributu na `false` .</span><span class="sxs-lookup"><span data-stu-id="64bfb-126">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="64bfb-127">U ostatních vazeb poskytovaných systémem můžete zabezpečené relace vypnout jenom vytvořením vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="64bfb-127">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="64bfb-128">Určení, že služba používá zabezpečené relace pomocí vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="64bfb-128">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="64bfb-129">Vytvořte vlastní vazbu, která určuje, zda jsou zprávy protokolu SOAP chráněny zabezpečenou relací.</span><span class="sxs-lookup"><span data-stu-id="64bfb-129">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="64bfb-130">Další informace o vytvoření vlastní vazby naleznete v tématu [How to: Customizing a System-dodaná vazba](../extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="64bfb-130">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="64bfb-131">Následující příklad kódu používá konfiguraci k určení vlastní vazby pro zprávy pomocí zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="64bfb-131">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="64bfb-132">Následující příklad kódu vytvoří vlastní vazbu, která <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pro spuštění zabezpečené relace používá režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="64bfb-132">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="64bfb-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="64bfb-133">See also</span></span>

- [<span data-ttu-id="64bfb-134">Přehled vazeb WCF</span><span class="sxs-lookup"><span data-stu-id="64bfb-134">WCF Bindings Overview</span></span>](../bindings-overview.md)
