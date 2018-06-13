---
title: 'Postupy: vytvoření zabezpečené relace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ce351a87e70b09a2f68654af817e28fa3145d79d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493194"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="d0442-102">Postupy: vytvoření zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="d0442-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="d0442-103">S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, vazby poskytované systémem Windows Communication Foundation (WCF) automaticky použít zabezpečených relací, pokud je povolená zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="d0442-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="d0442-104">Ve výchozím nastavení zabezpečených relací není i po webový server, který recykluje.</span><span class="sxs-lookup"><span data-stu-id="d0442-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="d0442-105">Po vytvoření zabezpečené relace mezipaměti klienta a služby, klíč, který je přidružen zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="d0442-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="d0442-106">Jak se vyměňují zprávy, se vyměňují jenom identifikátor ke klíči v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d0442-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="d0442-107">Pokud webový server je recykluje, mezipaměti je také recykluje, tak, aby webový server nemůže načíst uložené v mezipaměti klíče pro identifikátor.</span><span class="sxs-lookup"><span data-stu-id="d0442-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="d0442-108">V takovém případě je klientovi zpět vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d0442-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="d0442-109">Zabezpečených relací, které používají tokenu kontextu zabezpečení stavová (SCT) přežijí recyklovány webového serveru.</span><span class="sxs-lookup"><span data-stu-id="d0442-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="d0442-110">Další informace o používání stavová SCT v zabezpečené relaci najdete v tématu [postupy: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="d0442-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="d0442-111">Chcete-li určit, že služba používá zabezpečených relací pomocí jedné z vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="d0442-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="d0442-112">Nakonfigurujte službu, která používá vazbu poskytované systémem, který podporuje zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="d0442-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="d0442-113">S výjimkou produktů [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) vazby, pokud jsou vazby poskytované systémem nakonfigurovány pro použití zabezpečení zpráv WCF automaticky používá zabezpečených relací.</span><span class="sxs-lookup"><span data-stu-id="d0442-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="d0442-114">Následující tabulka uvádí vazby poskytované systémem, které podporují zabezpečení zpráv a zda je zabezpečení zpráv výchozího mechanismu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d0442-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="d0442-115">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="d0442-115">System-provided binding</span></span>|<span data-ttu-id="d0442-116">Konfigurační element</span><span class="sxs-lookup"><span data-stu-id="d0442-116">Configuration element</span></span>|<span data-ttu-id="d0442-117">Zabezpečení zpráv na ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="d0442-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="d0442-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d0442-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="d0442-119">Ne</span><span class="sxs-lookup"><span data-stu-id="d0442-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="d0442-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d0442-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="d0442-121">Ano</span><span class="sxs-lookup"><span data-stu-id="d0442-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="d0442-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d0442-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="d0442-123">Ano</span><span class="sxs-lookup"><span data-stu-id="d0442-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="d0442-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d0442-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="d0442-125">Ano</span><span class="sxs-lookup"><span data-stu-id="d0442-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="d0442-126">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="d0442-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="d0442-127">Ne</span><span class="sxs-lookup"><span data-stu-id="d0442-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="d0442-128">\<– netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="d0442-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="d0442-129">Ne</span><span class="sxs-lookup"><span data-stu-id="d0442-129">No</span></span>|  
  
     <span data-ttu-id="d0442-130">Následující příklad kódu používá k určení vazbu s názvem konfigurace `wsHttpBinding_Calculator` používající [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečené relace.</span><span class="sxs-lookup"><span data-stu-id="d0442-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="d0442-131">Následující příklad kódu určuje, že [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)zabezpečení zpráv a zabezpečení relací se používají k zabezpečení `secureCalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="d0442-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="d0442-132">Může být vypnuto zabezpečených relací pro [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) nastavením `establishSecurityContext` atribut `false`.</span><span class="sxs-lookup"><span data-stu-id="d0442-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="d0442-133">Pro ostatní poskytované systémem vazby zabezpečených relací lze pouze vypnout tak, že vytvoříte vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="d0442-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="d0442-134">Chcete-li určit, že služba používá zabezpečených relací pomocí vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="d0442-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="d0442-135">Vytvoření vlastní vazby, která určuje, že protokolu SOAP zprávy jsou chráněny zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="d0442-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="d0442-136">Další informace o vytváření vlastních vazeb najdete v tématu [postupy: přizpůsobení vazbu System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="d0442-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="d0442-137">Následující příklad kódu používá konfiguraci určuje vlastní vazby této zprávy pomocí zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="d0442-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="d0442-138">Následující příklad kódu vytvoří vlastní vazby, který používá <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> režim ověřování bootstrap zabezpečené relaci.</span><span class="sxs-lookup"><span data-stu-id="d0442-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d0442-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0442-139">See Also</span></span>  
 [<span data-ttu-id="d0442-140">Přehled vazeb WCF</span><span class="sxs-lookup"><span data-stu-id="d0442-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
