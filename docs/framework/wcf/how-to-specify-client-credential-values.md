---
title: 'Postupy: Zadání hodnot přihlašovacích údajů klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319853"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="7d581-102">Postupy: Zadání hodnot přihlašovacích údajů klienta</span><span class="sxs-lookup"><span data-stu-id="7d581-102">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="7d581-103">Pomocí Windows Communication Foundation (WCF) může služba určit, jak bude klient ověřený ke službě.</span><span class="sxs-lookup"><span data-stu-id="7d581-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="7d581-104">Například služba může určit, že se má klient ověřit pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7d581-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="7d581-105">Určení typu pověření klienta</span><span class="sxs-lookup"><span data-stu-id="7d581-105">To determine the client credential type</span></span>

1. <span data-ttu-id="7d581-106">Načtěte metadata z koncového bodu metadat služby.</span><span class="sxs-lookup"><span data-stu-id="7d581-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="7d581-107">Metadata se typicky skládají ze dvou souborů: kód klienta v programovacím jazyce podle vašeho výběru (výchozí je vizuál C#) a konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="7d581-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="7d581-108">Jedním ze způsobů, jak načíst metadata, je použít nástroj Svcutil. exe k vrácení kódu klienta a konfigurace klienta.</span><span class="sxs-lookup"><span data-stu-id="7d581-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="7d581-109">Další informace najdete v tématu [načtení metadat](./feature-details/retrieving-metadata.md) a [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7d581-109">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="7d581-110">Otevřete konfigurační soubor XML.</span><span class="sxs-lookup"><span data-stu-id="7d581-110">Open the XML configuration file.</span></span> <span data-ttu-id="7d581-111">Použijete-li nástroj Svcutil. exe, výchozí název souboru je Output. config.</span><span class="sxs-lookup"><span data-stu-id="7d581-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="7d581-112">Vyhledejte **> prvek \<security** s atributem **Mode** ( **\<security mode =** `MessageOrTransport` **>** , kde `MessageOrTransport` je nastaveno na jeden z režimů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7d581-112">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="7d581-113">Najděte podřízený element, který odpovídá hodnotě Mode.</span><span class="sxs-lookup"><span data-stu-id="7d581-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="7d581-114">Například pokud je režim nastaven na **zprávy**, vyhledejte **> prvek \<message** obsažený v elementu **> \<security** .</span><span class="sxs-lookup"><span data-stu-id="7d581-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="7d581-115">Poznamenejte si hodnotu přiřazenou atributu **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="7d581-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="7d581-116">Skutečná hodnota závisí na použitém režimu, přenosu nebo zprávě.</span><span class="sxs-lookup"><span data-stu-id="7d581-116">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="7d581-117">Následující kód XML ukazuje konfiguraci klienta pomocí zabezpečení zpráv a vyžádání certifikátu pro ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="7d581-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="7d581-118">Příklad: režim přenosu TCP s certifikátem jako přihlašovací údaje klienta</span><span class="sxs-lookup"><span data-stu-id="7d581-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="7d581-119">Tento příklad nastaví režim zabezpečení na transportní režim a nastaví hodnotu přihlašovacích údajů klienta na certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="7d581-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="7d581-120">Následující postupy ukazují, jak nastavit hodnotu přihlašovacích údajů klienta v klientovi v kódu a konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7d581-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="7d581-121">To předpokládá, že jste použili nástroj pro dodávání [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , který vrací metadata (kód a konfiguraci) ze služby.</span><span class="sxs-lookup"><span data-stu-id="7d581-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="7d581-122">Další informace najdete v tématu [Postup: Vytvoření klienta](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="7d581-122">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="7d581-123">Určení hodnoty přihlašovacích údajů klienta na klientovi v kódu</span><span class="sxs-lookup"><span data-stu-id="7d581-123">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="7d581-124">K vygenerování kódu a konfigurace ze služby použijte nástroj pro dodané [metadata (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="7d581-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="7d581-125">Vytvořte instanci klienta WCF pomocí vygenerovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="7d581-125">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="7d581-126">Na klientské třídě nastavte vlastnost <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> třídy <xref:System.ServiceModel.ClientBase%601> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d581-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="7d581-127">Tento příklad nastaví vlastnost na certifikát X. 509 pomocí metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> třídy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.</span><span class="sxs-lookup"><span data-stu-id="7d581-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="7d581-128">Můžete použít kterýkoli z výčtů třídy <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span><span class="sxs-lookup"><span data-stu-id="7d581-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="7d581-129">Název subjektu se tady používá pro případ změny certifikátu (kvůli datu vypršení platnosti).</span><span class="sxs-lookup"><span data-stu-id="7d581-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="7d581-130">Použití názvu subjektu umožní infrastruktuře znovu najít certifikát.</span><span class="sxs-lookup"><span data-stu-id="7d581-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="7d581-131">Určení hodnoty přihlašovacích údajů klienta v konfiguraci klienta</span><span class="sxs-lookup"><span data-stu-id="7d581-131">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="7d581-132">Přidejte prvek [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do prvku [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="7d581-132">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="7d581-133">Přidejte prvek [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) do prvku [> \<behaviors](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="7d581-133">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="7d581-134">Nezapomeňte nastavit požadovaný atribut `name` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d581-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="7d581-135">Přidejte prvek [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) do prvku [> \<clientCredentials](../configure-apps/file-schema/wcf/clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="7d581-135">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="7d581-136">Nastavte následující atributy na příslušné hodnoty: `storeLocation`, `storeName`, `x509FindType` a `findValue`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7d581-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="7d581-137">Další informace o certifikátech najdete v tématu [práce s certifikáty](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7d581-137">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

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

5. <span data-ttu-id="7d581-138">Při konfiguraci klienta Určete chování nastavením atributu `behaviorConfiguration` prvku `<endpoint>`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7d581-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="7d581-139">Element Endpoint je podřízeným prvkem prvku [\<client >](../configure-apps/file-schema/wcf/client.md) .</span><span class="sxs-lookup"><span data-stu-id="7d581-139">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="7d581-140">Také zadejte název konfigurace vazby nastavením atributu `bindingConfiguration` na vazbu pro klienta.</span><span class="sxs-lookup"><span data-stu-id="7d581-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="7d581-141">Pokud používáte generovaný konfigurační soubor, automaticky se vygeneruje název vazby.</span><span class="sxs-lookup"><span data-stu-id="7d581-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="7d581-142">V tomto příkladu je název `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="7d581-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="7d581-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d581-143">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="7d581-144">Programování zabezpečení WCF</span><span class="sxs-lookup"><span data-stu-id="7d581-144">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="7d581-145">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="7d581-145">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="7d581-146">Nástroj metadat modelu služby (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="7d581-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="7d581-147">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="7d581-147">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="7d581-148">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="7d581-148">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="7d581-149">@no__t – 1netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="7d581-149">\<netTcpBinding></span></span>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="7d581-150">@no__t – 1security ></span><span class="sxs-lookup"><span data-stu-id="7d581-150">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="7d581-151">@no__t – 1message ></span><span class="sxs-lookup"><span data-stu-id="7d581-151">\<message></span></span>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="7d581-152">@no__t – 1behavior ></span><span class="sxs-lookup"><span data-stu-id="7d581-152">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="7d581-153">@no__t – 1behaviors ></span><span class="sxs-lookup"><span data-stu-id="7d581-153">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="7d581-154">@no__t – 1clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="7d581-154">\<clientCertificate></span></span>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="7d581-155">@no__t – 1clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7d581-155">\<clientCredentials></span></span>](../configure-apps/file-schema/wcf/clientcredentials.md)
