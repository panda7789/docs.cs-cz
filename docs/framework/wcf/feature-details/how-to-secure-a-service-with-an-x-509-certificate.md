---
title: 'Postupy: Zabezpečení služby certifikátem X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
author: BrucePerlerMS
ms.openlocfilehash: 1c5ab5e76ebed549df09b365a5a271f81003a517
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073551"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="1f0f5-102">Postupy: Zabezpečení služby certifikátem X.509</span><span class="sxs-lookup"><span data-stu-id="1f0f5-102">How to: Secure a Service with an X.509 Certificate</span></span>
<span data-ttu-id="1f0f5-103">Zabezpečení služby certifikátem X.509 je základní technika, používat většinu vazby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1f0f5-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="1f0f5-104">Toto téma vás provede kroky konfigurace v místním prostředí služby pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="1f0f5-105">Předpokladem je platný certifikát, který slouží k ověření tohoto serveru.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="1f0f5-106">Certifikát musí být na server vydán důvěryhodnou certifikační autoritou.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="1f0f5-107">Pokud certifikát není platný, jakýkoli klient pokouší použít služba nebude důvěřovat služby a v důsledku toho se nevytváří žádné připojení.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="1f0f5-108">Další informace o používání certifikátů najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1f0f5-108">For more information about using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="1f0f5-109">Pro konfiguraci služby pomocí certifikátu pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="1f0f5-109">To configure a service with a certificate using code</span></span>  
  
1.  <span data-ttu-id="1f0f5-110">Vytvoření kontraktu služby a služba implementovaná.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="1f0f5-111">Další informace najdete v tématu [návrh a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="1f0f5-111">For more information, see [Designing and Implementing Services](../../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
2.  <span data-ttu-id="1f0f5-112">Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte jeho režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  <span data-ttu-id="1f0f5-113">Pak vytvoříte další dva <xref:System.Type> proměnné, jedno pro typ kontraktu a implementovaného kontraktu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  <span data-ttu-id="1f0f5-114">Vytvoření instance <xref:System.Uri> třídy pro bázovou adresu služby.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="1f0f5-115">Vzhledem k tomu, `WSHttpBinding` používá přenos pomocí protokolu HTTP, identifikátor URI (Uniform Resource) musí začínat řetězcem tohoto schématu nebo Windows Communication Foundation (WCF) vyvolá výjimku při otevření služby.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  <span data-ttu-id="1f0f5-116">Vytvořit novou instanci třídy <xref:System.ServiceModel.ServiceHost> třída s atributem proměnná typu implementovaného kontraktu a identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  <span data-ttu-id="1f0f5-117">Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> pomocí služby <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="1f0f5-118">Předejte kontrakt, vazbu a adresu koncového bodu konstruktoru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  <span data-ttu-id="1f0f5-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-119">Optional.</span></span> <span data-ttu-id="1f0f5-120">Chcete-li načíst metadata ze služby, vytvořte nový <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objektu a nastavit <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  <span data-ttu-id="1f0f5-121">Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy přidat platného certifikátu ve službě.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="1f0f5-122">Metodu můžete použít některou z několika metod najít certifikát.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="1f0f5-123">V tomto příkladu <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> výčtu.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="1f0f5-124">Výčet Určuje, že zadaná hodnota je název sady entit, který byl vydán certifikát.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="1f0f5-125">Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda zahájit naslouchání služby.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="1f0f5-126">Pokud vytvoříte konzolovou aplikaci, zavolejte <xref:System.Console.ReadLine%2A> metoda udržet službu ve stavu naslouchání.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="1f0f5-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f0f5-127">Example</span></span>  
 <span data-ttu-id="1f0f5-128">V následujícím příkladu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu pro konfiguraci služby pomocí certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="1f0f5-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f0f5-129">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1f0f5-129">Compiling the Code</span></span>  
 <span data-ttu-id="1f0f5-130">Pro zkompilování kódu se vyžaduje následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="1f0f5-130">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="1f0f5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f0f5-131">See Also</span></span>  
 [<span data-ttu-id="1f0f5-132">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="1f0f5-132">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
