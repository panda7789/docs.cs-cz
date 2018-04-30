---
title: 'Postupy: Zadání hodnot přihlašovacích údajů klienta'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 856d33f88b55c35927998b15acc7bbf8ff1e9fe2
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="8190c-102">Postupy: Zadání hodnot přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="8190c-102">How to: Specify Client Credential Values</span></span>
<span data-ttu-id="8190c-103">Pomocí [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], službu, můžete určit, jak je ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="8190c-103">Using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="8190c-104">Službu můžete například stanovení, ověření klienta s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="8190c-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>  
  
### <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="8190c-105">K určení typu pověření klienta</span><span class="sxs-lookup"><span data-stu-id="8190c-105">To determine the client credential type</span></span>  
  
1.  <span data-ttu-id="8190c-106">Načtení metadat z koncového bodu služby metadat.</span><span class="sxs-lookup"><span data-stu-id="8190c-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="8190c-107">Metadata se obvykle skládá z dva soubory: kód klienta na programovací jazyk podle vašeho výběru (výchozí hodnota je Visual C#) a konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="8190c-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="8190c-108">Jeden způsob, jak načíst metadata je použití nástroje Svcutil.exe vrátí kód klienta a konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="8190c-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="8190c-109">Další informace najdete v tématu [načítání metadat](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8190c-109">For more information, see [Retrieving Metadata](../../../docs/framework/wcf/feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
2.  <span data-ttu-id="8190c-110">Otevřete konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="8190c-110">Open the XML configuration file.</span></span> <span data-ttu-id="8190c-111">Pokud používáte nástroje Svcutil.exe, výchozí název souboru je Output.config.</span><span class="sxs-lookup"><span data-stu-id="8190c-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>  
  
3.  <span data-ttu-id="8190c-112">Najít  **\<zabezpečení >** element s **režimu** atribut (**< režim zabezpečení =** `MessageOrTransport` **>** kde `MessageOrTransport` je nastavena na jeden z režimů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8190c-112">Find the **\<security>** element with the **mode** attribute (**<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>  
  
4.  <span data-ttu-id="8190c-113">Najděte podřízený element, který odpovídá hodnotě režimu.</span><span class="sxs-lookup"><span data-stu-id="8190c-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="8190c-114">Například, pokud režim je nastaven na **zpráva**, Najít  **\<zpráva >** obsažené v elementu  **\<zabezpečení >** element.</span><span class="sxs-lookup"><span data-stu-id="8190c-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>  
  
5.  <span data-ttu-id="8190c-115">Poznamenejte si hodnotu přiřazenou **clientCredentialType** atribut.</span><span class="sxs-lookup"><span data-stu-id="8190c-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="8190c-116">Skutečná hodnota závisí na režimu, který se používá, přenos nebo zprávy.</span><span class="sxs-lookup"><span data-stu-id="8190c-116">The actual value depends on which mode is used, transport or message.</span></span>  
  
 <span data-ttu-id="8190c-117">Následující kód ukazuje konfigurace pro klienta pomocí zabezpečení zpráv a které vyžadují certifikát pro ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="8190c-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="8190c-118">Příklad: Režim přenosu protokolu TCP s certifikátem jako pověření klienta</span><span class="sxs-lookup"><span data-stu-id="8190c-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>  
 <span data-ttu-id="8190c-119">Tento příklad nastaví režim zabezpečení pro režim přenosu a nastaví hodnotu přihlašovacích údajů klienta s certifikátem X.509.</span><span class="sxs-lookup"><span data-stu-id="8190c-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="8190c-120">Následující postupy ukazují, jak nastavit hodnotu přihlašovacích údajů klienta na straně klienta v kódu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8190c-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="8190c-121">Předpokladem je, že jste použili [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vrátit metadata (kódu a konfigurace) ze služby.</span><span class="sxs-lookup"><span data-stu-id="8190c-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="8190c-122">Další informace najdete v tématu [postupy: vytvoření klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="8190c-122">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="8190c-123">Zadejte hodnotu přihlašovacích údajů klienta na straně klienta v kódu</span><span class="sxs-lookup"><span data-stu-id="8190c-123">To specify the client credential value on the client in code</span></span>  
  
1.  <span data-ttu-id="8190c-124">Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pro generování kódu a konfigurace ze služby.</span><span class="sxs-lookup"><span data-stu-id="8190c-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>  
  
2.  <span data-ttu-id="8190c-125">Vytvoření instance [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta pomocí generovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="8190c-125">Create an instance of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client using the generated code.</span></span>  
  
3.  <span data-ttu-id="8190c-126">U třídy klienta nastavena <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třída na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8190c-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="8190c-127">Tento příklad nastaví vlastnost na certifikát X.509 pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.</span><span class="sxs-lookup"><span data-stu-id="8190c-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <span data-ttu-id="8190c-128">Můžete použít libovolnou výčtech <xref:System.Security.Cryptography.X509Certificates.X509FindType> třídy.</span><span class="sxs-lookup"><span data-stu-id="8190c-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="8190c-129">Název předmětu je zde použita v případě, že certifikát mění (z důvodu datum vypršení platnosti).</span><span class="sxs-lookup"><span data-stu-id="8190c-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="8190c-130">Použití v názvu subjektu umožňuje infrastruktury vyhledejte certifikát znovu.</span><span class="sxs-lookup"><span data-stu-id="8190c-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="8190c-131">Zadejte hodnotu přihlašovacích údajů klienta v klientském počítači v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="8190c-131">To specify the client credential value on the client in configuration</span></span>  
  
1.  <span data-ttu-id="8190c-132">Přidat [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu, který chcete [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="8190c-132">Add a [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
2.  <span data-ttu-id="8190c-133">Přidat [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, který chcete [ \<chování >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="8190c-133">Add a [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="8190c-134">Nastavte požadované `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8190c-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="8190c-135">Přidat [ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) elementu, který chcete [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span><span class="sxs-lookup"><span data-stu-id="8190c-135">Add a [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
4.  <span data-ttu-id="8190c-136">Nastavte následující atributy odpovídající hodnoty: `storeLocation`, `storeName`, `x509FindType`, a `findValue`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8190c-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="8190c-137">Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8190c-137">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  <span data-ttu-id="8190c-138">Při konfiguraci klienta, určete chování, a to nastavením `behaviorConfiguration` atribut `<endpoint>` elementu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8190c-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="8190c-139">Koncový bod elementu je podřízená [ \<klienta >](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span><span class="sxs-lookup"><span data-stu-id="8190c-139">The endpoint element is a child of the [\<client>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="8190c-140">Také, zadejte název konfigurace vazeb nastavením `bindingConfiguration` atribut vazby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="8190c-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="8190c-141">Pokud používáte generovaného konfiguračního souboru, název vazby je automaticky vytvořen.</span><span class="sxs-lookup"><span data-stu-id="8190c-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="8190c-142">V tomto příkladu je název `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="8190c-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8190c-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="8190c-143">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>  
 [<span data-ttu-id="8190c-144">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="8190c-144">Programming WCF Security</span></span>](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="8190c-145">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="8190c-145">Selecting a Credential Type</span></span>](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="8190c-146">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="8190c-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="8190c-147">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="8190c-147">Working with Certificates</span></span>](../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="8190c-148">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="8190c-148">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="8190c-149">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="8190c-149">\<netTcpBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)  
 [<span data-ttu-id="8190c-150">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="8190c-150">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
 [<span data-ttu-id="8190c-151">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="8190c-151">\<message></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)  
 [<span data-ttu-id="8190c-152">\<chování ></span><span class="sxs-lookup"><span data-stu-id="8190c-152">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)  
 [<span data-ttu-id="8190c-153">\<chování ></span><span class="sxs-lookup"><span data-stu-id="8190c-153">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [<span data-ttu-id="8190c-154">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="8190c-154">\<clientCertificate></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)  
 [<span data-ttu-id="8190c-155">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="8190c-155">\<clientCredentials></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
