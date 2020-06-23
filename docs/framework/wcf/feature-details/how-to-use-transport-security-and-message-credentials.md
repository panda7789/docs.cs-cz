---
title: 'Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv'
description: Naučte se implementovat zabezpečení přenosu s přihlašovacími údaji pro zprávy, které nabízí nejlepší přenos a režimy zabezpečení zpráv ve službě WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246646"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="82776-103">Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv</span><span class="sxs-lookup"><span data-stu-id="82776-103">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="82776-104">Zabezpečení služby pomocí přenosu a přihlašovacích údajů pro zprávy využívá nejlepší z přenosů i režimů zabezpečení zpráv v Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="82776-104">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="82776-105">Zabezpečení transportní vrstvy zajišťuje integritu a důvěrnost, zatímco zabezpečení vrstev zpráv poskytuje celou řadu přihlašovacích údajů, které nejsou možné s přísným mechanismem zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="82776-105">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="82776-106">V tomto tématu se dozvíte o základních krocích pro implementaci přenosu s přihlašovacími údaji zprávy pomocí <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> vazeb a.</span><span class="sxs-lookup"><span data-stu-id="82776-106">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="82776-107">Další informace o nastavení režimu zabezpečení naleznete v tématu [How to: set a Security Mode](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="82776-107">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="82776-108">Při nastavení režimu zabezpečení na `TransportWithMessageCredential` je přenos určena skutečným mechanismem, který poskytuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="82776-108">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="82776-109">V případě protokolu HTTP je mechanismus SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP (HTTPS); v případě protokolu TCP se jedná o protokol SSL přes TCP nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="82776-109">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="82776-110">Pokud je přenos HTTP (pomocí <xref:System.ServiceModel.WSHttpBinding> ), SSL over HTTP poskytuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="82776-110">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="82776-111">V takovém případě je nutné nakonfigurovat počítač hostující službu s certifikátem SSL vázaným na port, jak je uvedeno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="82776-111">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="82776-112">Pokud je přenos TCP (pomocí <xref:System.ServiceModel.NetTcpBinding> ), ve výchozím nastavení je poskytnuté zabezpečení na úrovni přenosu Windows Security nebo SSL přes TCP.</span><span class="sxs-lookup"><span data-stu-id="82776-112">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="82776-113">Pokud používáte protokol SSL přes protokol TCP, je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody, jak je uvedeno dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="82776-113">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="82776-114">Použití WSHttpBinding s certifikátem pro zabezpečení přenosu (v kódu)</span><span class="sxs-lookup"><span data-stu-id="82776-114">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="82776-115">Pomocí nástroje HttpCfg.exe navažte certifikát SSL s portem v počítači.</span><span class="sxs-lookup"><span data-stu-id="82776-115">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="82776-116">Další informace najdete v tématu [Postup: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="82776-116">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="82776-117">Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="82776-117">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="82776-118">Nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-118">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="82776-119">(Další informace najdete v tématu [Výběr typu přihlašovacích údajů](selecting-a-credential-type.md).) Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-119">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="82776-120">Vytvořte instanci <xref:System.Uri> třídy s příslušnou základní adresou.</span><span class="sxs-lookup"><span data-stu-id="82776-120">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="82776-121">Upozorňujeme, že adresa musí používat schéma HTTPS a musí obsahovat skutečný název počítače a číslo portu, ke kterému je certifikát SSL vázaný.</span><span class="sxs-lookup"><span data-stu-id="82776-121">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="82776-122">(Případně můžete v konfiguraci nastavit základní adresu.)</span><span class="sxs-lookup"><span data-stu-id="82776-122">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="82776-123">Přidejte koncový bod služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="82776-123">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="82776-124">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> a zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="82776-124">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="82776-125">Použití NetTcpBinding s certifikátem pro zabezpečení přenosu (v kódu)</span><span class="sxs-lookup"><span data-stu-id="82776-125">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="82776-126">Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a nastavte <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="82776-126">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="82776-127">Nastavte na <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-127">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="82776-128">Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-128">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="82776-129">Vytvořte instanci <xref:System.Uri> třídy s příslušnou základní adresou.</span><span class="sxs-lookup"><span data-stu-id="82776-129">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="82776-130">Upozorňujeme, že adresa musí používat schéma NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="82776-130">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="82776-131">(Případně můžete v konfiguraci nastavit základní adresu.)</span><span class="sxs-lookup"><span data-stu-id="82776-131">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="82776-132">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="82776-132">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="82776-133">Pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy explicitně nastavte certifikát X. 509 pro službu.</span><span class="sxs-lookup"><span data-stu-id="82776-133">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="82776-134">Přidejte koncový bod služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="82776-134">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="82776-135">Zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="82776-135">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="82776-136">Použití NetTcpBinding se systémem Windows pro zabezpečení přenosu (v kódu)</span><span class="sxs-lookup"><span data-stu-id="82776-136">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="82776-137">Vytvořte instanci <xref:System.ServiceModel.NetTcpBinding> třídy a nastavte <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost na <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="82776-137">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="82776-138">Nastavte zabezpečení přenosu pro použití Windows nastavením na <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> <xref:System.ServiceModel.TcpClientCredentialType.Windows> .</span><span class="sxs-lookup"><span data-stu-id="82776-138">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="82776-139">(Všimněte si, že toto je výchozí nastavení.)</span><span class="sxs-lookup"><span data-stu-id="82776-139">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="82776-140">Nastavte na <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-140">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="82776-141">Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-141">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="82776-142">Vytvořte instanci <xref:System.Uri> třídy s příslušnou základní adresou.</span><span class="sxs-lookup"><span data-stu-id="82776-142">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="82776-143">Upozorňujeme, že adresa musí používat schéma NET. TCP.</span><span class="sxs-lookup"><span data-stu-id="82776-143">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="82776-144">(Případně můžete v konfiguraci nastavit základní adresu.)</span><span class="sxs-lookup"><span data-stu-id="82776-144">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="82776-145">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="82776-145">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="82776-146">Pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy explicitně nastavte certifikát X. 509 pro službu.</span><span class="sxs-lookup"><span data-stu-id="82776-146">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="82776-147">Přidejte koncový bod služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="82776-147">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="82776-148">Zavolejte <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="82776-148">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="82776-149">Použití konfigurace</span><span class="sxs-lookup"><span data-stu-id="82776-149">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="82776-150">Použití WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="82776-150">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="82776-151">Nakonfigurujte počítač s certifikátem SSL vázaným na port.</span><span class="sxs-lookup"><span data-stu-id="82776-151">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="82776-152">(Další informace najdete v tématu [Postup: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="82776-152">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="82776-153">V této konfiguraci není nutné nastavovat `transport` hodnotu prvku <>.</span><span class="sxs-lookup"><span data-stu-id="82776-153">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="82776-154">Zadejte typ přihlašovacích údajů klienta pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="82776-154">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="82776-155">Následující příklad nastaví `clientCredentialType` atribut `message` prvku <> na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="82776-155">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="82776-156">Použití NetTcpBinding s certifikátem pro zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="82776-156">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="82776-157">Pro protokol SSL přes TCP musíte explicitně zadat certifikát v `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="82776-157">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="82776-158">Následující příklad určuje certifikát vystavitelem ve výchozím umístění úložiště (místní počítač a osobní úložiště).</span><span class="sxs-lookup"><span data-stu-id="82776-158">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="82776-159">Přidat [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do oddílu Bindings</span><span class="sxs-lookup"><span data-stu-id="82776-159">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="82776-160">Přidejte prvek vazby a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-160">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="82776-161">Přidejte prvek <`security`> a nastavte `mode` atribut na `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="82776-161">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="82776-162">Přidejte prvek <`message>` a nastavte `clientCredentialType` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-162">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="82776-163">Použití NetTcpBinding s Windows pro zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="82776-163">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="82776-164">Přidejte [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) do části Bindings (vazby),</span><span class="sxs-lookup"><span data-stu-id="82776-164">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="82776-165">Přidejte prvek <`binding`> a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-165">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="82776-166">Přidejte prvek <`security`> a nastavte `mode` atribut na `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="82776-166">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="82776-167">Přidejte prvek <`transport`> a nastavte `clientCredentialType` atribut na `Windows` .</span><span class="sxs-lookup"><span data-stu-id="82776-167">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="82776-168">Přidejte prvek <`message`> a nastavte `clientCredentialType` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82776-168">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="82776-169">Následující kód nastaví hodnotu na certifikát.</span><span class="sxs-lookup"><span data-stu-id="82776-169">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="82776-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="82776-170">See also</span></span>

- [<span data-ttu-id="82776-171">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="82776-171">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="82776-172">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="82776-172">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="82776-173">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="82776-173">Securing Services and Clients</span></span>](securing-services-and-clients.md)
