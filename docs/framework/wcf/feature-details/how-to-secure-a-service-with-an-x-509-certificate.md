---
title: 'Postupy: Zabezpečení služby certifikátem X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
author: BrucePerlerMS
ms.openlocfilehash: 1c5ab5e76ebed549df09b365a5a271f81003a517
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47402562"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Postupy: Zabezpečení služby certifikátem X.509
Zabezpečení služby certifikátem X.509 je základní technika, používat většinu vazby Windows Communication Foundation (WCF). Toto téma vás provede kroky konfigurace v místním prostředí služby pomocí certifikátu X.509.  
  
 Předpokladem je platný certifikát, který slouží k ověření tohoto serveru. Certifikát musí být na server vydán důvěryhodnou certifikační autoritou. Pokud certifikát není platný, jakýkoli klient pokouší použít služba nebude důvěřovat služby a v důsledku toho se nevytváří žádné připojení. Další informace o používání certifikátů najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Pro konfiguraci služby pomocí certifikátu pomocí kódu  
  
1.  Vytvoření kontraktu služby a služba implementovaná. Další informace najdete v tématu [návrh a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
2.  Vytvoření instance <xref:System.ServiceModel.WSHttpBinding> třídy a nastavte jeho režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3.  Pak vytvoříte další dva <xref:System.Type> proměnné, jedno pro typ kontraktu a implementovaného kontraktu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4.  Vytvoření instance <xref:System.Uri> třídy pro bázovou adresu služby. Vzhledem k tomu, `WSHttpBinding` používá přenos pomocí protokolu HTTP, identifikátor URI (Uniform Resource) musí začínat řetězcem tohoto schématu nebo Windows Communication Foundation (WCF) vyvolá výjimku při otevření služby.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5.  Vytvořit novou instanci třídy <xref:System.ServiceModel.ServiceHost> třída s atributem proměnná typu implementovaného kontraktu a identifikátor URI.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6.  Přidat <xref:System.ServiceModel.Description.ServiceEndpoint> pomocí služby <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Předejte kontrakt, vazbu a adresu koncového bodu konstruktoru, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7.  Volitelné. Chcete-li načíst metadata ze služby, vytvořte nový <xref:System.ServiceModel.Description.ServiceMetadataBehavior> objektu a nastavit <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> vlastnost `true`.  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8.  Použití <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> třídy přidat platného certifikátu ve službě. Metodu můžete použít některou z několika metod najít certifikát. V tomto příkladu <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> výčtu. Výčet Určuje, že zadaná hodnota je název sady entit, který byl vydán certifikát.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metoda zahájit naslouchání služby. Pokud vytvoříte konzolovou aplikaci, zavolejte <xref:System.Console.ReadLine%2A> metoda udržet službu ve stavu naslouchání.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodu pro konfiguraci služby pomocí certifikátu X.509.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pro zkompilování kódu se vyžaduje následující obory názvů:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
