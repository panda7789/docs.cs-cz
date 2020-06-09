---
title: 'Postupy: Zabezpečení služby certifikátem X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 10d6db63368ee55040f85f922b9483982e8ff264
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596965"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="0476d-102">Postupy: Zabezpečení služby certifikátem X.509</span><span class="sxs-lookup"><span data-stu-id="0476d-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="0476d-103">Zabezpečení služby pomocí certifikátu X. 509 je základní technika, kterou používá většina vazeb ve službě Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0476d-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="0476d-104">Toto téma vás provede jednotlivými kroky konfigurace samoobslužné služby s certifikátem X. 509.</span><span class="sxs-lookup"><span data-stu-id="0476d-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="0476d-105">Požadavek je platný certifikát, který lze použít k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="0476d-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="0476d-106">Certifikát musí být vydán pro server důvěryhodnou certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="0476d-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="0476d-107">Není-li certifikát platný, nebude služba při pokusu o používání služby pro službu důvěřovat, a proto nebude provedeno žádné připojení.</span><span class="sxs-lookup"><span data-stu-id="0476d-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="0476d-108">Další informace o používání certifikátů najdete v tématu [práce s certifikáty](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0476d-108">For more information about using certificates, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="0476d-109">Konfigurace služby s certifikátem pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="0476d-109">To configure a service with a certificate using code</span></span>  
  
1. <span data-ttu-id="0476d-110">Vytvořte kontrakt služby a implementovanou službu.</span><span class="sxs-lookup"><span data-stu-id="0476d-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="0476d-111">Další informace najdete v tématu [navrhování a implementace služeb](../designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="0476d-111">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md).</span></span>  
  
2. <span data-ttu-id="0476d-112">Vytvořte instanci <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message> , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0476d-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <span data-ttu-id="0476d-113">Vytvořte dvě <xref:System.Type> proměnné, jednu pro typ kontraktu a implementovaný kontrakt, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0476d-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <span data-ttu-id="0476d-114">Vytvořte instanci <xref:System.Uri> třídy pro základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="0476d-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="0476d-115">Vzhledem k tomu `WSHttpBinding` , že používá přenos pomocí protokolu HTTP, musí identifikátor URI (Uniform Resource Identifier) začínat tímto schématem nebo Windows Communication Foundation (WCF) vyvolá výjimku při otevření služby.</span><span class="sxs-lookup"><span data-stu-id="0476d-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <span data-ttu-id="0476d-116">Vytvořte novou instanci <xref:System.ServiceModel.ServiceHost> třídy s implementací proměnné typu kontraktu a identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="0476d-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <span data-ttu-id="0476d-117">Přidejte <xref:System.ServiceModel.Description.ServiceEndpoint> ke službě službu pomocí <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0476d-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="0476d-118">Předání kontraktu, vazby a adresy koncového bodu konstruktoru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0476d-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. <span data-ttu-id="0476d-119">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0476d-119">Optional.</span></span> <span data-ttu-id="0476d-120">Chcete-li načíst metadata ze služby, vytvořte nový <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objekt a nastavte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="0476d-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <span data-ttu-id="0476d-121">Pomocí <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy přidejte platný certifikát do služby.</span><span class="sxs-lookup"><span data-stu-id="0476d-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="0476d-122">Metoda může použít jednu z několika metod k vyhledání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="0476d-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="0476d-123">V tomto příkladu se používá <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> výčet.</span><span class="sxs-lookup"><span data-stu-id="0476d-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="0476d-124">Výčet Určuje, že poskytnutá hodnota je název entity, pro kterou byl certifikát vydán.</span><span class="sxs-lookup"><span data-stu-id="0476d-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="0476d-125">Voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metody zahajte naslouchání služby.</span><span class="sxs-lookup"><span data-stu-id="0476d-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="0476d-126">Pokud vytváříte konzolovou aplikaci, zavolejte <xref:System.Console.ReadLine%2A> metodu pro zachování služby ve stavu naslouchání.</span><span class="sxs-lookup"><span data-stu-id="0476d-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="0476d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="0476d-127">Example</span></span>  
 <span data-ttu-id="0476d-128">Následující příklad používá <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu ke konfiguraci služby s certifikátem X. 509.</span><span class="sxs-lookup"><span data-stu-id="0476d-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0476d-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0476d-129">Compiling the Code</span></span>  
 <span data-ttu-id="0476d-130">Pro zkompilování kódu jsou vyžadovány následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="0476d-130">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="0476d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0476d-131">See also</span></span>

- [<span data-ttu-id="0476d-132">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="0476d-132">Working with Certificates</span></span>](working-with-certificates.md)
