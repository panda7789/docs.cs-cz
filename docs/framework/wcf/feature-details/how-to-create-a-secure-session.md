---
title: "Postupy: vytvoření zabezpečené relace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f2393209352f18eb25b9837ca1ad8ca2746b91d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="83d10-102">Postupy: vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="83d10-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="83d10-103">S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, vazby poskytované systémem v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automaticky používat zabezpečených relací, pokud je povolená zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="83d10-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="83d10-104">Ve výchozím nastavení zabezpečených relací není i po webový server, který recykluje.</span><span class="sxs-lookup"><span data-stu-id="83d10-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="83d10-105">Po vytvoření zabezpečené relace mezipaměti klienta a služby, klíč, který je přidružen zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="83d10-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="83d10-106">Jak se vyměňují zprávy, se vyměňují jenom identifikátor ke klíči v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="83d10-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="83d10-107">Pokud webový server je recykluje, mezipaměti je také recykluje, tak, aby webový server nemůže načíst uložené v mezipaměti klíče pro identifikátor.</span><span class="sxs-lookup"><span data-stu-id="83d10-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="83d10-108">V takovém případě je klientovi zpět vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="83d10-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="83d10-109">Zabezpečených relací, které používají tokenu kontextu zabezpečení stavová (SCT) přežijí recyklovány webového serveru.</span><span class="sxs-lookup"><span data-stu-id="83d10-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="83d10-110">pomocí stavová SCT v zabezpečené relaci, najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="83d10-110"> using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="83d10-111">Chcete-li určit, že služba používá zabezpečených relací pomocí jedné z vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="83d10-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="83d10-112">Nakonfigurujte službu, která používá vazbu poskytované systémem, který podporuje zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="83d10-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="83d10-113">S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, pokud vazby poskytované systémem jsou nakonfigurovaná pro použití zabezpečení zpráv [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticky použije zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="83d10-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically uses secure sessions.</span></span> <span data-ttu-id="83d10-114">Následující tabulka uvádí vazby poskytované systémem, které podporují zabezpečení zpráv a zda je zabezpečení zpráv výchozího mechanismu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="83d10-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="83d10-115">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="83d10-115">System-provided binding</span></span>|<span data-ttu-id="83d10-116">Konfigurační element</span><span class="sxs-lookup"><span data-stu-id="83d10-116">Configuration element</span></span>|<span data-ttu-id="83d10-117">Zabezpečení zpráv na ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="83d10-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="83d10-118">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="83d10-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="83d10-119">Ne</span><span class="sxs-lookup"><span data-stu-id="83d10-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="83d10-120">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="83d10-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="83d10-121">Ano</span><span class="sxs-lookup"><span data-stu-id="83d10-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="83d10-122">\<– wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="83d10-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="83d10-123">Ano</span><span class="sxs-lookup"><span data-stu-id="83d10-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="83d10-124">\<– wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="83d10-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="83d10-125">Ano</span><span class="sxs-lookup"><span data-stu-id="83d10-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="83d10-126">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="83d10-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="83d10-127">Ne</span><span class="sxs-lookup"><span data-stu-id="83d10-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="83d10-128">\<– netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="83d10-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="83d10-129">Ne</span><span class="sxs-lookup"><span data-stu-id="83d10-129">No</span></span>|  
  
     <span data-ttu-id="83d10-130">Následující příklad kódu používá k určení vazbu s názvem konfigurace `wsHttpBinding_Calculator` používající [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="83d10-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="83d10-131">Následující příklad kódu určuje, že [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečení relací se používají k zabezpečení `secureCalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="83d10-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="83d10-132">Může být vypnuto zabezpečených relací pro [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nastavením `establishSecurityContext` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="83d10-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="83d10-133">Pro ostatní poskytované systémem vazby zabezpečených relací lze pouze vypnout tak, že vytvoříte vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="83d10-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="83d10-134">Chcete-li určit, že služba používá zabezpečených relací pomocí vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="83d10-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="83d10-135">Vytvoření vlastní vazby, která určuje, že protokolu SOAP zprávy jsou chráněny zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="83d10-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="83d10-136">Vytvoření vlastní vazby, najdete v části [postupy: přizpůsobení vazbu System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="83d10-136"> creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="83d10-137">Následující příklad kódu používá konfiguraci určuje vlastní vazby této zprávy pomocí zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="83d10-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="83d10-138">Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování bootstrap zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="83d10-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="83d10-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="83d10-139">See Also</span></span>  
 [<span data-ttu-id="83d10-140">Vazby WCF – přehled</span><span class="sxs-lookup"><span data-stu-id="83d10-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
