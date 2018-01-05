---
title: "Programování zabezpečení WCF"
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
helpviewer_keywords: message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
caps.latest.revision: "25"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4b296d9bf9b52dfc8e782f6e324be1de8c76d349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="programming-wcf-security"></a><span data-ttu-id="89eed-102">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="89eed-102">Programming WCF Security</span></span>
<span data-ttu-id="89eed-103">Toto téma popisuje základní programovací úlohy použité k vytvoření zabezpečeného [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="89eed-103">This topic describes the fundamental programming tasks used to create a secure [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="89eed-104">Toto téma popisuje pouze ověřování, důvěrnost a integritu, souhrnně označované jako *přenosu zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="89eed-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="89eed-105">Toto téma nepopisuje autorizace (řízení přístupu k prostředkům nebo službám); informace o ověřování najdete v tématu [autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89eed-106">Cenné Úvod k koncepty zabezpečení, zejména v ohledem na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete na webu MSDN na sadu vzory a postupy kurzy [scénáře, vzory a implementace pokyny pro webové služby vylepšení (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span><span class="sxs-lookup"><span data-stu-id="89eed-106">For a valuable introduction to security concepts, especially in regard to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](http://go.microsoft.com/fwlink/?LinkID=88250).</span></span>  
  
 <span data-ttu-id="89eed-107">Programování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení je založena na nastavení následující tři kroky: režim zabezpečení, typu pověření klienta a hodnot přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="89eed-107">Programming [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="89eed-108">Abyste mohli provést tyto kroky buď prostřednictvím kódu nebo konfigurace.</span><span class="sxs-lookup"><span data-stu-id="89eed-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="89eed-109">Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="89eed-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="89eed-110">Následující příklad popisuje obecné kroky pro programování s režimem zabezpečení v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="89eed-110">The following explains the general steps for programming with the security mode in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
1.  <span data-ttu-id="89eed-111">Vyberte jeden z předdefinovaných vazby, které jsou vhodné pro vaše požadavky aplikací.</span><span class="sxs-lookup"><span data-stu-id="89eed-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="89eed-112">Seznam voleb vazby najdete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-112">For a list of the binding choices, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="89eed-113">Téměř každý vazby má ve výchozím nastavení zabezpečení povoleno.</span><span class="sxs-lookup"><span data-stu-id="89eed-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="89eed-114">Jedinou výjimkou je <xref:System.ServiceModel.BasicHttpBinding> – třída (pomocí konfigurace, [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span><span class="sxs-lookup"><span data-stu-id="89eed-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="89eed-115">Vazba, kterou vyberete určuje přenosu.</span><span class="sxs-lookup"><span data-stu-id="89eed-115">The binding you select determines the transport.</span></span> <span data-ttu-id="89eed-116">Například <xref:System.ServiceModel.WSHttpBinding> používá protokol HTTP jako přenos; <xref:System.ServiceModel.NetTcpBinding> používá protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="89eed-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2.  <span data-ttu-id="89eed-117">Vyberte jeden z režimů zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="89eed-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="89eed-118">Všimněte si, že vazby, kterou vyberete, určuje možnosti k dispozici režimu.</span><span class="sxs-lookup"><span data-stu-id="89eed-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="89eed-119">Například <xref:System.ServiceModel.WSDualHttpBinding> neumožňuje zabezpečení přenosu (není možnost).</span><span class="sxs-lookup"><span data-stu-id="89eed-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="89eed-120">Podobně ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umožňuje zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="89eed-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="89eed-121">Máte tři možnosti:</span><span class="sxs-lookup"><span data-stu-id="89eed-121">You have three choices:</span></span>  
  
    1.  `Transport`  
  
         <span data-ttu-id="89eed-122">Zabezpečení přenosu závisí na mechanismu, který používá vazby, které jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="89eed-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="89eed-123">Například, pokud používáte `WSHttpBinding` je mechanismus zabezpečení Secure Sockets Layer (SSL) (také mechanismus pro protokol HTTPS).</span><span class="sxs-lookup"><span data-stu-id="89eed-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="89eed-124">Hlavní výhodou zabezpečení přenosu je obecně řečeno, zajišťuje dobrý propustnost, bez ohledu na to, které přenosu používáte.</span><span class="sxs-lookup"><span data-stu-id="89eed-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="89eed-125">Však obsahuje dvě omezení: první je, že přenosový mechanismus Určuje typ pověření pro ověření uživatele.</span><span class="sxs-lookup"><span data-stu-id="89eed-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="89eed-126">Toto je nevýhodou pouze v případě, že služba potřebuje pro spolupráci s jinými službami, které potřebují různé typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="89eed-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="89eed-127">Druhá je, že, protože zabezpečení není použita na úrovni zpráv, zabezpečení je implementovaná v segmentu směrování způsobem spíše než začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="89eed-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="89eed-128">Toto omezení druhé je problém pouze v případě, že cesta zpráv mezi klientem a službou obsahuje prostředníci.</span><span class="sxs-lookup"><span data-stu-id="89eed-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="89eed-129">přenos, které chcete použít, najdete v části [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-129"> which transport to use, see [Choosing a Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="89eed-130">pomocí zabezpečení přenosu, najdete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-130"> using transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
    2.  `Message`  
  
         <span data-ttu-id="89eed-131">Zabezpečení zpráv znamená, že každá zpráva obsahuje potřebné hlavičky a zabezpečení dat, které chcete zachovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="89eed-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="89eed-132">Vzhledem k tomu, že se liší složení záhlaví může obsahovat libovolný počet přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="89eed-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="89eed-133">Faktor to stane, pokud jste se spolupráce s jinými službami této poptávky typ určité pověření, který nelze zadat přenosový mechanismus, nebo pokud zprávy musí být použit s více než jedna služba, kde každá služba vyžaduje typ různých přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="89eed-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="89eed-134">[Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-134"> [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
    3.  `TransportWithMessageCredential`  
  
         <span data-ttu-id="89eed-135">Tato volba používá přenosové vrstvy zabezpečit přenos zpráv, při každé zprávy je i bohaté přihlašovací údaje potřebovat další služby.</span><span class="sxs-lookup"><span data-stu-id="89eed-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="89eed-136">Kombinuje výkon výhod zabezpečení přenosu s výhodou bohaté pověření zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="89eed-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="89eed-137">Toto je k dispozici následující vazby: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, a <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="89eed-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="89eed-138">Pokud se rozhodnete použít zabezpečení přenosu pro protokol HTTP (jinými slovy, HTTPS), musíte také nakonfigurovat certifikát SSL hostitele a povolit protokol SSL na portu.</span><span class="sxs-lookup"><span data-stu-id="89eed-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="89eed-139">[Zabezpečení přenosu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-139"> [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
4.  <span data-ttu-id="89eed-140">Pokud používáte <xref:System.ServiceModel.WSHttpBinding> a není potřeba navázat zabezpečené relaci, nastavte <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="89eed-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="89eed-141">Zabezpečené relace nastane, když klient a služba vytvoření kanálu pomocí symetrického klíče (klient i server používají stejný klíč délky konverzace, dokud nezavřete dialogové okno).</span><span class="sxs-lookup"><span data-stu-id="89eed-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="89eed-142">Nastavení typu pověření klienta</span><span class="sxs-lookup"><span data-stu-id="89eed-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="89eed-143">Vyberte typ pověření klienta podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="89eed-143">Select a client credential type as appropriate.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="89eed-144">[Výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span><span class="sxs-lookup"><span data-stu-id="89eed-144"> [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span></span> <span data-ttu-id="89eed-145">K dispozici jsou následující typy pověření klienta:</span><span class="sxs-lookup"><span data-stu-id="89eed-145">The following client credential types are available:</span></span>  
  
-   `Windows`  
  
-   `Certificate`  
  
-   `Digest`  
  
-   `Basic`  
  
-   `UserName`  
  
-   `NTLM`  
  
-   `IssuedToken`  
  
 <span data-ttu-id="89eed-146">V závislosti na tom, jak nastavit režim musíte nastavit typ přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="89eed-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="89eed-147">Například pokud jste vybrali `wsHttpBinding`a nastavili režim "Zpráva,", pak můžete také nastavit `clientCredentialType` atribut elementu zprávy na jednu z následujících hodnot: `None`, `Windows`, `UserName`, `Certificate` , a `IssuedToken`, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="89eed-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="89eed-148">Nebo v kódu:</span><span class="sxs-lookup"><span data-stu-id="89eed-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="89eed-149">Nastavení hodnot přihlašovacích údajů služby</span><span class="sxs-lookup"><span data-stu-id="89eed-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="89eed-150">Jakmile vyberete typu pověření klienta, je nutné nastavit skutečné přihlašovací údaje pro službu a klienta pro použití.</span><span class="sxs-lookup"><span data-stu-id="89eed-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="89eed-151">Ve službě, jsou přihlašovací údaje nastavit pomocí <xref:System.ServiceModel.Description.ServiceCredentials> třídy a vrácený <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost <xref:System.ServiceModel.ServiceHostBase> – třída.</span><span class="sxs-lookup"><span data-stu-id="89eed-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="89eed-152">Vazba používá znamená typ přihlašovacích údajů služby, vybrali režim zabezpečení a typ pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="89eed-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="89eed-153">Následující kód nastaví certifikát pro přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="89eed-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="89eed-154">Nastavení hodnot přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="89eed-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="89eed-155">Na straně klienta, nastavte hodnoty přihlašovacích údajů klienta pomocí <xref:System.ServiceModel.Description.ClientCredentials> třídy a vrácené <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> – třída.</span><span class="sxs-lookup"><span data-stu-id="89eed-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="89eed-156">Následující kód nastaví certifikát jako pověření klienta pomocí protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="89eed-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="89eed-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="89eed-157">See Also</span></span>  
 [<span data-ttu-id="89eed-158">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="89eed-158">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="89eed-159">Běžné scénáře zabezpečení</span><span class="sxs-lookup"><span data-stu-id="89eed-159">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
