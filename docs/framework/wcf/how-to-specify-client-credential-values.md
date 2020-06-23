---
title: 'Postupy: Zadání hodnot přihlašovacích údajů klienta'
description: Přečtěte si, jak může služba WCF určit, jak se má klient ověřit pro tuto službu. Tento příklad určuje certifikát X. 509 a režim přenosu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244449"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="71933-104">Postupy: Zadání hodnot přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="71933-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="71933-105">Pomocí Windows Communication Foundation (WCF) může služba určit, jak bude klient ověřený ke službě.</span><span class="sxs-lookup"><span data-stu-id="71933-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="71933-106">Například služba může určit, že se má klient ověřit pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="71933-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="71933-107">Určení typu pověření klienta</span><span class="sxs-lookup"><span data-stu-id="71933-107">To determine the client credential type</span></span>

1. <span data-ttu-id="71933-108">Načtěte metadata z koncového bodu metadat služby.</span><span class="sxs-lookup"><span data-stu-id="71933-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="71933-109">Metadata se typicky skládají ze dvou souborů: kód klienta v programovacím jazyce podle vašeho výběru (výchozí nastavení je Visual C#) a konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="71933-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="71933-110">Jedním ze způsobů, jak načíst metadata, je použít nástroj Svcutil.exe k vrácení kódu klienta a konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="71933-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="71933-111">Další informace najdete v tématu [načtení metadat](./feature-details/retrieving-metadata.md) a [Nástroj pro nástroj pro metadata ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="71933-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="71933-112">Otevřete konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="71933-112">Open the XML configuration file.</span></span> <span data-ttu-id="71933-113">Použijete-li nástroj Svcutil.exe, je výchozí název souboru Output.config.</span><span class="sxs-lookup"><span data-stu-id="71933-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="71933-114">Vyhledejte **\<security>** element s atributem **Mode** ( **\<security mode =**`MessageOrTransport`**>** kde `MessageOrTransport` je nastaven na jeden z režimů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="71933-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="71933-115">Najděte podřízený element, který odpovídá hodnotě Mode.</span><span class="sxs-lookup"><span data-stu-id="71933-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="71933-116">Například pokud je režim nastaven na **zprávy**, najděte **\<message>** element obsažený v **\<security>** elementu.</span><span class="sxs-lookup"><span data-stu-id="71933-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="71933-117">Poznamenejte si hodnotu přiřazenou atributu **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="71933-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="71933-118">Skutečná hodnota závisí na použitém režimu, přenosu nebo zprávě.</span><span class="sxs-lookup"><span data-stu-id="71933-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="71933-119">Následující kód XML ukazuje konfiguraci klienta pomocí zabezpečení zpráv a vyžádání certifikátu pro ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="71933-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="71933-120">Příklad: režim přenosu TCP s certifikátem jako přihlašovací údaje klienta</span><span class="sxs-lookup"><span data-stu-id="71933-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="71933-121">Tento příklad nastaví režim zabezpečení na transportní režim a nastaví hodnotu přihlašovacích údajů klienta na certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="71933-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="71933-122">Následující postupy ukazují, jak nastavit hodnotu přihlašovacích údajů klienta v klientovi v kódu a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="71933-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="71933-123">To předpokládá, že jste použili nástroj pro dodávání [metadat (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) k vrácení metadat (kódu a konfigurace) ze služby.</span><span class="sxs-lookup"><span data-stu-id="71933-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="71933-124">Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="71933-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="71933-125">Určení hodnoty přihlašovacích údajů klienta na klientovi v kódu</span><span class="sxs-lookup"><span data-stu-id="71933-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="71933-126">K vygenerování kódu a konfigurace ze služby použijte nástroj pro dodané [metadata (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="71933-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="71933-127">Vytvořte instanci klienta WCF pomocí vygenerovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="71933-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="71933-128">Na klientské třídě nastavte <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> vlastnost <xref:System.ServiceModel.ClientBase%601> třídy na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71933-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="71933-129">Tento příklad nastaví vlastnost na certifikát X. 509 pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> třídy.</span><span class="sxs-lookup"><span data-stu-id="71933-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="71933-130">Můžete použít kterýkoli z výčtů <xref:System.Security.Cryptography.X509Certificates.X509FindType> třídy.</span><span class="sxs-lookup"><span data-stu-id="71933-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="71933-131">Název subjektu se tady používá pro případ změny certifikátu (kvůli datu vypršení platnosti).</span><span class="sxs-lookup"><span data-stu-id="71933-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="71933-132">Použití názvu subjektu umožní infrastruktuře znovu najít certifikát.</span><span class="sxs-lookup"><span data-stu-id="71933-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="71933-133">Určení hodnoty přihlašovacích údajů klienta v konfiguraci klienta</span><span class="sxs-lookup"><span data-stu-id="71933-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="71933-134">Přidejte [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="71933-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="71933-135">Přidejte [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element do [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="71933-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="71933-136">Nezapomeňte nastavit požadovaný `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71933-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="71933-137">Přidejte [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element do [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="71933-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="71933-138">Nastavte následující atributy na příslušné hodnoty: `storeLocation` , `storeName` , a `x509FindType` `findValue` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="71933-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="71933-139">Další informace o certifikátech najdete v tématu [práce s certifikáty](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="71933-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

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

5. <span data-ttu-id="71933-140">Při konfiguraci klienta Určete chování nastavením `behaviorConfiguration` atributu `<endpoint>` prvku, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="71933-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="71933-141">Element Endpoint je podřízeným prvkem [\<client>](../configure-apps/file-schema/wcf/client.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="71933-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="71933-142">Také zadejte název konfigurace vazby nastavením `bindingConfiguration` atributu na vazbu pro klienta.</span><span class="sxs-lookup"><span data-stu-id="71933-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="71933-143">Pokud používáte generovaný konfigurační soubor, automaticky se vygeneruje název vazby.</span><span class="sxs-lookup"><span data-stu-id="71933-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="71933-144">V tomto příkladu je název `"tcpBindingWithCredential"` .</span><span class="sxs-lookup"><span data-stu-id="71933-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="71933-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="71933-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="71933-146">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="71933-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="71933-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="71933-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="71933-148">Nástroj ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="71933-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="71933-149">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="71933-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="71933-150">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="71933-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
