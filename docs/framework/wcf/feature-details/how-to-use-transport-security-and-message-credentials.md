---
title: 'Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b94c6fd4761a5b0383c21d36a6d717f78a8825de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496037"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="22036-102">Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv</span><span class="sxs-lookup"><span data-stu-id="22036-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="22036-103">Zabezpečení služby přenosu a zpráva pověření používá nejlepší přenosu a zpráva režimy zabezpečení ve Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="22036-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="22036-104">Transport layer security poskytuje v sum, integrity a důvěrnosti, zatímco zpráva vrstvy zabezpečení poskytuje přihlašovací údaje, které nejsou možné pomocí mechanismy zabezpečení striktní přenosu.</span><span class="sxs-lookup"><span data-stu-id="22036-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="22036-105">Toto téma ukazuje základní kroky pro implementaci přenosu zpráv přihlašovací údaje pomocí <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> vazby.</span><span class="sxs-lookup"><span data-stu-id="22036-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="22036-106">Další informace o nastavení režimu zabezpečení najdete v tématu [postupy: nastavení režimu zabezpečení](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="22036-106">For more information about setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="22036-107">Při nastavování režimu zabezpečení na `TransportWithMessageCredential`, přenos určuje skutečné mechanismus, který poskytuje zabezpečení transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="22036-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="22036-108">Pro protokol HTTP je tento mechanismus Secure Sockets Layer (SSL) přes protokol HTTP (HTTPS); pro TCP je protokol SSL přes TCP nebo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="22036-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="22036-109">Pokud je přenos HTTP (pomocí <xref:System.ServiceModel.WSHttpBinding>), SSL přes protokol HTTP poskytuje zabezpečení transportní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="22036-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="22036-110">V takovém případě musíte nakonfigurovat počítač hostující službu certifikátem SSL vázána k portu, jak uvidíte později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="22036-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="22036-111">Pokud je přenos TCP (pomocí <xref:System.ServiceModel.NetTcpBinding>), ve výchozím nastavení zabezpečení transportní vrstvy poskytované je zabezpečení systému Windows nebo SSL přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="22036-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="22036-112">Při použití protokolu SSL přes TCP, je nutné zadat certifikát pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metoda, jak uvidíte později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="22036-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="22036-113">Použít WSHttpBinding s certifikátem zabezpečení přenosu (v kódu)</span><span class="sxs-lookup"><span data-stu-id="22036-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="22036-114">Použijte nástroj HttpCfg.exe k vytvoření vazby certifikátu SSL port na počítači.</span><span class="sxs-lookup"><span data-stu-id="22036-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="22036-115">Další informace najdete v tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="22036-115">For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="22036-116">Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> a nastavit <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="22036-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="22036-117">Nastavte <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="22036-118">(Další informace najdete v tématu [výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-118">(For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="22036-119">Vytvoření instance <xref:System.Uri> třídy příslušné základní adresu.</span><span class="sxs-lookup"><span data-stu-id="22036-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="22036-120">Všimněte si, že adresa musí používat schéma "HTTPS" a musí obsahovat skutečný název počítač a číslo portu, který je vázána certifikát SSL.</span><span class="sxs-lookup"><span data-stu-id="22036-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="22036-121">(Alternativně můžete nastavit základní adresa v konfiguraci.)</span><span class="sxs-lookup"><span data-stu-id="22036-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="22036-122">Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="22036-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="22036-123">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> a volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="22036-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="22036-124">Použít NetTcpBinding s certifikátem zabezpečení přenosu (v kódu)</span><span class="sxs-lookup"><span data-stu-id="22036-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="22036-125">Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> a nastavit <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="22036-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="22036-126">Nastavte <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="22036-127">Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="22036-128">Vytvoření instance <xref:System.Uri> třídy příslušné základní adresu.</span><span class="sxs-lookup"><span data-stu-id="22036-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="22036-129">Všimněte si, že adresu musí používat schéma "net.tcp".</span><span class="sxs-lookup"><span data-stu-id="22036-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="22036-130">(Alternativně můžete nastavit základní adresa v konfiguraci.)</span><span class="sxs-lookup"><span data-stu-id="22036-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="22036-131">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="22036-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="22036-132">Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třída explicitně nastavit pro službu certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="22036-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="22036-133">Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="22036-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="22036-134">Volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="22036-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="22036-135">Pro použití NetTcpBinding s Windows pro zabezpečení přenosu (v kódu)</span><span class="sxs-lookup"><span data-stu-id="22036-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="22036-136">Vytvoření instance <xref:System.ServiceModel.NetTcpBinding> a nastavit <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> vlastnost <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="22036-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="22036-137">Nastavení zabezpečení přenosu pomocí systému Windows nastavením <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> k <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="22036-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="22036-138">(Všimněte si, že toto je výchozí hodnota.)</span><span class="sxs-lookup"><span data-stu-id="22036-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="22036-139">Nastavte <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="22036-140">Následující kód používá <xref:System.ServiceModel.MessageCredentialType.Certificate> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="22036-141">Vytvoření instance <xref:System.Uri> třídy příslušné základní adresu.</span><span class="sxs-lookup"><span data-stu-id="22036-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="22036-142">Všimněte si, že adresu musí používat schéma "net.tcp".</span><span class="sxs-lookup"><span data-stu-id="22036-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="22036-143">(Alternativně můžete nastavit základní adresa v konfiguraci.)</span><span class="sxs-lookup"><span data-stu-id="22036-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="22036-144">Vytvořte instanci <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="22036-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="22036-145">Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třída explicitně nastavit pro službu certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="22036-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="22036-146">Přidání koncového bodu služby pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="22036-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="22036-147">Volání <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="22036-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="22036-148">Pomocí konfigurace</span><span class="sxs-lookup"><span data-stu-id="22036-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="22036-149">Chcete-li použít WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="22036-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="22036-150">Nakonfigurujte počítač certifikátem SSL vázány na port.</span><span class="sxs-lookup"><span data-stu-id="22036-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="22036-151">(Další informace najdete v tématu [postup: Nakonfigurujte certifikát protokolu SSL Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="22036-151">(For more information, see [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="22036-152">Není nutné nastavovat <`transport`> Hodnota elementu s touto konfigurací.</span><span class="sxs-lookup"><span data-stu-id="22036-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="22036-153">Zadejte typ pověření klienta pro zprávy úroveň zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="22036-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="22036-154">Následující příklad nastavuje `clientCredentialType` atribut <`message`> elementu, který chcete `UserName`.</span><span class="sxs-lookup"><span data-stu-id="22036-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="22036-155">Použít NetTcpBinding s certifikátem zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="22036-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="22036-156">Pro protokol SSL přes TCP, je třeba explicitně zadat certifikát v `<behaviors>` elementu.</span><span class="sxs-lookup"><span data-stu-id="22036-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="22036-157">Následující příklad určuje certifikát jeho vystavitelem ve výchozím umístění úložiště (místní počítač a osobní úložiště).</span><span class="sxs-lookup"><span data-stu-id="22036-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2.  <span data-ttu-id="22036-158">Přidat [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do části vazby</span><span class="sxs-lookup"><span data-stu-id="22036-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="22036-159">Přidá prvek vazby a nastavte `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="22036-160">Přidat <`security`> elementu a nastavte `mode` atribut `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="22036-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="22036-161">Přidat <`message>` elementu a nastavte `clientCredentialType` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="22036-162">Pro použití NetTcpBinding s Windows pro zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="22036-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="22036-163">Přidat [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) do části vazby</span><span class="sxs-lookup"><span data-stu-id="22036-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="22036-164">Přidat <`binding`> elementu a sadu `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="22036-165">Přidat <`security`> elementu a nastavte `mode` atribut `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="22036-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="22036-166">Přidat <`transport`> elementu a sadu `clientCredentialType` atribut `Windows`.</span><span class="sxs-lookup"><span data-stu-id="22036-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="22036-167">Přidat <`message`> elementu a sadu `clientCredentialType` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="22036-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="22036-168">Následující kód nastaví hodnotu k certifikátu.</span><span class="sxs-lookup"><span data-stu-id="22036-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22036-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="22036-169">See Also</span></span>  
 [<span data-ttu-id="22036-170">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="22036-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [<span data-ttu-id="22036-171">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="22036-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="22036-172">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="22036-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
