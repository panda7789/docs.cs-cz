---
title: 'Postupy: Nastavení režimu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e8c08fba0e4a74eafab00e75977a9f756c1b1cfa
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="41c1d-102">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="41c1d-102">How to: Set the Security Mode</span></span>
<span data-ttu-id="41c1d-103">Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí na nejvíce předdefinované vazby: přenos zpráv a "přenos s pověřením zpráv."</span><span class="sxs-lookup"><span data-stu-id="41c1d-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="41c1d-104">Dva další režimy, které jsou specifické pro dvě vazby: v režimu "pouze přenos pověření" nalezen <xref:System.ServiceModel.BasicHttpBinding>a "I" režim, v nalezen <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="41c1d-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="41c1d-105">Ale v tomto tématu soustřeďuje na tři běžných režimů zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, a <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="41c1d-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
 <span data-ttu-id="41c1d-106">Všimněte si, že ne každé předdefinované vazba podporuje všechny tyto režimy.</span><span class="sxs-lookup"><span data-stu-id="41c1d-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="41c1d-107">Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> třídy a ukazuje, jak nastavení režimu prostřednictvím kódu programu i prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="41c1d-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>  
  
 <span data-ttu-id="41c1d-108">Další informace najdete v tématu zabezpečení WCF, najdete v části [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md), [zabezpečení služby](../../../docs/framework/wcf/securing-services.md), a [zabezpečení služeb a klientů](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="41c1d-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="41c1d-109">Další informace o režim přenosu a zpráv najdete v tématu [zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md) a [zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="41c1d-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
### <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="41c1d-110">Nastavení režimu zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="41c1d-110">To set the security mode in code</span></span>  
  
1.  <span data-ttu-id="41c1d-111">Vytvoření instance třídy vazby, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="41c1d-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="41c1d-112">Seznam předdefinovaných vazby najdete v tématu [System-Provided vazby](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="41c1d-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="41c1d-113">Tento příklad vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="41c1d-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>  
  
2.  <span data-ttu-id="41c1d-114">Nastavte `Mode` vlastnost v objektu vrácený `Security` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="41c1d-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     <span data-ttu-id="41c1d-115">Alternativně nastavte režim na zprávu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-115">Alternatively, set the mode to message, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     <span data-ttu-id="41c1d-116">Nebo můžete nastavit režim přenosu s pověřením zpráv, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  <span data-ttu-id="41c1d-117">Můžete také nastavit režim v konstruktoru vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="41c1d-118">Nastavení vlastnosti ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="41c1d-118">Setting the ClientCredentialType Property</span></span>  
 <span data-ttu-id="41c1d-119">Nastavení režimu na jednu ze tří hodnot Určuje, jak nastavit `ClientCredentialType` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="41c1d-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="41c1d-120">Například pomocí <xref:System.ServiceModel.WSHttpBinding> třída, nastavení režimu na `Transport` znamená, je nutné nastavit <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> třída na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>  
  
#### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="41c1d-121">Chcete-li nastavit vlastnost ClientCredentialType pro režim přenosu</span><span class="sxs-lookup"><span data-stu-id="41c1d-121">To set the ClientCredentialType property for Transport mode</span></span>  
  
1.  <span data-ttu-id="41c1d-122">Vytvoření instance vazby.</span><span class="sxs-lookup"><span data-stu-id="41c1d-122">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="41c1d-123">Nastavte `Mode` vlastnost `Transport`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-123">Set the `Mode` property to `Transport`.</span></span>  
  
3.  <span data-ttu-id="41c1d-124">Nastavte `ClientCredential` vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="41c1d-125">Následující kód nastaví vlastnost na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-125">The following code sets the property to `Windows`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="41c1d-126">Chcete-li nastavit vlastnost ClientCredentialType pro režim zprávy</span><span class="sxs-lookup"><span data-stu-id="41c1d-126">To set the ClientCredentialType property for Message mode</span></span>  
  
1.  <span data-ttu-id="41c1d-127">Vytvoření instance vazby.</span><span class="sxs-lookup"><span data-stu-id="41c1d-127">Create an instance of the binding.</span></span>  
  
2.  <span data-ttu-id="41c1d-128">Nastavte `Mode` vlastnost `Message`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-128">Set the `Mode` property to `Message`.</span></span>  
  
3.  <span data-ttu-id="41c1d-129">Nastavte `ClientCredential` vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="41c1d-130">Následující kód nastaví vlastnost na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-130">The following code sets the property to `Certificate`.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="41c1d-131">Chcete-li nastavit vlastnost režimu a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="41c1d-131">To set the Mode and ClientCredentialType property in configuration</span></span>  
  
1.  <span data-ttu-id="41c1d-132">Přidat element do odpovídající vazby [ \<vazby >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="41c1d-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="41c1d-133">Následující příklad přidá [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="41c1d-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
2.  <span data-ttu-id="41c1d-134">Přidat `<binding>` elementu a sadu jeho `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="41c1d-135">Přidat `<security>` elementu a sadu `mode` atribut `Message`, `Transport`, nebo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="41c1d-136">Pokud režim je nastaven na `Transport`, přidejte `<transport>` elementu a sadu `clientCredential` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>  
  
     <span data-ttu-id="41c1d-137">Následující příklad nastaví režim "`Transport"`a nastaví `clientCredentialType` atribut `<transport>` element"`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="41c1d-138">Alternativně nastavte `security mode` na "`Message"`, za nímž následují `<"message">` elementu.</span><span class="sxs-lookup"><span data-stu-id="41c1d-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="41c1d-139">Tento příklad nastaví `clientCredentialType` na "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="41c1d-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     <span data-ttu-id="41c1d-140">Pomocí <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> hodnota je zvláštní případ a je popsáno níže.</span><span class="sxs-lookup"><span data-stu-id="41c1d-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>  
  
### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="41c1d-141">Pomocí TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="41c1d-141">Using TransportWithMessageCredential</span></span>  
 <span data-ttu-id="41c1d-142">Při nastavování režimu zabezpečení na `TransportWithMessageCredential`, přenos určuje skutečné mechanismus, který poskytuje zabezpečení transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="41c1d-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="41c1d-143">Například protokol HTTP používá Secure Sockets Layer (SSL) přes protokol HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="41c1d-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="41c1d-144">Proto nastavení `ClientCredentialType` vlastnost libovolného objektu zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity>) je ignorována.</span><span class="sxs-lookup"><span data-stu-id="41c1d-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="41c1d-145">Jinými slovy, můžete nastavit pouze `ClientCredentialType` objektu zabezpečení zpráv (pro `WSHttpBinding` vazba, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).</span><span class="sxs-lookup"><span data-stu-id="41c1d-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>  
  
 <span data-ttu-id="41c1d-146">Další informace najdete v tématu [postupy: použití zabezpečení přenosu a přihlašovací údaje zpráva](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="41c1d-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c1d-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="41c1d-147">See Also</span></span>  
 [<span data-ttu-id="41c1d-148">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="41c1d-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [<span data-ttu-id="41c1d-149">Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv</span><span class="sxs-lookup"><span data-stu-id="41c1d-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [<span data-ttu-id="41c1d-150">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="41c1d-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="41c1d-151">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="41c1d-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="41c1d-152">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="41c1d-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="41c1d-153">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="41c1d-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="41c1d-154">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="41c1d-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)  
 [<span data-ttu-id="41c1d-155">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="41c1d-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)  
 [<span data-ttu-id="41c1d-156">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="41c1d-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
